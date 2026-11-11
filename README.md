# 🚀 RunPod + vLLM: Private DevOps AI Coding Agent Recipes

Skrócona dokumentacja oraz komendy startowe serwera **vLLM** dla kart **NVIDIA L40S** (48 GB VRAM) oraz **NVIDIA RTX 5090** (32 GB VRAM) dla agentów programistycznych (*Cline*, *Qwen Code*).

---

## 🛠️ Gotowe komendy startowe vLLM (RunPod Docker Arguments)

### 1. NVIDIA L40S (48 GB VRAM)
* **Opcja A (`Qwen/Qwen3.6-35B-A3B-FP8`)** general

```
Qwen/Qwen3.6-35B-A3B-FP8 --max-model-len 262144 --gpu-memory-utilization 0.95 --max-num-seqs 4 --language-model-only --reasoning-parser qwen3 --enable-auto-tool-choice --tool-call-parser qwen3_xml --host 0.0.0.0 --port 8000 --default-chat-template-kwargs '{"preserve_thinking":true}' --override-generation-config '{"temperature":1.0,"top_p":0.95,"top_k":20,"min_p":0.0,"presence_penalty":1.5,"repetition_penalty":1.0}'
```

* **Opcja B (`Qwen/Qwen3.8-27B-FP8`)**

```
Qwen/Qwen3.6-35B-A3B-FP8 --max-model-len 131072 --gpu-memory-utilization 0.95 --max-num-seqs 2 --language-model-only --enable-prefix-caching --reasoning-parser qwen3 --enable-auto-tool-choice --tool-call-parser qwen3_xml --host 0.0.0.0 --port 8000 --default-chat-template-kwargs '{"preserve_thinking":true}' --override-generation-config '{"temperature":0.6, "top_p":0.95, "top_k":20, "min_p":0.0, "presence_penalty":0.0, "repetition_penalty":1.0}'
```

### 2. NVIDIA RTX 5090 (32 GB VRAM) — Konfiguracje NVFP4
* **Opcja A (`nvidia/Qwen3.8-27B-NVFP4`)** 

```
nvidia/Qwen3.8-27B-NVFP4 --quantization modelopt --max-model-len 131072 --kv-cache-dtype fp8_e4m3 --gpu-memory-utilization 0.95 --max-num-seqs 4 --language-model-only --reasoning-parser qwen3 --enable-auto-tool-choice --tool-call-parser qwen3_xml --host 0.0.0.0 --port 8000 --default-chat-template-kwargs '{"reasoning_effort":"medium"}' --override-generation-config '{"temperature":1.0,"top_p":0.95,"top_k":20,"min_p":0.0,"presence_penalty":0.0,"repetition_penalty":1.0}'
```

* **Opcja B (`nvidia/Qwen3.6-35B-A3B-NVFP4`)**

```
nvidia/Qwen3.6-35B-A3B-NVFP4 --quantization modelopt --max-model-len 131072 --kv-cache-dtype fp8 --gpu-memory-utilization 0.95 --max-num-seqs 4 --language-model-only --reasoning-parser qwen3 --enable-auto-tool-choice --tool-call-parser qwen3_xml --host 0.0.0.0 --port 8000 --default-chat-template-kwargs '{"preserve_thinking":true}' --override-generation-config '{"temperature":0.6,"top_p":0.95,"top_k":20,"min_p":0.0,"presence_penalty":0.0,"repetition_penalty":1.0}'
```


---

## 📊 Wyniki testów i konfiguracje

Dokładne parametry uruchamiania modeli takich jak `Qwen/Qwen3.6-35B-A3B-FP8` oraz `Qwen/Qwen3.8-27B-FP8` (wraz z opcjami dla kart L40S i RTX 5090 z NVFP4) oraz szczegółową analizę i konfiguracje opisuję w artykułach na LinkedIn:

1. [Qwen3.6-35B-A3B (MoE) vs Qwen3.8-27B (Dense) na karcie L40S – optymalizacja vLLM pod pracę z agentem AI](https://www.linkedin.com/pulse/qwen36-35b-a3b-moe-vs-qwen38-27b-dense-na-karcie-l40s-wiktorowski-dpfpf)
2. [Qwen3.8-27B i Qwen3.6-35B-A3B w formacie NVFP4 na karcie RTX 5090 – jak zmieścić duże modele w 32 GB VRAM i przyspieszyć pracę z agentem AI](https://www.linkedin.com/pulse/qwen38-27b-i-qwen36-35b-a3b-w-formacie-nvfp4-na-rtx-5090-wiktorowski-l2brf)
3. [Strojenie agentów AI w DevOps: vLLM, qwen3_xml vs qwen3_coder i terminalowy Qwen Code](https://www.linkedin.com/pulse/strojenie-agentów-ai-w-devops-vllm-qwen3xml-vs-i-qwen-wiktorowski-ahhjf)

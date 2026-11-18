# M461C: a small local AI that knows when it doesn't know

> [!CAUTION]
> **These model files only work properly inside the OpenDaemon app.**
>
> The model files in [Releases](https://github.com/open-daemon/M461C/releases) do **not** contain M461C's senses (search when unsure, refuse harm). Those come from a special engine that ships inside OpenDaemon.
>
> **Do not run these files in Ollama, LM Studio or plain llama.cpp.** You would get a plain Qwen3.5-4B, without any of the improvements on this page.
>
> You don't need to download anything here: OpenDaemon downloads these exact files for you. See **[How to get M461C working](#how-to-get-m461c-working)**.

M461C runs entirely on an ordinary Windows PC, on a graphics card with 4 GB of memory. No cloud, no account, no subscription.

Most small AI models answer everything with the same confidence, even when they are making it up. M461C notices from inside its own computation when it is about to guess. Then it searches the web, reads the sources, and only then answers. It also notices when a request is harmful, and refuses it politely, before it writes a word.

**Measured against the original Qwen3.5-4B, on the same home PC:**

| | Original model | M461C |
|---|---|---|
| Made-up answers on 147 invented topics | 34 | **0** |
| Searched before answering on those topics | 104 | **147** |
| Real questions answered right (of 147) | 142 | **142** |
| Harmful requests refused (of 13) | 11 | **13** |
| Harmless requests wrongly refused (of 15) | 0 | **0** |
| Final exam, never seen while building: harmful asks refused (of 60) | 41 | **60** |
| Final exam, never seen while building: harmless asks wrongly refused (of 60) | 0 | **6** |
| Speed on a 2016 4 GB graphics card | ~19 tokens/s | ~19 tokens/s |

The final exam was written in advance and run once, at the end, so it is the honest measure. The full report, **[Senses on the Golden Gate is All You Need.](paper/M461C-paper.md)**, has the results and honest limits.

![Safer: all 13 harmful requests refused](paper/charts/4-safety.png)

![Final exam: all 60 harmful asks refused](paper/charts/5-final-exam.png)

## See it

https://github.com/user-attachments/assets/e984a3a6-e0c7-492c-bcfa-b5b1d4fe4c8f

M461C demo (2 minutes 37): its name, a search on a question it can't know, a letter-counting question, and what you can test with it. Running on a 2016 GTX 1050 Ti 4 GB GPU. Music: Elektronomia - Sky High [NCS Release].

## How to get M461C working

M461C is free inside **[OpenDaemon](https://apps.microsoft.com/detail/9NRBTQJJXF4G)**, our AI app for Windows.

1. **Install OpenDaemon** from the [Microsoft Store](https://apps.microsoft.com/detail/9NRBTQJJXF4G). It's free.
2. **Optional: add cloud AI for the rest of the app.** The first time you open the chat, the setup guide starts. Free NVIDIA API keys work well:
   - Sign up at [build.nvidia.com/models](https://build.nvidia.com/models).
   - Click **API Key** in the top-right corner. NVIDIA asks for your phone number; enter the code it sends you by SMS.
   - Create a key and give it any name (`1`, `2`, `3`...). **We recommend about 10 free keys**, so if one stops working the others keep going.
   - You can also add your own paid API keys. To change your setup later, type `/onboarding` in the chat at any time.
3. **Open the Local AI tab and click Download.** The app downloads these same model files from this page by itself. The engine that gives M461C its senses is already inside OpenDaemon.
4. **Start it.** M461C runs on your own PC, on any graphics card with 4 GB of memory or more. No cloud, no account, no subscription.

**About OpenDaemon:** an agentic app that is growing into an agentic hub, with new tools added every month, for free. You can support us by downloading it, using it and sharing it with your friends. Questions or ideas: **support@open-daemon.com**

## Honest limits

- It is a small model: it knows less than large ones, and it still makes mistakes.
- It sometimes refuses too much: on the final exam it opened 6 of 60 harmless answers with "I cannot…".
- The tests behind the numbers above are small (dozens to a few hundred questions).

## Credits

Built on **Qwen3.5-4B** by the Qwen team (Apache-2.0).

The detailed technical report is available to research labs: **support@open-daemon.com**

Made by David, developer of [OpenDaemon](https://apps.microsoft.com/detail/9NRBTQJJXF4G).

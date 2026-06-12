---
title: "problems compiling dumb"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jaytwokay on 2008-02-17
Hey all. I'm still pretty new to this whole linux thing (been using it almost a year now), but  I've been having a few problems trying to install DUMB (Dynamic Universal Music Bibliotheque) 0.9.3. When I try to "make" I get this error message. Any help would be appreciated.

```
 In file included from src/allegro/alplay.c:24:
include/aldumb.h:38: error: expected ‘)’ before ‘*’ token
include/aldumb.h:39: error: expected ‘)’ before ‘*’ token
src/allegro/alplay.c:35: error: expected specifier-qualifier-list before ‘AUDIOSTREAM’
src/allegro/alplay.c: In function ‘al_start_duh’:
src/allegro/alplay.c:62: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:62: warning: implicit declaration of function ‘play_audio_stream’
src/allegro/alplay.c:64: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:69: warning: implicit declaration of function ‘voice_set_priority’
src/allegro/alplay.c:69: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:71: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:73: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:74: warning: implicit declaration of function ‘stop_audio_stream’
src/allegro/alplay.c:74: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:79: error: ‘AL_DUH_PLAYER’ has no member named ‘volume’
src/allegro/alplay.c:80: error: ‘AL_DUH_PLAYER’ has no member named ‘silentcount’
src/allegro/alplay.c: In function ‘al_stop_duh’:
src/allegro/alplay.c:90: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:91: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:92: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c: In function ‘al_pause_duh’:
src/allegro/alplay.c:102: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:103: warning: implicit declaration of function ‘voice_stop’
src/allegro/alplay.c:103: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c: In function ‘al_resume_duh’:
src/allegro/alplay.c:112: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:113: warning: implicit declaration of function ‘voice_start’
src/allegro/alplay.c:113: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c: In function ‘al_duh_set_priority’:
src/allegro/alplay.c:122: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:123: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c: In function ‘al_duh_set_volume’:
src/allegro/alplay.c:131: error: ‘AL_DUH_PLAYER’ has no member named ‘volume’
src/allegro/alplay.c: In function ‘al_duh_get_volume’:
src/allegro/alplay.c:138: error: ‘AL_DUH_PLAYER’ has no member named ‘volume’
src/allegro/alplay.c: In function ‘al_poll_duh’:
src/allegro/alplay.c:150: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:156: warning: implicit declaration of function ‘get_audio_stream_buffer’
src/allegro/alplay.c:156: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:156: warning: assignment makes pointer from integer without a cast
src/allegro/alplay.c:161: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:161: error: ‘AL_DUH_PLAYER’ has no member named ‘volume’
src/allegro/alplay.c:164: error: ‘AL_DUH_PLAYER’ has no member named ‘silentcount’
src/allegro/alplay.c:165: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:166: warning: implicit declaration of function ‘free_audio_stream_buffer’
src/allegro/alplay.c:166: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:167: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:168: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:173: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:179: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c: In function ‘al_duh_get_position’:
src/allegro/alplay.c:188: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c: In function ‘al_duh_encapsulate_sigrenderer’:
src/allegro/alplay.c:215: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:217: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:222: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
src/allegro/alplay.c:224: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:226: error: ‘AL_DUH_PLAYER’ has no member named ‘volume’
src/allegro/alplay.c:227: error: ‘AL_DUH_PLAYER’ has no member named ‘silentcount’
src/allegro/alplay.c: In function ‘al_duh_get_sigrenderer’:
src/allegro/alplay.c:236: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c: In function ‘al_duh_decompose_to_sigrenderer’:
src/allegro/alplay.c:247: error: ‘AL_DUH_PLAYER’ has no member named ‘sigrenderer’
src/allegro/alplay.c:248: error: ‘AL_DUH_PLAYER’ has no member named ‘stream’
make[1]: *** [obj/unix/release/alplay.o] Error 1
make: *** [all] Error 2

```

---

### Post by 1337455 10534 on 2008-02-17
Is there a binary you can get? It looks like there is a problem in the source code (:?).

---


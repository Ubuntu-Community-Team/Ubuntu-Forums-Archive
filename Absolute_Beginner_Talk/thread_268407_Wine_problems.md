---
title: "Wine problems"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by dez_cole on 2006-09-30
Ive been working on setting up Ubuntu for a few weeks and now I'm trying to use wine. Every time i try to start a demo of prey, this pops up on the game terminal 
> Prey 0.2.95 win-x86 May 30 2006 21:14:05
2205 MHz AMD CPU with MMX & 3DNow! & SSE
496 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0  - 192.168.1.101/1.0.0.0
Found interface: sit0  - /
Sys_InitNetworking: adding loopback interface
prey using MMX & SSE for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Current search path:
Z:\home\dez/base
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted demo mode.

Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Couldn't load default.cfg
I already installed it, and blender works so i dont think its the video drivers. Thanks A Lot!

---

### Post by cacharreo on 2006-09-30
You should configure wine before use it
Run ***winecfg*** first

---

### Post by dez_cole on 2006-09-30
actually i did configure wine.

---

### Post by dez_cole on 2006-09-30
Sorry to bump my thread but does anyone know how to fix this. Also whenever i go into winecfg this comes onto the terminal
> fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)

if i click in the audio tab in winecfg this pops up as well> fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
Please help, Thanks a lot!

---


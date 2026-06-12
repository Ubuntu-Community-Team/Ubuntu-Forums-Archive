---
title: "no sound in CSS ahhh :'("
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-12-10
Ok, sound works in wine with me, IE for Oblivion and xfire. I'm using the OSS driver with emulation in the winecfg. Can anybody give me some clues as to why sound isn't working in CSS?  I've tried all the drivers btw ?????

Thanks in advance for help :)

---

### Post by Comzee on 2007-12-10
:popcorn:

---

### Post by daInvincibleGama on 2008-01-19
I have the same problem.

There's something that Steam apparently does to take control of the sound and not share it with anything, including native linux apps and its own games. Using ALSA makes the problem go away, but it causes crashes within minutes in CSS. So does enabling "Driver Emulation" in ths OSS settings.

Yeah, that's pretty stupid, but we gotta play without sound until someone figures out a workaround or a patch, since I don't have much of a clue about Wine/WindowsAPI and API translation.

It will probably be a quick fix if someone who knows what they are doing looks into it.

Either way, this doesn't belong in the nubchat board. It is a pretty involved issue.

So please help.

My machine:

Ubuntu 7.10 x64
Intel C2D 2.4 Ghz
nVidia 650i chipset
Analog Devices Sound with nVidia mixer i think
nVidia 8800GTS 640MB (G80)

---


---
title: "kworld usb dvd maker"
date: 2011-04-23
forum: Any Other OS
---

### Post by draucia on 2011-04-23
I'm trying to get this thing to work under linux. I am running linux mint 10 (basically ubuntu 10.10, so it shouldn't matter). I'm trying to make a perm. switch over to linux, but it's hard without this capture card. I have scanning, and everything working BUT this. It would be great if you could help me capture video from a TV with this capture card.

I've followed this thread. [http://ubuntuforums.org/showthread.php?t=856712]("http://ubuntuforums.org/showthread.php?t=856712"), but the repo is down and I can't manage to make install the linuxtv one... can someone please tell me steps to get this working?

Doing "lsusb" does display this device. I've tried following a few other guides, but it just doesn't work. Has anybody gotten this to work?

Oh and:

[http://www.linuxtv.org/wiki/index.php/Em28xx_devices]("http://www.linuxtv.org/wiki/index.php/Em28xx_devices")

EM2800_BOARD_KWORLD_USB2800 Kworld USB2800 IS supported.

I've tried doing what it said on that page, but:

> /home/draucia/v4l-dvb/v4l/firedtv-fw.c: In function 'model_name':
/home/draucia/v4l-dvb/v4l/firedtv-fw.c:254: warning: assignment discards qualifiers from pointer target type
/home/draucia/v4l-dvb/v4l/firedtv-fw.c: In function 'node_probe':
/home/draucia/v4l-dvb/v4l/firedtv-fw.c:280: warning: passing argument 1 of 'model_name' discards qualifiers from pointer target type
/home/draucia/v4l-dvb/v4l/firedtv-fw.c:244: note: expected 'u32 *' but argument is of type 'const u32 *'
  CC [M]  /home/draucia/v4l-dvb/v4l/firedtv-1394.o
/home/draucia/v4l-dvb/v4l/firedtv-1394.c:22: fatal error: dma.h: No such file or directory
compilation terminated.
make[3]: *** [/home/draucia/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/draucia/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/draucia/v4l-dvb/v4l'
make: *** [all] Error 2


---

### Post by Perfect Storm on 2011-04-24
Moved to Other OS/Distro Talk.

---

### Post by draucia on 2011-04-24
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

This isn't Other OS/Distro Talk. This is multimedia talk about a capture card on linux. Please move it back to the multimedia section. If you actually read the thread...

---

### Post by mips on 2011-04-24
> **draucia said:**
> This isn't Other OS/**Distro** Talk. This is multimedia talk about a capture card on linux. Please move it back to the multimedia section. If you actually read the thread...

NO. This is about Linux Mint which like all other distros (and Ubuntu derivatives) falls in the domain of Other OS/**Distro** Talk. If you use Ubuntu it would fall in the multimedia section.

---

### Post by Perfect Storm on 2011-04-24
What mips says is correct. 
But it would be better if you check out Mint Forums which are geared towards Mint Linux and its setups/applications etc. [http://forums.linuxmint.com/](http://forums.linuxmint.com/) - they have a multimedia section for Mint.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by draucia on 2011-04-24
> **Artificial Intelligence said:**
> What mips says is correct. 
But it would be better if you check out Mint Forums which are geared towards Mint Linux and its setups/applications etc. [http://forums.linuxmint.com/](http://forums.linuxmint.com/) - they have a multimedia section for Mint.


regards
A.I. Dude
Ubuntu Forum Staff

Okay than I guess. Too bad the Linux Mint forums are not as active. Linux Mint is a derivative of ubuntu. Same help files, etc. I guess it's fine though.

---

### Post by draucia on 2011-04-26
Bump! Any help?

---


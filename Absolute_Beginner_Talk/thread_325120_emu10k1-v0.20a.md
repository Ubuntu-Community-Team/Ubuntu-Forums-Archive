---
title: "emu10k1-v0.20a"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Stunnerlikenone on 2006-12-25
Hi, As you have already guessed (most likely) I am new to the Linux operating system.  Right now I'm having trouble using my sound card with my new installed Ubuntu OS.  I just wanted to find a simple way to install it that I can understand.  The farthest I have gone through the installation is changing it from a tar file to regular file.  Anything else I have or had to do has failed.  I know I have to reconfigure the Kernel but I also don't know how to do that.  any help that can be given is much appreciated.

the File is emu10k1-v0.20a
currently residing in this directory /home/stun/dls
beyond that I don't know what else to say so i guess I will just wait for a reply

---

### Post by karamba_kid on 2006-12-25
Do you have a sound card with the emu10k1 chipset.  I have one and everything works perfectly but I bought one because my on-board sound didn't/doesn't work very well with *nix and this chipset seems to work very well (out of the box).  You should post the output of lspci | grep audio. here is mine:

$ lspci | grep audio
0000:02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

You are trying edgy, correct?

---


---
title: "[SOLVED] error installing .tar files"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2008-03-03
I'm just trying to update the ALSA files as a result of a sound problem and I get the following message when I go to the alsa-tools-1.0.16 directory.
As you can see, the directory does exist, so is this a problem that I should be aware of?

tony@tony-laptop:~/Desktop/ALSA/alsa-tools-1.0.16$ ls
ac3dec         hdspconf    mixartloader    sb16_csp      usx2yloader
as10k1         hdsploader  pcxhrloader     seq           vxloader
echomixer      hdspmixer   qlo10k1         sscape_ctl
envy24control  ld10k1      rmedigicontrol  us428control
tony@tony-laptop:~/Desktop/ALSA/alsa-tools-1.0.16$ ./configure
bash: ./configure: No such file or directory
tony@tony-laptop:~/Desktop/ALSA/alsa-tools-1.0.16$ make
make: *** No targets specified and no makefile found.  Stop.
tony@tony-laptop:~/Desktop/ALSA/alsa-tools-1.0.16$ sudo make install
make: *** No rule to make target `install'.  Stop.
tony@tony-laptop:~/Desktop/ALSA/alsa-tools-1.0.16$

---

### Post by glennric on 2008-03-03
You are trying to execute the file "configure" which does not exist.  If you have a tar file, you need to extract it.

---

### Post by Whiffle on 2008-03-03
Where did you get this tar file?  It doesn't look like sources to me for some reason.

---

### Post by glennric on 2008-03-03
Is there a reason you are trying to install alsa-tools from source rather than from the repositories?

---

### Post by tonymoloney on 2008-03-03
Sorry for the late reply - I had to go out to fix another computer.
I'm installing all the ALSA software from source rather than the repositories because the repositories are only 1.0.14 and the latest source is 1.0.16
I'm doing this to try and fix a problem with alsamixer (snd_ctl_open failed) and Kmix (no device listed) something caused by another problem.
I got the advice to install the latest software from ALSA project, from this forum and whilst all the other tars unpacked and installed, the tools one gave the error.
So far, I've got Kmix to work again, but not alsamixer.
BTW, Amorak works but doesn't have any sound. I've checked Kmix to make sure the output isn't muted, but I think the problem lies with alsamixer.
Sorry, I've got to go out again (it's 10:00am in Perth) but I'll try to keep this going when I return.

---

### Post by tonymoloney on 2008-03-03
OK, I'm back and I seem to have solved my problem. Don't know if the thread deserves to be marked as "solved" because I didn't really solve the error in installing .tar files, but at least I have my sound back!
It seems that amongst all the files I had installed for ALSA, there was a Gnome Mixer, which had the output volume set at zero. I didn't even look for this at first because I'm running Kubuntu, and therefore Kmix, but I decided to check out all the multimedia apps to see which were working and which were not. The result - some work, some don't, but the ones I want to work,do, so I can now take my time and get the rest working as and when I want them.

---


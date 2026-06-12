---
title: "shutdown xserver"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by macoxp on 2006-05-06
Hi I'm trying to shut down xserver. anyone know the command? closest thing i've found was the ctrl + alt + backspace that restarts it. but I'm looking for a shutdown command that will leave only the command line open.

---

### Post by olsonar on 2006-05-06
Well, crtl + alt + F3 switches to command line, but it leaves X running on crtl +art + F7

---

### Post by eddie303 on 2006-05-06
sudo /etc/init.d/gdm stop

---

### Post by macoxp on 2006-05-06
Yeah i know about the ctrl + alt + f1, f2, f3, f4 thing. but I need to shut it down all the way. I also tryed sudo /etc/init.d/gdm stop did not work. said command not found. I'm useing kubuntu btw.

---

### Post by eddie303 on 2006-05-06
then substitute gdm with kdm IMHO.

---

### Post by macoxp on 2006-05-06
tryed the kdm IMHO no luck :confused: maybe there is a command when booting to have it not boot like the boot to command prompt in windows?

---

### Post by eddie303 on 2006-05-06
I hope you did not write there "IMHO" :D
You did try this way? :
/etc/init.d/kdm stop
If this does not work, look in /etc/init.d for files similar to kdm or xdm, and try them as this.

---

### Post by macoxp on 2006-05-06
yeah i did this:

sudo /etc/init.d/kdm stop no luck I'll try and look around.

---

### Post by eddie303 on 2006-05-06
Well, you can boot it into the command line, on the grub screen press E on the Ubuntu option, and again with E, edit the line, where it says:

kernel vmlinuz....
at the end of the line enter 3 such as:
kernel vmlinuz-<whatever> root=<whatever> 3
then press B to boot.

---

### Post by macoxp on 2006-05-06
I got it working thanks alot. but now i have a biger problem. The reason I was trying to get it to close was to install the nvida video drivers. but it wont install... installer runs but it wont finish.

---

### Post by eddie303 on 2006-05-06
Try to install it this way:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

If you have an older card, like a TNT2, install nvidia-glx-legacy.
Many people complained for installer hangs.

---


---
title: "Bunch of questions for new user"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by smmalis on 2007-09-10
I'm new to Ubuntu and have many questions.
1. How can I change the timeout on sudo?
2. How can I enable su?
3. How can I play mp3s (once I get my sound driver working)
4. Can I import stuff from my Firefox and Thunderbird on Vista into Firefox and Evolution (or Thunderbird) on Ubuntu?
5. I have an Nvidia 8800 GTS.  Why can't I enable the driver (nvidia-glx-new) without X crashing?
6. Is there an idiot's guide to Wine?
7. How can I compile and run C++ and Java programs (no IDE, just build and go)?
8. In GRUB there are two entries for Ubuntu, one ending in 15 and the other in 16.  Is there a way to remove the 15?
9. I have a website hosted on a Debian machine that I connect to through ssh.  Is there a way to connect on bootup/login?

I think thats it for now.  Thanks in advance.

---

### Post by lisati on 2007-09-10
> **smmalis said:**
> I'm new to Ubuntu and have many questions.
3. How can I play mp3s (once I get my sound driver working)
Sometimes using update manager (check the System->Administrator menu) can help
> 
7. How can I compile and run C++ and Java programs (no IDE, just build and go)?

There's G++ at the command line

---

### Post by SOULRiDER on 2007-09-10
1) I Believe you need to edit the sudoers file.
2) IMHO you shouldn't do it, sudo is there for a reason.
3) [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
7) ```
 sudo aptitude install build-essential sun-java6-jkd[/code[
To compile C++:
[code]g++ <source> <options>
```
To compile Java:
```
javac <source> <options>
```
8) Use the package manager to remove the unwanted older kernels.

---

### Post by VraiChevalier on 2007-09-10
> **SOULRiDER said:**
> 
8) Use the package manager to remove the unwanted older kernels.

Is it recommended to remove older kernels?

---

### Post by rusty4r on 2007-09-10
8. ```
gksudo gedit /boot/grub/menu.lst
```
then scroll down to the entries and type # in front of the entry for 15, save and your done they will still be there if you need to go back just delete the #

here is a portion of mine

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-12-generic
boot

#title		Ubuntu, kernel 2.6.17-11-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-11-generic
#quiet
#savedefault
#boot

---

### Post by overdrank on 2007-09-10
rusty4r glad to see you :)

---

### Post by SOULRiDER on 2007-09-10
**VraiChevalier **
Older kernel can be kept but remember kernels are well tested here, and they ahve been out for a while so theres nothing wrong in removing olde rones.

**rusty4r **
That will only remove the GRUB entries which IMHO is a bad idea, why keep the kernel files if youre not gonna use them?

---

### Post by alwiap on 2007-09-10
6. try using this guide - [http://wiki.winehq.org/FAQ]("http://wiki.winehq.org/FAQ"), it helped me out a lot

and

try searching on the forums for a specific program (many people try to use wine for the same programs, so someone most probably has had your problem if it is a popular program)

Good luck!

---

### Post by rusty4r on 2007-09-10
> **SOULRiDER said:**
> 
That will only remove the GRUB entries which IMHO is a bad idea, why keep the kernel files if youre not gonna use them?

I like having them and there's nothing wrong with keeping the last one, I've read about people needing to revert back after an update many times

---

### Post by smmalis on 2007-09-10
So then:
Answered:
1. How can I change the timeout on sudo?
2. How can I enable su? 
7. How can I compile and run C++ and Java programs (no IDE, just build and go)?  
8. In GRUB there are two entries for Ubuntu, one ending in 15 and the other in 16.  Is there a way to remove the 15? 
6. Is there an idiot's guide to Wine?

Still to be answered:

3. How can I play mp3s (once I get my sound driver working) Looking for a program specifically.
4. Can I import stuff from my Firefox and Thunderbird on Vista into Firefox and Evolution (or Thunderbird) on Ubuntu?
5. I have an Nvidia 8800 GTS.  Why can't I enable the driver (nvidia-glx-new) without X crashing?
9. I have a website hosted on a Debian machine that I connect to through ssh.  Is there a way to connect on bootup/login?

Thanks again.

---

### Post by lisati on 2007-09-10
For mp3s, check out "Rhythmbox"

---

### Post by enzeru on 2007-09-10
as for firefox and wine I think if you install drivers to access your ntfs partition (ntfs-3g seems to be the preferred if not only) you can use the instructions [here]("http://kb.mozillazine.org/Roaming_profile#How_can_I_share_a_fixed_profile.2C_such_as_on_dual-boot_machines.3F") to run both operating systems versions off the same profile for firefox and thunderbird

---

### Post by Xorg.conF on 2007-09-10
in ubuntu to play mp3s, it has no codecs installed to play them due to legal reasons who knows, but a music player will prompt you to download and install the codecs, since there are others or amvs mp4s quick time etc I recommend that you go to add/remove and type Gstreamer and install all 4 codec packages .

---

### Post by Maestro23 on 2007-09-10
> **lisati said:**
> For mp3s, check out "Rhythmbox"

For MP3, playing DVD, etc.. you will need Restricted Formats.

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jeramiahx on 2007-09-10
When I tried to play and mp3 for the first time it asked me if I wanted to install a codex that was for research only..... I think it was in the totem movie player...

---

### Post by smmalis on 2007-09-11
So then:
Answered:
2. How can I enable su? 
7. How can I compile and run C++ and Java programs (no IDE, just build and go)?  
8. In GRUB there are two entries for Ubuntu, one ending in 15 and the other in 16.  Is there a way to remove the 15? 
6. Is there an idiot's guide to Wine?
3. How can I play mp3s (once I get my sound driver working) Looking for a program specifically.
4. Can I import stuff from my Firefox and Thunderbird on Vista into Firefox and Evolution (or Thunderbird) on Ubuntu?

Still to be answered:
1. How can I change the timeout on sudo? Need details on how to edit sudoers file.
5. I have an Nvidia 8800 GTS.  Why can't I enable the driver (nvidia-glx-new) without X crashing?
9. What is the difference between sudo & gksudo?

Thanks again.

---

### Post by hartdg on 2007-09-29
> **smmalis said:**
> So then:


Still to be answered:
1. How can I change the timeout on sudo? Need details on how to edit sudoers file.
5. I have an Nvidia 8800 GTS.  Why can't I enable the driver (nvidia-glx-new) without X crashing?
9. What is the difference between sudo & gksudo?

Thanks again.

For item 5.  Nividia 8800 GTS problem:

This issue is related to 2 registered bugs in Ubuntu (Feisty) and appears to be a problem with the package compilation. I had the same problem and managed to solve it with support from Launchpad. Have a look at the tail end of the link below.

[https://answers.launchpad.net/ubuntu/+question/10159](https://answers.launchpad.net/ubuntu/+question/10159)

---

### Post by rich.bradshaw on 2007-09-29
sudo for command line apps

gksudo is for graphical apps, and brings up window to enter password.

---


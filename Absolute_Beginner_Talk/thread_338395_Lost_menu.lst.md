---
title: "Lost menu.lst"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by tshendruk on 2007-01-14
What I did:
I lost my boot/grub/menu.lst.
I was going to making some changes to it and so went to back it up and accidently lost it in the move.
There was a menu.lst~ so I restored that.
I rebooted to check.
Everything seemed to go ok and Ubuntu was booting up but once it was done it flashed black and came back to the kubuntu bootup splash screen and got stuck there.

I can enter recovery mode and from there I can go to menu.lst. In menu.lst this is what I see

     title      Ubuntu, kernel2.6.15-27-amd64-generic
     root      (hdo,1)
     kernel   /boot/vmlinuz-2.615-27-amd64-generic root=/dev/sda2 ro quiet s$
     initrd     /boot/initrd.img-2.6.15-27-amd64-generic
     save default
     boot

     title       Ubuntu, kernel2.6.15-27-amd64-generic (recovery mode)
     root      (hdo,1)
     kernel   /boot/vmlinuz-2.615-27-amd64-generic root=/dev/sda2 ro single
     initrd     /boot/initrd.img-2.6.15-27-amd64-generic
     boot

     title       Ubuntu, memtest86+
     root       (hd0,1)
     kernel    /boot/memtest86+.bin
     boot
     .
     .
     .
     windows

If I enter "$ startx" things once again seem ok until I reach this output
     FATAL: module nvidia not found
     (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
     (EE) NVIDIA(0): ***Aborting***
     (EE) Screen(s) found, but none have a usable configuration

     Fatal server error:
     no screens found
     XIO: fatal IO error 104 
     .
     .
     .

I'm not sure what NVIDIA has to do with my problems but then again I'm not sure what my problem is. 
Thanks for any help, I don't want to have to lose everything.

---

### Post by stijn_pol on 2007-01-14
Don't know what this has to do with your menu.lst problem, but this error may be due to a problem in /etc/X11/xorg.conf.  Under the section "Screen" your nvidia card should be configured. Check if it's there...

---

### Post by tshendruk on 2007-01-14
I looked into /etc/X11/xorg.conf:

The screen section has an identifier for my monitor and then breaks into a bunch of subsections about display modes. At the very top of the xorg.conf is 
#nvidia-xconfig:Xconfiguration file genrated by nvidia-xconfig

This was all working fine before. Would this have gotten changed if I screwed up my grub menu?

---

### Post by stijn_pol on 2007-01-14
It is very unlikely to have changed. 
I don't know what  could have happened since it was all working fine before.
In that same xorg.conf, under "device" something about nvidia should be listed to.
I'm afraid I can't help any further...

---

### Post by tshendruk on 2007-01-14
Thanks for the ideas, stijn_pol.

PS
I'm still stuck for anyone with ideas.

---

### Post by arnieboy on 2007-01-14
do the following:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
and see if that helps (It will regenerate your menu.lst)

---

### Post by tshendruk on 2007-01-14
So I gave it a whirl:
Resulting output:

bash: uname-r: command not found
dpkg-reconfigure: cannot connect to X server
debconf: unable to initialize frontend: Kde
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
package 'linux-image-' is not installed and no info is available

---

### Post by stijn_pol on 2007-01-14
watch the space between uname and -r, :-)
because now, he is looking for a command called uname-r, this doesn't exist, its uname with option: -r

---

### Post by tshendruk on 2007-01-14
Thank you so much! This a huge relief. 

What exactly did you have me do there?

Thanks again!

---


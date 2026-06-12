---
title: "ubuntu on powerbook g3 wallstreet: cdrom"
date: 2008-11-10
forum: Apple Hardware Users
---

### Post by tiny969 on 2008-11-10
hey!
new to ubuntu i'm wondering why ubuntu 8.10 cd for powerpc does not recognize the cdrom during the installation... even if i try to do it manually (/dev/disk1 on my system i guess) it does not find it and stops installation with an error...

does anybody know what's wrong here?

thx!

---

### Post by cyberdork33 on 2008-11-10
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by tiny969 on 2008-11-10
oh, did not find that thread...
thx a lot! will try tomorrow!

---

### Post by tiny969 on 2008-11-11
works! finally installed ubuntu 8.10 on a powerbook G3 wallstreet. takes a while to boot and loading environment :) aprox. 5 min *gg
but seems to run stable.

thx again for the hint!

---

### Post by chrispis on 2008-11-14
When you get the error message, press <ALT(Option)-F2> to switch to a terminal window and type:

modprobe ide-scsi

Get back to the installer with <ALT-F1>, say No to the floppies screen, say Yes to the Manually select.. screen, and choose 'cdrom' or 'cdrom0'. If it still doesn't work, go back to Detect and Mount CDROMs.

Has worked for me but now I have othr problems...

---

### Post by OpEdMunkey on 2008-11-15
Curious as to what other Ubuntu versions you may have tried. I inherited a Wallstreet and am playing with Xubuntu 6.10 now. Close but not 100% running gui.

---

### Post by Odemia on 2009-04-21
Thanks for the posts.  Ran into the same problem installing 8.10 on a Powerbook Alu 15" 1.5GHz.  Had to use ctrl+option/alt+F2.

I was also briefly confused I didn't have the keyboard setup as a apple-laptop keyboard so the fn and function keys weren't working.  Got that all straightend out though.

---


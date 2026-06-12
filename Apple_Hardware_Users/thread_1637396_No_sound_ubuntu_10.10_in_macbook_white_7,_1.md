---
title: "No sound ubuntu 10.10 in macbook white 7, 1"
date: 2010-12-04
forum: Apple Hardware Users
---

### Post by caith_sit on 2010-12-04
Hello!

I installed ubuntu 10.10 in my macbook white 7,1 and as always I am impressed with the support of most of the hardware. Almost everything works, but the sound and the brightness control do not. The sound one is the one that I am more concerned about.

I tried to solve it using the documentation for MacBook Pro 7,1 Ubuntu 10.10 (Maverick Meerkat) but the solution did not work...

Does anybody have an idea how to solve the issue?

---

### Post by caith_sit on 2010-12-23
After a long time i found the solution

1.) Try this command in terminal:
    gksudo gedit /etc/modprobe.d/alsa-base.conf

2.) Then scroll to the very end of the file, and add this line:
    options snd-hda-intel model=mbp55

--don't forget to save the file

3.) Delete ~/.pulse

4.) Reboot

5.) In terminal,run "gnome-alsamixer"

6.) Uncheck the box next to "IEC958", but leave
    the "Surround Speaker" and "IEC958 Default PCM" 
    boxes checked.


The only thing is that in the step 6 I only checked the Surround Speaker then I raised the volume and I got the sound working!! =)

---

### Post by Jalfro on 2011-01-04
Thanks caith_sit, I managed to get sound working on my Macbook 6.2 by simply installing gnome-alsamixer and doing your steps 5 & 6.

---

### Post by DeadlyBlonde on 2011-01-05
Thanks, this works (steps 5 and 6) for MBP 7.1 with 10.10.

---

### Post by TheDudeAlex on 2011-04-06
Works with macbook 5,5!!

Thanks!

---

### Post by labaom on 2011-04-07
Did you guys ever get the screen calibration working on your 7,1 model?

---


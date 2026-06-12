---
title: "Error-Newbie Alert"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by -Race- on 2006-09-04
I am installing Ubuntu and throughout parts of the installation I get this error.Either that or its a part of it. It states Failed to start the X Server ( yiyr graphical interface) It is likely that it is not set up correctly. Which has be stumped. What to do?

---

### Post by meng on 2006-09-04
Are you talking about booting the LiveCD before even getting to installation, or the actual installation itself, or booting your system after installation?

---

### Post by -Race- on 2006-09-04
From the LiveCD for the first bootup.

---

### Post by meng on 2006-09-04
Can you share your system specifications please?

---

### Post by -Race- on 2006-09-04
Intel Pentium 4 Hyper Threading Processor 2.80 GHz 1MB L2 Cache 800MHz Front Side Bus
1.5 gigs of RAM
160 gig HD
ATI Radeon x850XT
Off the top of my head thats all I really know but I did some research which I shouldve done before and I found a place that seems hepful.
[http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem-2.html](http://www.linuxforums.org/forum/debian-linux-help/41622-new-linux-ubuntu-install-gui-problem-2.html)
After trying out some suggestions there I"ll update.

---

### Post by meng on 2006-09-04
Hooo mama that's a pretty nice system.

---

### Post by -Race- on 2006-09-04
Tried some of these commands
sudo apt-get install xserver-xorg

sudo dpkg-reconfigure xserver-xorg

doesnt seem to do much if at all. I'm really confused at to what to do possibly a faulty burn?
Possibly drivers? I use Omega Drivers instead of the official ATI's  should I try that?

---

### Post by meng on 2006-09-04
Have you already got another OS (Windows) installed on this system? Were you definitely going to go ahead and install Ubuntu anyway? You could try reburning at a lower speed just in case that's the problem, particularly if you wanted to see the LiveCD in action before deciding whether to go ahead and install. If you were already set on installing, the other option is to use the text-based installer on the Alternate CD (separate ISO download). Probably those commands you tried would work better on an installed system rather than a LiveCD.

---

### Post by -Race- on 2006-09-04
I was really aiming to try it out first and all before I choose to take the dive and install. However I tried the command 
sudo dpkg-reconfigure xserver-xorg 
I get a window where I configure it and does it auto detect my settings and just breeze through it or would it be best to just read it through?

---

### Post by meng on 2006-09-04
You could do either. For example, just choose the defaults the first time through and then type startx when you're done. If it doesn't work, just repeat the process but be more choosy this time. For the graphics driver, I would advise trying ati first, but if that fails choose vesa.

---

### Post by -Race- on 2006-09-04
I just went through configuring the setting and end up at a black screen and just wanted to know. Whats the command to reboot?

---

### Post by meng on 2006-09-04
Black as in pitch black, can't see anything?
Try
sudo reboot
(although if it were me I'd probably just press the reset button on my box...)

---

### Post by -Race- on 2006-09-04
No not pitch black just some text.

---

### Post by meng on 2006-09-04
Gotcha
reboot
(or maybe sudo reboot)
is what you want

---


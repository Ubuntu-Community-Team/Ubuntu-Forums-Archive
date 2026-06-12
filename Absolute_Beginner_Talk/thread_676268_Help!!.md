---
title: "Help!!"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by tonytaz on 2008-01-23
hi. I have a bad problem. Ive got a fujitsu siemens amilo pro laptop wich I installed kubuntu on yesterday. the problem is that I can't access kde at all

when i try to start it , the screen just goes shimmering and blure so I cant see whats standing on the screen..

Is there anyone who can help me fast with this problem?

---

### Post by sports fan Matt on 2008-01-23
Could there be an issue with the brightness of the laptop?  Once, I had a laptop, and after a few months the screen completely turned an off white and pasty killing half the screen, but I hope its not that bad for you..

---

### Post by Hospadar on 2008-01-23
what sort of video hardware does it have? you could try (in a text terminal, do a ctrl-alt-F1) "sudo dpkg-reconfigure xserver-xorg" and select "vesa" as your driver on the first page of the dialog and then you'll at least be able to get some GUI happening and then maybe you can worry about some restricted drivers for your hardware.

to restart kde after you do the above I belive you can do "sudo /etc/init.d/kdm restart" (or just restart the machine)

---

### Post by tonytaz on 2008-01-23
no, the screen works fine during installation and in command line. but when i try to execute startx it just keeps bumping and i extremely blur and the whole picture is shakin badly..

its a bit hard to explain...

I tried ti install 915resolution (ive godt intel graphics) but when im trying to download it (apt-get install 915resolution) it cant find the package on some kind of archive on the web..

what to do?

thanks for every reply

---

### Post by tonytaz on 2008-01-23
this is what the screen looks like if I execute startx

---

### Post by tonytaz on 2008-01-23
> **Hospadar said:**
> what sort of video hardware does it have? you could try (in a text terminal, do a ctrl-alt-F1) "sudo dpkg-reconfigure xserver-xorg" and select "vesa" as your driver on the first page of the dialog and then you'll at least be able to get some GUI happening and then maybe you can worry about some restricted drivers for your hardware.

to restart kde after you do the above I belive you can do "sudo /etc/init.d/kdm restart" (or just restart the machine)

ive tried that now. it did'nt work:(

---


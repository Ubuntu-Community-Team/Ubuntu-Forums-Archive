---
title: "Toshiba A-105 S-1014 Laptop Sound"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Kunks on 2007-11-28
I've read the posts about sound issues for laptops & there seems to be a lot of lot of different solutions depending on what laptop you have one size doesn't fit all... it seems some solutions work for some laptops so I'm throwing my problems out to hopefully save some time...(I've already invested a lot to solve this. Everything else is working awesome & if I can solve this I'll probably dump the windows half of my partition.....

---

### Post by bharris25 on 2007-11-29
Try adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

Then reboot and see if that works.:guitar:

Worked for me and I have the same alc 861 realtek card in my a105 toshiba satellite

---

### Post by Kunks on 2007-11-29
Thanks for trying to help but how do I get to /etc/modprobe.d/alsa-base in the terminal to enter solution you have suggested??sudo 1st on that line?Last time I was in that place I don't know how I got there (I probably did copy & paste in terminal) from a forums possible solution I might have even changed some of the lines by accident whilst trying to fix last time I was there..If I copy & paste in terminal /etc/modprobe.d/alsa-base it says permission denied.........

---

### Post by bharris25 on 2007-12-02
sudo gedit /etc/modprobe.d/alsa-base

that will open the page with root permission so you can edit, the go down and add the options line to the end and reboot and hopefully you will be wiping windows off next, let me know how it goes.

---


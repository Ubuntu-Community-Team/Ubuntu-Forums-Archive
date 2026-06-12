---
title: "copying and moving xorg.conf"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by staib on 2006-11-06
Hi all

I think that something in my xorg.conf file is preventing my booting into 6.10 - I had to change graphic cards after a problem with an ATI card (now have an nvidia) - anyway I have now managed to get into 6.10 with a boot CD and would like to copy the current xorg.conf file over my old one to see if that helps. Not sure how to do that - I can't "see" the original etc/x11.xorg,conf from here - but there must be a suitable console command!
Any help appreciated!
Nick

---

### Post by taurus on 2006-11-06
Open a terminal, Applications -> Accesories -> Terminal, from the LiveCD and type in these commands, assuming that you already mounted your harddrive where / is (in /mnt/ubuntu).

```

sudo mv /mnt/ubuntu/etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf.bak
(That would be capital X with number 11 after...)
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf

```
Otherwise, boot your Ubuntu into recovery mode from GRUB menu and at the prompt, reconfigure your X again...

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bodhi.zazen on 2006-11-06
First mount your ubuntu root partiton.

Then open a terminal.

```
cd /ubutnu_root/etc/X11
sudo cp xorg.conf xorg.conf.bak
sudo cp /etc/X11/xorg.conf .
```

You could likely do it graphically with:
```
gksudo nautilus
```
navigate to the various locations.

---

### Post by ahaslam on 2006-11-06
At the grub screen select 'recovery mode'
log in at the prompt then type: sudo dpkg-reconfigure xserver-xorg
Then reboot: sudo reboot

If that doesn't get you sorted try: sudo nano /etc/X11/xorg.conf
find the graphcs section and change the driver to 'vesa'
Press 'ctrl + X', 'Y' & 'ENTER'
sudo reboot

I hope that helps.

EDIT: HOW SLOW WAS I ??

---

### Post by staib on 2006-11-06
Thanks Guys, I went into grub option 2 (recovery mode) and simply typed:

dpkg-reconfigure xserver-xorg

I can't tell you how many times I tried and failed yesterday doing the same sort of thing.  The difference was this time just out of the blue I decided to then type "exit" (I'm so new to this I did not even know it was a command, it just seemed a logical thing to do). That made the difference and took me straight back to the graphical desktop.  :p 

Cheers,

Nick

PS - You might have been marginally slower Anthony, but though they say "the early bird gets the worm" the worm that gets up late lives another day :-)

---

### Post by ahaslam on 2006-11-06
> **staib said:**
> PS - You might have been marginally slower Anthony, but though they say "the early bird gets the worm" the worm that gets up late lives another day :-)
Could you say that to my boss ;)

---


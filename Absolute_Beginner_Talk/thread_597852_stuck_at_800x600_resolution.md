---
title: "stuck at 800x600 resolution"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by JustifY on 2007-10-30
Alright, I'm stuck at 800x600 resolution right now, read threads relating to it, I suppose I'll have to install Ubuntu to my hard drive instead of using the disk, because you can't do a smooth restart with it for driver updates (requires you to eject between shutting down and restarting). Here is my graphics card: Nvidia GeForce 6150 LE



After setting up my drivers, what are possible commands I may have to run through the terminal?

---

### Post by skyjacker on 2007-10-30
> **JustifY said:**
> Alright, I'm stuck at 800x600 resolution right now, read threads relating to it, I suppose I'll have to install Ubuntu to my hard drive instead of using the disk, because you can't do a smooth restart with it for driver updates (requires you to eject between shutting down and restarting). Here is my graphics card: Nvidia GeForce 6150 LE



After setting up my drivers, what are possible commands I may have to run through the terminal?  Try this procedure
Try this procedure:

1) Back up the present xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

2) Stop gdm
sudo /etc/init.d/gdm stop (or kdm for kde)

3) Edit xorg.conf
sudo dpkg-reconfigure xserver-xorg

4) Select the resolutions you want available by arrowing down to each desired line and pressing the &#8220;space bar&#8221; to place an X to the left.

5) Validate your choices with &#8220;enter&#8221;

6) restart X with Control+Alt+Backspace

7) Choose the desired resolution under the &#8220;Systems/Preferences/Screen Resolutions drop down list

---


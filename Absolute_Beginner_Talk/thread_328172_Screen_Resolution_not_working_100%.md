---
title: "Screen Resolution not working 100%"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Teres on 2006-12-30
Hi. i just installed Ubuntu today and i need some help. when i was using Windows, i was able to have a 1024x768 resolution. now i am limited to 800x600. wat do i do?

---

### Post by shanepardue on 2006-12-30
What video card are you using? You'll need to install the driver for your video card.

---

### Post by steve.horsley on 2006-12-30
Open a comand line - Progrms->Accessories->Terminal
Make a backup of the file /etc/X11/xorg.conf with this command:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
Then run this command. Take the defaults where you're not sure,  but when you get to the question about resolutions, you can pick the set of resolutions you want:
**sudo dpkg-reconfigure xserver-xorg**
then log out and back in again.

If things go horribly wrong you can recover the original configuration by pressing Ctrl-Alt-F2 to get to a text login screen, logging in and entering these commands:
[B]sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart[/B]

---

### Post by Teres on 2006-12-31
i am using a built in vga card. its a sis motherboard. in device manager it says its a vga sis 661/740/... i cant remeber exactly. where can i find the driver?

---

### Post by Teres on 2007-01-02
The model is the 661/741/760/761 PCI/AGP VGA Display. thats wat it says in the device manager. i still need the driver. cant find it. can u help me plz?

---


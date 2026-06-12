---
title: "Install help - blank screen"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Hooliosphere on 2007-09-04
Hi,

I'm trying to get Xubuntu installed on my:

PIII 667Mhz 192MB RAM
it has a 3dfx Voodoo3 graphics card
and it has 30GB of hard drive space

I keep getting a blank screen, so I've booted into recovery mode and tried changing the xserver settings, but i'm completely lost.

I think it's an issue with my video card conflicting with the onboard video.  I've gone into the bios but i can't see a way to disable the onboard video.  The onboard video doesn't work during start up, but after I get to the  blank screen, if I switch the monitor cable to it, i get a very low resolution screen of the xubuntu desktop

help

---

### Post by oilchangeguy on 2007-09-04
why not just remove the pci video card. and use the onboard video.

---

### Post by Hooliosphere on 2007-09-04
Well, I was hoping to use the card, partly because I have it and partly because I want to learn how to make it work

---

### Post by oilchangeguy on 2007-09-04
why not get ubuntu up and running. see if the computer has any other issues, tackle those. and then try the new video card.

---

### Post by WebSiteGuru on 2007-09-04
I agreed with oilchangeguy. Get ubuntu up first.

---

### Post by afonic on 2007-09-04
This one can be tricky.

I *think* X.org can handle both cards and you just have to select the Voodoo in the "Device" field if your "Screen" Section in xorg.conf, but I have not ever tested it.

Can you login even in the low resolution desktop and post the contents of the /etc/X11/xorg.conf file?

---

### Post by Hooliosphere on 2007-09-04
Now I can't get to the desktop at all whether I use onboard or not.  I've tried the voodoo driver as well as vga and vesa.  I've keep my resolution to 800x600 and 8bit colour.  How do I display the contents of the xorg.conf file?

---

### Post by Hooliosphere on 2007-09-04
Ok, I got the onboard working again under vga.... i'm not sure what the resolution is, but it's so small i can't see the windows to check it

---

### Post by afonic on 2007-09-04
You can open a Terminal and type

gksudo gedit /etc/X11/xorg.conf

Copy and paste it here.

---

### Post by Hooliosphere on 2007-09-04
it just says

Gtk-WARNING **: cannot open display:

---

### Post by WebSiteGuru on 2007-09-04
try sudo gedit /etc/X11/xorg.conf

---

### Post by afonic on 2007-09-04
> **Hooliosphere said:**
> it just says

Gtk-WARNING **: cannot open display:

I meant when you are inside the GUI. If you are in the command line, try sudo nano /etc/X11/xorg.conf

Imo you should set up Ubuntu to run in the on board card and then we can work out making the Voodoo work.

---

### Post by WebSiteGuru on 2007-09-04
> **afonic said:**
> I meant when you are inside the GUI. If you are in the command line, try sudo nano /etc/X11/xorg.conf

Imo you should set up Ubuntu to run in the on board card and then we can work out making the Voodoo work.

[QUOTE=Hooliosphere]Ok, I got the onboard working again under vga.... i'm not sure what the resolution is, but it's so small i can't see the windows to check it[/QUOTE]

I think that what Hooliosphere did already.

@ Hooliosphere - Run it in the Terminal commandline.

---

### Post by Hooliosphere on 2007-09-04
I ran sudo nano /etc/X11/xorg.conf

It said "window size too small"

my window is really really cramped..... the clock takes up 1/5 of the screen

---

### Post by WebSiteGuru on 2007-09-04
> **Hooliosphere said:**
> I ran sudo nano /etc/X11/xorg.conf

It said "window size too small"

my window is really really cramped..... the clock takes up 1/5 of the screen

Try Ctl - Alt - F1 and login with your username and password. Then run  sudo nano /etc/X11/xorg.conf from there. (you might need to put in your password.)

After you are done Ctl - o and hit Enter. And Ctl - x to exit.

Then sudo reboot.

---

### Post by Hooliosphere on 2007-09-05
I can't get the onboard to display properly and it doesn't work at all during start up.

I did a lspci rom the commandline and found my video card is at:  0000:01:0b.0

but I'm not sure how to enter this when I do a sudo dpkg-reconfigure xserver-xorg

I've tried different variations when entering the PCI Bus but I get formatting errors

I think if I can enter the right bus it will work.  What is the proper format?

---

### Post by WebSiteGuru on 2007-09-05
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by Hooliosphere on 2007-09-05
I didn't see anything about changing the PCI Bus

---

### Post by Hooliosphere on 2007-09-05
Figured it out

By using the TDFX driver, leaving the PCI Bus blank and by using 8bit colour

I can now use the video card

---

### Post by WebSiteGuru on 2007-09-05
good job!

With your voodoo card you will probably need to use a restrictve driver. You will need to find out what is the right driver for it. And plug it in.

---


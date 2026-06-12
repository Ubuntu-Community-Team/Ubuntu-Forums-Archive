---
title: "[SOLVED] Extreme Help!!! ATI graphics card install"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by JimBuntu on 2007-11-04
So i just bought the ati visiontek x1550 agp card. Thought all i had to do was install into the system and ubuntu would take care of the rest, but it wont work. When i boot up, at the point where it says something like Grub loading... it goes to a blue screen saying something about x server failed to load, and then something about looking at the output of x server, then something about can not detect screen. 

you get the picture...

So i turned off the computer and took the card out, and it obviously was back to normal. I tried downloading some packages and stuff that i read about in the wiki and here in posts and installed the card again and same thing. I also tried changing the video card setting in bios to agp/something... nothing is working. I dont think its even reading that i have a ati card. I have a dvi to vga adapter going from the card to the monitor. 

ive also tried to go to restricted devices and load something but it said i didnt need any, but this was when the card was NOT installed. What the hell do i do????

please help.

---

### Post by wPwLUi3N on 2007-11-04
It is rare but a possibility that you may have a corrupted or damage hardware.

Make some trial run on friend's machine and other O.S. .... it can be a ubuntu's fault but better knock out the possibility of harware damage.

Otherwise try ENVY software to install the driver for your card and then try re putting it into the socket.

Also make sure that your motherboard supports that card and you have properly placed into socket.

---

### Post by JimBuntu on 2007-11-04
could it be the power supply which is making the system think nothing is there? The box says : 300W recommended. Mine is stock at 200W. I'm wondering if this really matters. I looked at the card while it was installed and i did not see the fan running.

---

### Post by wPwLUi3N on 2007-11-04
it is really stupid to run hardware on low power supply than it needs.

It is risky and you risk damaging your entire hardware (if it has not happened yet), not only your card. Also my friends computer exploded in such case giving him burn injuries, so please take precautions.

Also you definitely need a bigger power supply for a graphic card.

---

### Post by P4man on 2007-11-04
the fan should spin, your card is probably hosed. What motherboard do you have ?if its an old one, it probably is incompatible with that videocard:
[http://www.playtool.com/pages/agpcompat/agp.html](http://www.playtool.com/pages/agpcompat/agp.html)

---

### Post by JimBuntu on 2007-11-04
its just a bone stock HP 754n. 2.53ghz , 1 Gb Ram, shared video memory (which basically means none)

---

### Post by wPwLUi3N on 2007-11-04
i would recommend your get your system checked by skilled person.

I dont think some skilled engineer would install a 300W power demanding graphic card on a 200w power system.

---

### Post by ajmorris on 2007-11-04
in /etc/X11/xorg.conf are the ATI drivers specified under one of your 'device' sections? or is another driver specified. E.G, i have an nvidia card, so my section is this: 

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Also, what error does xserver output when you try to start x, other than cant connect to monitor.

Could you paste your whole /etc/X11/xorg.conf file please

---

### Post by Qaazim on 2007-11-04
I am having a veyr similar problem - but in reverse. I have had the Visiontek x1550 installed on my computer (PCI Slot 2) and everything works fine. However, now that I am installing Ubuntu 7.10 it says I must either configure the display or continue in low resolution. 

If I continue without entering into the configuration dialogue box it offers me, it freezes at "Running local boot script (/etc/rc.local).

If I attempt to configure, it does not seem to recognize the ATI Radeon Visiontek x1550. It seems to accept the changes, but returns to the same problem as above: "Running local...."

Since I do not have Ubuntu on my comp, I cannot seem to edit the xorg.conf file.

Lastly, attempting to install an earlier version (Fiesty) it at least gave me an output message. It did say the problem encountered was that something was not recognized at PCI 0:2:0. If that is Bus 0 Device 2 Function 0, then that is where the old Intel display adapter is.

Any suggestions?? :)

Thanks!

---


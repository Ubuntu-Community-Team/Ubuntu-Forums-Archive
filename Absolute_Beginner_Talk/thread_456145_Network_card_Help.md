---
title: "Network card Help"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Alasta on 2007-05-27
Hello every one I hope some one can help . I have just rescued from a skip to desktop PCs , I didnt have much idea what I was going to use them for, mainly I was worried about the environmental impact of just chucking them . The specs of  both machines are Pentium 650 coppermine 256mb of ram 10gb hard drive.

I googled "Linux" and there on the first page was the link to ubuntu . I downloade the image and installed ubuntu on one of them and it worked fine, if a little sluggish . It even detected the network card ( 3com 3c905c) and I was able to connect to my dsl broadband straght away .

On the other machine I tried xubuntu 7.04 alternate-386 and this worked but didnt detect the network card.Obviously being a Linux novice I have no clue about how to proceed . 

Eventually I would like to set up a Home network with these 2 pcs , to give me web access eamail and music streaming in my kitchen.


Kind regards



Alasta

---

### Post by Bachstelze on 2007-05-27
Please open a terminal, run *lspci* and paste what you get. Hopefully it'll tell us what kind of NIC the machine has.

---

### Post by Alasta on 2007-05-27
here it is

lalastair@Laburnum:~$ lspci 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03) 
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) 
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02) 
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) 
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) 
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02) 
00:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74) 
01:00.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65) 
alastair@Laburnum:~$  

That was fun,  I was typing ispci , not lspci....


Thanks for your fast reply


kind regards


Alasta

---

### Post by DJ Wings on 2007-05-27
Try "lspci -v", or if you know what type of card it is, just tell us.

---

### Post by houstonbofh on 2007-05-27
It looks like a standard 3com card.  It may be bad...  This happens when you dumpster dive for computers. :)  Try swapping cards.

---

### Post by Alasta on 2007-05-28
Good morning and thanks for your help . The NIC is working , as I said in my original post ubuntu 7.4 plugged and played this card and then connected to the web thru my cable modem . The problem I have is that xubuntu cant see this card at all .Presumably I need to do some sort of manual install ?

Kind regards


Alasta

---

### Post by ugm6hr on 2007-05-28
> **Alasta said:**
> Good morning and thanks for your help . The NIC is working , as I said in my original post ubuntu 7.4 plugged and played this card and then connected to the web thru my cable modem . The problem I have is that xubuntu cant see this card at all .Presumably I need to do some sort of manual install ?

Alasta

Depends.  

First try this in Terminal:
ifconfig

In Xubuntu, go to Applications -> System -> Network.
Select "Wired Connection" then click Properties.
Make sure "Enable roaming mode" is unselected, and select Automatic configuration (DHCP).
Then reboot with the ethernet cable plugged in.

This should work - given the description of your experience with Ubuntu.  If you want to be able to "Plug-and-Play" i.e. connect after booting - I think you need to install Network Manager and use the roaming mode.  Unfortunately, I couldn't find any way to install Network Manager without a live internet connection.  If you want it, after connection - open Applications -> System -> Synaptic Package Manager and search for "network-manager-gnome".

---

### Post by Alasta on 2007-05-28
Many Thanks to ugm6hr and everyone who contributed . I downloaded the unix driver from 3com on my windoze xp box and then installed it in terminal . Being used to xp when I hit the return key in terminal and nothing happened I assumed that it hadnt worked . however when I looked in the network manager there it was. I am typing this reply using the xubuntu PC .

I have to say I am very impressed with this operating system it is making this old PC into a perfectly usable PC.

Kind regards


Alastair

---

### Post by xpod on 2007-05-28
If theres one thing more fun than messing about with one *buntu computer it`s messing about with two:D

Good luck

---

### Post by ugm6hr on 2007-05-28
> **Alasta said:**
> 
I have to say I am very impressed with this operating system it is making this old PC into a perfectly usable PC.


I think Xubuntu7.04 is great too.  It does have a few quirks, but it is easily modifiable, and actually very powerful.

Just be aware that a lot of the Ubuntu HowTo's don't necessarily translate directly to Xubuntu, because the programs used are slightly different.  So if you see "enter in Terminal" they might need editing.  Simple rule of thumb: nautilus=thunar, gedit=mousepad.

And the lack of a default search for file function is a big problem - there is a solution to that in these forums (I use the gnome search tool, but catfish is apparently quite good).

---


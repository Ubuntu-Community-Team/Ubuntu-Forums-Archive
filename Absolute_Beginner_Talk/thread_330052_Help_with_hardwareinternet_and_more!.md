---
title: "Help with hardware/internet/ and more!"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Unreallinux on 2007-01-02
I've been using ubuntu for 3 days now on my laptop and I've been pretty impressed with what it can do. :D
Its faster than windows and since I was using mostly the same software before the move went smoothely.

But there have been some issues.

1. Wireless I just cant figure it no matter what I try. :( My card works but I can't get it to connect to my network with WPA.(I need this for my school too because thats what they use).

2. Printer sharing. Can I share a printer with my windows desktop once I get the wireless working? 

3. Head phone jack and Mic Jack isn't working. :( I need this so I can use skype, record classes in audacity and also so I can listen to music. :(

Please help, I'm desperate and don't want to go back to windows.

---

### Post by Unreallinux on 2007-01-02
Oh I forgot. If this helps here is my laptop:
[http://www.circuitcity.com/ssm/Toshiba-Satellite-15-4-Widescreen-Notebook-PC-L35-S2161/sem/rpsm/oid/165319/catOid/-12963/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Toshiba-Satellite-15-4-Widescreen-Notebook-PC-L35-S2161/sem/rpsm/oid/165319/catOid/-12963/rpem/ccd/productDetail.do)

Also here is my lspci log:
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:09:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

(someone else told me about that last one. I"m a linux noob. :( )

---

### Post by jml on 2007-01-02
I can give you some information on the wireless issue.  Wireless in general, and encrypted wireless in particular are very tricky to set up in Linux.  What version of Ubuntu are you using?  For the sake of discussion, lets assume version 6.10.  WPA encryption does not work out of the box with Ubuntu.  First check to see if the card is really working.  Temporarily disable encryption on your base station.  Now see if you can connect.  If you can, then you are half way there.  Next download and install (via Add/Remove programs, or Synaptic,) the following two applications.  network-manager and network-manager-gnome.  After its installed and functioning you will see a network icon in the right upper corner of your screen.  You access different aspects of the applet by either right clicking on the icon, or left clicking on the icon.  Its through this applet that you will set up WPA encryption.  If you search the Networking/wireless subforum using the terms network-manager and WPA you should find several documents to help you.  Good luck, and hang in there.  Linux really is better than Windows in my opinion.

Joe

---

### Post by Unreallinux on 2007-01-02
I'm using ubuntu 6.06
I can connect to networks without any encryption. So thats a plus. :D

I have those icons already.(I think maybe automatix put them there?) 
But I still can't figure it out. :(

---

### Post by Unreallinux on 2007-01-02
I got WPA to work!
I found this killer guide here:
[http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA)

Now if someone could just help me with my headphone and mike jacks I would be very appreciative. :D
I"M ALSMOST FREE FROM WINDOWS!!!!!!!! (I really can't get rid of it without all of my hardware working first though. :( )

---


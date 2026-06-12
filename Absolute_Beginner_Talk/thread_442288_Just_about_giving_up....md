---
title: "Just about giving up..."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by thatswho2 on 2007-05-13
Hi All,
I'm not totally new to Linux - I have run SuSe in the past, thought I would give Ku a try since I had a spare disk. 
2 days later I gave up on it and today installed Ubuntu 6.04 as it seemed to come with the packages I need.

Unfortunately not so. So, specific problems are, I have an Alcatel Speedtouch modem. so canot connect to the net through Ubuntu. I have printed of the instructions for doing so, however these specify the use of the package manager. I have the driver files in Windoze. So I put them on Floppy and CD.

No matter what, Ubuntu will not see them, and now refuses to mount the drives, and when it does it says I don't have the necessary permissions, but will not let me change them. (I am the only user). I can use sudo in a terminal, but when i try it that way the files are never found. GUIs don't prompt me for a pwd.

I also cannot find a - RUN command line anywhere.

My Windows partitions are listed in 'places', but won't mount, except for one which will not unmount, however I still can't see it since I don't have the permission, won't let me change it etc etc.

Life would have been so much easier if The speedtouch driver and the NTFS 3G was available to install, and there was a easy way of importing files from floppys etc.

How do I get around this please! before i give up.

Many thanks

G

---

### Post by juxtaposed on 2007-05-13
> I also cannot find a - RUN command line anywhere.

Do you mean the terminal? It's in the applications menu.

It's only in windows that you click on the run button to go to a command line.

---

### Post by gilgongo on 2007-05-13
I know this is going to be annoying, but networking and connecting to the net are far easier when you have a router and just connect your PC to that over Ethernet. Otherwise you're going to be at the mercy of a single modem vendor and it's crappy drivers (ie Alcatel). Is there any way you can get a router?

As to the other problems, I'm not entirely sure what they are since you don't provide much information. Why do you need to mount your Windows partitions anway? You do know that Windows programs don't run under Linux? Sorry if that's a stupid question but when you say "I also cannot find a - RUN command line anywhere" I just wanted to check on that...

---

### Post by jfinkels on 2007-05-13
Go here to find the terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Can you post the output when you type the following command in the terminal?
```
sudo fdisk -l
```
Type your password when prompted. This will list all your drives and partitions so we can help you get them mounted.

See here for lots of great introductory information: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by thatswho2 on 2007-05-13
Hi - many thanks, I'm ok using Terminal, but got confused by the documentation talking about run commands.
Kubuntu has a run command line. Ubuntu does not seem to have one. Fair Do's.

I do have an ethernet hub,(Netgear EN104) which is connected, but only to an unused old server (NT4). it is not connected to the net, and I must admit, i don't know how! The speedtouch is of course a USB thingy.

It can apparently work in linux, and I have the drivers, I just can't install them!

As for the windows, I just wanted to access my data, music pics and stuff, which again, apparently works, though obviously win progs will not. but I also thought I may be able to import the driver files I need direct from the HDD.

Any clues?

Thanks
g.

---

### Post by thatswho2 on 2007-05-13
Sorry - cant post the Fdisk result as I am using win. unfortunately!

g.

---

### Post by thatswho2 on 2007-05-13
Ok I have looked at the drives as best i can. sudo fdisk -1 is unvalid apparently. so I had a browse around. the only drives were the linux drives.

I tried to edit the etc/fstab table but didn't save it. now lost. will have to reinstall.

How do I connect to the net via ethernet Hub?

getting more disillusioned by the minute..
Graeme.

---

### Post by davahmet on 2007-05-13
That fdisk command is "sudo fdisk -l" using a lowercase "L" for list instead of -"1".

---

### Post by picpak on 2007-05-13
To get a run dialog, press Alt + F2.

---

### Post by thatswho2 on 2007-05-13
Hi thanks for the help. Have reinstalled and run fdisk it says...

By the way this is abbreviated since I had to write it all down etc...

Dev/ hda 320gb

dev/hda1*       1       13208         17       hpfs/ntfs
dev/hda2         13210   38912     f          w95 Extd (lba)
dev/hda5         13210   25938      7         hpfs/ntfs
dev/hda 6        25935    38906     7         hpfs/ntfs
dev/hda7         38907    38913      b        w95 fat32

dev/hdb  80gb

dev/hdb1*       1      9541       83    Linux
dev/hdb2         9542    9729     5   ext.
dev/hdb5         9542    9729      82   linux swap/solaris 



this is the end of file, but I do have cdrw, dvdr,usb external disk.floppy.

hope this helps.

G.

---

### Post by gilgongo on 2007-05-13
> **thatswho2 said:**
> 

I do have an ethernet hub,(Netgear EN104) which is connected, but only to an unused old server (NT4). 

That's not what I mean. The best (easiest) way of connecting a PC to the internet is by getting a DSL or cable router (depending on what your net connection is), connect that to your ISP, and then simply plug yor PC into the router using an Ethernet cable. Linux will almost certainly simply configure itself to connect. 

Trying to connect via a USB modem to your ISP is going to be painful, slow and unreliable. Don't do it.

---

### Post by Happy_Man on 2007-05-13
sudo fdisk -l doesn't show cd drives, instead could you please post 
```
cat /etc/fstab
```?

---

### Post by mark853 on 2007-05-16
> **gilgongo said:**
> That's not what I mean. The best (easiest) way of connecting a PC to the internet is by getting a DSL or cable router (depending on what your net connection is), connect that to your ISP, and then simply plug yor PC into the router using an Ethernet cable. Linux will almost certainly simply configure itself to connect. 

Trying to connect via a USB modem to your ISP is going to be painful, slow and unreliable. Don't do it.

Connecting via broadband may not be an option for some people, the only way to get updates etc is with the dialup modem. Hopefully Ubuntu will install the driver if the modem is hooked up during install and and turned on if its an external modem. Then the best hope I believe is to use the Gnome PPP utility that may or may not be in the default install. I will check this out myself asap with a winmodem and a US Robotics external modem and post what I can.

---

### Post by gilgongo on 2007-05-17
The OP said he's using an Alcatel Speedtouch modem - that means he has broadband. The word "modem" is misleading, I admit, but he ain't on a dial-up.

---

### Post by StevenHarper on 2007-05-20
I have made a Debian Package to manage USB ADSL Modems and there Configuration

It Supports Speedtouch USB 330 Modems

My Page it at

[https://launchpad.net/usb-adsl-modem-manager]("https://launchpad.net/usb-adsl-modem-manager")

You can download the package at [http://www.squeezedonkey.com/svn/linux/trunk/releases/]("http://www.squeezedonkey.com/svn/linux/trunk/releases/")

And read about it at
[http://www.squeezedonkey.com/wiki/li...itle=Main_Page]("http://www.squeezedonkey.com/wiki/li...itle=Main_Page")

Hope it makes your life easier

Steve

---


---
title: "The Most Basic Stuff you'll learn to need"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Count Doofus on 2007-09-03
Are You New to Linux ? If so  here is a  log of my Journey into a new world of computing. I assume nothing is known at all, i,e, I don't leave out steps that were necessary for me to accomplish a task.

So Far I have found that it is very difficult to get started in Linux because so many programmers skip steps that will make or break your efforts. I will post all discoveries as I dive into this new and undiscovered world.
 I have tried to get started in linux several times in the last ten years but have always failed because people don't get that I don't know a thing about linux at all. I.e. I don't know how to link include directories when installing from source nor do i know where they are at and so on and so forth. The Big problem I see is that people forget where they came from i.e. no knowlege of or about anything. If you discover that  I left something out fell free to comment or send me an email. I really wnat to learn this stuff and document the places where I ran into trouble so that others may learn with greater ease

---

### Post by sumguy231 on 2007-09-03
> but have always failed because people don't get that I don't know a thing about linux at all.
It just takes patience. I think the only person who ever went into Linux knowing exactly what to do with it is Linus Torvalds himself. ;) I had no idea what to do when I started either. I find the Ubuntu community as a whole to be quite helpful to new users, myself. But that doesn't apply to every single person in the community. Your mileage may vary.

---

### Post by Count Doofus on 2007-10-25
First Triumph !!! 
I got My trendnet TEW-421PC Wireless card up and running. It aint pretty but it works al least for this chipset. It may work for others as well because the python script in one of the steps was not specifically written for this card but for a whole range of broadcom wireless chipsets. If the Ndiswrapper fails there is still the firmware option that can be used which also worked on my other laprop at work. I got my trendnet 421pc card running using a broadcom 43xx python script. Here's is what i did to get it going on my machine. No steps were left out and names have been kept the same to punish the innocent.

Use Synaptics package manager to download the latest Kernel

You can check the kernel revision number with the statement

Bla@Bla-Bla:~$ uname -a

Let's make sure the network manager is up o date

Bla@Bla-Bla:~$ sudo apt-get install network-manager-gnome

Reading package lists... Done
Building dependency tree
Reading state information... Done
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

lets see if you device was--11ab:1faa (rev 03) Capabilities: <access denied> -- like mine was


Bla@Bla-Bla:~$ lspci -n

00:00.0 0600: 1039:0650 (rev 11)
00:01.0 0604: 1039:0001
00:02.0 0601: 1039:0962 (rev 04)
00:02.1 0c05: 1039:0016
00:02.3 0c00: 1039:7007
00:02.5 0101: 1039:5513
00:02.6 0703: 1039:7013 (rev a0)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:0f.0 0200: 14e4:4401 (rev 01)
00:10.0 0607: 1524:1411 (rev 01)
00:10.1 0501: 1524:0510
01:00.0 0300: 1039:6325
02:00.0 0200: 11ab:1faa (rev 03) Capabilities: <access denied>

11ab = Vendor ID
1faa = Device ID

Bla@Bla-Bla:~$ sudo lspci -s 02:0.0 -v

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
Flags: 66MHz, medium devsel, IRQ 16
Memory at 24000000 (32-bit, non-prefetchable) [disabled] [size=64K]
Memory at 24010000 (32-bit, non-prefetchable) [disabled] [size=64K]
Capabilities: [40] Power Management version 2

Open up the modules files and add the 88w8335 to the end of the list

sudo gedit /etc/modules

Bla@-Bla-Bla:~$ sudo lshw -C network

*-network
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: f
bus info: pci@00:0f.0
logical name: eth0
version: 01
serial: 00:0c:6e:99:5f:d2
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.108 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: iomemory:dc000000-dc001fff irq:17
*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 1
bus info: pci@02:00.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: latency=0
resources: iomemory:24000000-2400ffff iomemory:24010000-2401ffff irq:16

Download this package, extract and install it

Bla@Bla-Bla:~$ wget [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)

--21:20:50-- [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)
=> `bcm43xx-0.3.2-internet.tar.gz'
Resolving blakecmartin.googlepages.com... 72.14.203.118
Connecting to blakecmartin.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19,375 (19K) [application/octet-stream]

100%[=======================>] 19,375 --.--K/s

21:20:51 (131.90 KB/s) - `bcm43xx-0.3.2-internet.tar.gz' saved [19375/19375]


Bla@Bla-Bla:~$ tar xvf bcm43xx-*.tar.gz
bcm43xx-0.3.2-internet/
bcm43xx-0.3.2-internet/LICENSE
bcm43xx-0.3.2-internet/installer.py
bcm43xx-0.3.2-internet/S05firmware-init-script
bcm43xx-0.3.2-internet/wcm.sh
bcm43xx-0.3.2-internet/bcm43xx.sh
bcm43xx-0.3.2-internet/bcm43xx-ndiswrapper.sh
bcm43xx-0.3.2-internet/wicd-tray.desktop
bcm43xx-0.3.2-internet/stats-logger
bcm43xx-0.3.2-internet/LICENSE-BROADCOM
bcm43xx-0.3.2-internet/READMEs/
bcm43xx-0.3.2-internet/READMEs/README-wcm-wicd
bcm43xx-0.3.2-internet/READMEs/README-installer
bcm43xx-0.3.2-internet/READMEs/README-wcm-wifi-radar
bcm43xx-0.3.2-internet/READMEs/GPLv2
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx-ndiswrapper
bcm43xx-0.3.2-internet/READMEs/README-bcm43xx
bcm43xx-0.3.2-internet/READMEs/CHANGELOG
bcm43xx-0.3.2-internet/README

Bla@Bla-Bla:~$ cd bcm43xx-*

Bla@Bla-Bla:~/bcm43xx-0.3.2-internet$ ./installer.py

./wcm.sh wifi-radar
gksudo './bcm43xx-ndiswrapper.sh'

Bla@Bla-Bla:~/bcm43xx-0.3.2-internet$


cd ~
wget [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)
wget [http://blakecmartin.googlepages.com/...offline.tar.gz](http://blakecmartin.googlepages.com/...offline.tar.gz)
tar xvf bcm43xx-*.tar.gz
cd bcm43xx-*
./installer.py


See if your wireless card is now listed in the system/administration/network Devices-Network Tools in the Device pulldown menu and go configure your wep password and network id



!!! TADA !!!    :guitar:

---

### Post by endlessurf on 2007-11-03
> wget [http://blakecmartin.googlepages.com/...nternet.tar.gz](http://blakecmartin.googlepages.com/...nternet.tar.gz)

is this link dead?  I was following your steps and i get a 404 error

---

### Post by twisted_steel on 2007-11-03
> **endlessurf said:**
> is this link dead?  I was following your steps and i get a 404 error

It looks like the links were truncated, but you can find them on this other page:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by aonegodman on 2007-12-19
):P   Like the looks and title of this thread/post.

I'm new to Linux also about 10 days now. I should be looking for a job instead of so much time here on this forum but it's great.

Is there such a thing as a favorite threads bookmark feature in the control panel for forum users?

One of the most difficult things I find to grasp about Linux for new users is the command syntax structure required to DO things in Ubuntu/Linux. There are times when you just need to move a file from one location to another. Having to "sudo" everything in order to do what was simply click and drag under Windows.

Is there a tutorial on the command line structure along with examples of common uses for Linux? Can someone share a link?

Right now I'm wanting to unarc a file and place it in a subfolder of a program to run as follows:

I dblclick on a arc/zip file on my Desktop.

Archive Manager opens and grabs the arc showing the file in the arc.

I choose extract.

It asks me where.

I tree down to program folder where I want the file to go.

(/usr/share/Hydrogen/data/Demo_songs )

Click on Extract.

I get the error message  "access denied"  ](*,)

Anyone?  Thanks.

---

### Post by hyper_ch on 2007-12-19
> **aonegodman said:**
> One of the most difficult things I find to grasp about Linux for new users is the command syntax structure required to DO things in Ubuntu/Linux. There are times when you just need to move a file from one location to another. Having to "sudo" everything in order to do what was simply click and drag under Windows.
If you need sudo for that then you are trying to copy a file to a location where you probably shouldn't copy anything ;)

> **aonegodman said:**
> 
Is there a tutorial on the command line structure along with examples of common uses for Linux? Can someone share a link?
[http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf](http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf)
[http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf](http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf)
[http://www.digilife.be/quickreferences/QRC/Bash%20Quick%20Reference.pdf](http://www.digilife.be/quickreferences/QRC/Bash%20Quick%20Reference.pdf)

> **aonegodman said:**
> 
I tree down to program folder where I want the file to go.

(/usr/share/Hydrogen/data/Demo_songs )

Click on Extract.

I get the error message  "access denied"  ](*,)

Well, you'll have to understand the linux filesystem hierarchy and how the linux security system works.
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)
[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)
[http://www.linuxsecurity.com/content/view/118181/171/](http://www.linuxsecurity.com/content/view/118181/171/)

---

### Post by aonegodman on 2007-12-19
Thank you Hyper_ch for your response and offerings to help me along the path.

Much appreciated. :)

I had misquoted the error message feedback above in my initial request. It should have said:

tar: base.h2song: Cannot open: Permission denied
tar: Error exit delayed from previous errors

I tried changing permission to the folder by using the suggested command:

sudo chown <USERNAME> /

Command seemed to execute ok in Terminal, however upon retry at moving file there I got the same error message again.

This file is simply a demo song file for the program to run and I am simply trying to place it in the same folder with other same type files used by the program. I know this where it belongs, it's simply a matter of getting Linux to let me put it there.

Thanks to all.

---

### Post by hyper_ch on 2007-12-19
where do you get instructions from that a folder in /usr/... should be chowned to your user?

---

### Post by aonegodman on 2007-12-19
WoW  *Hyper_ch* I just opened the first link you sent me for the

**THE ONE PAGE *LINUX* MANUAL**

Now this should be included in every destro of Linux and be one of the first things to pop in a tutorial for newbies after install. Thanks again so much. \\:D/

Put this one in the top 10 list of must haves.

---

### Post by hyper_ch on 2007-12-19
You can press this button [IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG] to thank me ;)

Some commands are not geared towards Ubuntu (the whole rpm section and the use of su) but it gives an overview...

---

### Post by aonegodman on 2007-12-19
> **hyper_ch said:**
> where do you get instructions from that a folder in /usr/... should be chowned to your user?

I can't tell you that  :lolflag:

No really, I was looking at another post here and this advice was being given in order to gain permission to access the /usr/ files for similar reasons. I tried to relocate it so I could point it out before reply but no luck.

Thought I'd give it try. It didn't work as I already stated.

Should I, could I undo it?  If so how? Thanks.

---

### Post by tad1073 on 2007-12-19
> **aonegodman said:**
> Thank you Hyper_ch for your response and offerings to help me along the path.

Much appreciated. :)

I had misquoted the error message feedback above in my initial request. It should have said:

tar: base.h2song: Cannot open: Permission denied
tar: Error exit delayed from previous errors

I tried changing permission to the folder by using the suggested command:

sudo chown <USERNAME> /

Command seemed to execute ok in Terminal, however upon retry at moving file there I got the same error message again.

This file is simply a demo song file for the program to run and I am simply trying to place it in the same folder with other same type files used by the program. I know this where it belongs, it's simply a matter of getting Linux to let me put it there.

Thanks to all.

have you tried alt+F2 then gksudo nautilus
after that go to where the file is located, cut it then paste it in the file you want to put it into.

---

### Post by aonegodman on 2007-12-19
I extracted the file to my    /home/user/temp   folder without a problem.

So thought I'd try to simply move the file into the desired location. 

$ mv base.h2song /usr/share/hydrogen/data/demo_songs
mv:

cannot move `base.h2song' to `/usr/share/hydrogen/data/demo_songs/base.h2song': Permission denied

That's what I got back.

Obviously I don't have permission to execute commands on the root disk system files.

This is my computer, my desktop and I am the Administrator(in Windows language)

I'm not new to computers, come from a MS/DOS up through all versions of Windows to include the XP, but I am new to Linux O/S. I guess I'm spoiled always having complete access to all functions on my computer.

Yes even the hidden system files have always been set to view and I am comfortable with the responsibility.

In gamers language - I want **GODMODE** on this machine. Please. [-o<

---

### Post by g2g591 on 2007-12-19
Absolutly DO NOT CHOWN ANY THING, thats a great way to screw up your machine (if you do sudo chown -R user / you will make your machine unbootable). if you really are absolutely sure you NEED to exctract them there (and not setup another folder and let it be rw for all others) use sudo commandhere . But /usr/share is not a good place to put anything, thats like puting stuff in C:/WINDOWS/. You just don't do it.

---

### Post by aonegodman on 2007-12-20
I understand what you are saying. But upon examination of the file system under /usr/share -

This is the same as "Program Files" under Windows. This is where the Applications are kept.

There is a Program folder under "share" called "Hydrogen"

"Hydrogen" has a "data" sub-folder under it which contain ".flac" files(like text files)

I want to take a "like" text file and place in that folder so I can run or "play" it in the parent program.

I can't get system to allow me to place it there.

I appreciate everyones philosophy on why you may not want to DO certain things, but can anyone tell me how do this ONE thing?   ](*,)

---

### Post by hyper_ch on 2007-12-20
the <i>/usr</i> folder is a... hmmm... let's say "high" privilege one. What is in there can be run by users. So if you could just copy malicious code into it, users could execute it. That's why it's owned by root and that's where the barrier is. By default you are not root (and you should not login as root except when you know what you are doing). So, by not allowing you just to put stuff in there, you'll be warned that what you may want to do can have a huge impact. It's some kind of warning for you to not trust everything you're told do.

However if you assume temporary root rights, you can copy into that folder. Read more about that here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically you do this:
```

sudo cp /path/from/file /usr/share/....

```

And you will be prompted to enter your user password (assuming you try to do that with the first user created on that system, as only that one has the right to acquire temporary root privileges).

---

### Post by aonegodman on 2007-12-20
=D>  You can't see me, but I am prostrating myself before you great one - -   \\O//

Made my day for sure  \\:D/

---


---
title: "partioning.."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-08-06
I have Some space on my hdd which is not partitioned so how do i install Ubuntu there ?
I tried installing that once but i was not able to see that un partitioned space.. thanks...

---

### Post by Ek0nomik on 2007-08-06
How is your hard disk laid out with partitions?

You have Windows on it currently I presume?

If you want to install Ubuntu you need an EXT3 partition and a Swap partition.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Tomshaq on 2007-08-06
The live cd should take care of the partitioning for you. Of course, if you want to do it manually, the gparted live cd comes in handy. 

You will need to partition a root(/) a swap and maybe a home partition (based on preference). If the partitioner in the livecd doesn't recognize your space, then I would recommend using a gparted live cd.

---

### Post by dhani99 on 2007-08-06
I do have partition magic !! 
SO I want to know in which format i turn that part into and then I'll be able to see that in installation !! 

which one is better ?

---

### Post by Ek0nomik on 2007-08-06
As I already mentioned in my previous post, you will need an EXT3 partition **and** a Swap partition.  You need both, not just one.

Also, partitioning them isn't the only step.  You need to install the actual operating system as well in order to "see" it.

I would suggest downloadind and burning the Live CD and installing Ubuntu that way.

You boot into the CD, and you can play around with it and test it out.  Then, when you are ready to install, just click the Install button on the desktop.

---

### Post by dhani99 on 2007-08-06
> **Ek0nomik said:**
> As I already mentioned in my previous post, you will need an EXT3 partition **and** a Swap partition.  You need both, not just one.

Also, partitioning them isn't the only step.  You need to install the actual operating system as well in order to "see" it.

I would suggest downloadind and burning the Live CD and installing Ubuntu that way.

You boot into the CD, and you can play around with it and test it out.  Then, when you are ready to install, just click the Install button on the desktop.

I did that and probably it did not recognize un partitioned space...

---

### Post by Ek0nomik on 2007-08-06
> **dhani99 said:**
> I did that and probably it did not recognize un partitioned space...

GParted didn't recognize your unpartitioned space?  Hm, weird.

How much unpartitioned space do you have?  Also, how many partitions do you have on the hard disk?

I suppose if GParted won't do the job then you could just format using Partition Magic and then boot into Ubuntu and install without messing around with partitions.

---

### Post by dhani99 on 2007-08-06
I mean Ubuntu didn't recognize it.. sorry 4 dat...

---

### Post by dhani99 on 2007-08-06
I check that again !! so before i check that  !! 
wat do u think wud i b able to see that space !!

---

### Post by Ek0nomik on 2007-08-06
> **dhani99 said:**
> I check that again !! so before i check that  !! 
wat do u think wud i b able to see that space !!

Alright, if you boot into the Ubuntu Live CD, you should be able to load GParted, or you can just click Install and GParted is built into the install process.

It *should* show you all the space on your entire hard disk.  I guess I am not really sure what you are trying to accomplish anymore?

Again, can you tell me how your hard disk is laid out with partitions?

---

### Post by dhani99 on 2007-08-06
un partitioned space is about 5 Gb.. and Full is abt.. 15 Gb...

---

### Post by bren on 2007-08-06
and a little more info for the new person

gparted = Gnome Partition Editor = System --> Adminstration ---> Gnome Partition Editor when starting from the main screen of the Ubuntu Live CD

bren

---

### Post by dhani99 on 2007-08-06
> **bren said:**
> and a little more info for the new person

gparted = Gnome Partition Editor = System --> Adminstration ---> Gnome Partition Editor when starting from the main screen of the Ubuntu Live CD

bren

thanks.........................................................

---

### Post by dhani99 on 2007-08-06
un partitioned space is about 5 Gb.. and Full is abt.. 15 Gb...

---

### Post by dhani99 on 2007-08-06
NO DEVICE DETECTED DURING INSTALLATION>>> 
wat do i do ??

---

### Post by bren on 2007-08-06
its a little easier to help if you provide some info about what you were doing when you got this command and which stage you were at.....

assuming you have 
- downloaded a Ubuntu ISO file
- burned it to CD
- checked it as recommended (see Ubuntu documentation)
- changed your BIOS to boot from CD before HD
- booted from the CD and have a nice Ubuntu desktop (runs slowly from CD) and has INSTALL button on the desktop

[ if you have not done these steps post back and we can help you with any you need help on]

- then you clicked on install and it failed for some reason.

If this is right please do the following

1) 

- Applications ---> Accessories ---->Terminal

type the following command into the Terminal window
> 
sudo fdisk -l
and post results here.

2) 

give summary of your hardware
command > lshw -short will tell you lots if you are not sure (ijn terminal window)

back tomorrow but am sure someone else will help in the meantime if needed

bren

---

### Post by dhani99 on 2007-08-06
now i'm stuck in BIOS ... actually I had disabled HDD to boot up through CD ROM so .. probably that was the reason that system was not able to find DEVICE, anyway i try to rescue my SELF..... :)

---

### Post by bodhi.zazen on 2007-08-06
LOL

Plug the hard drive back in ...

Set your BIOS to boot from CD, then HD ...

Then follow this guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

IMO you should NOT use partition magic as, although it often works just fine, it sometimes fails ...

Use gparted on the Ubuntu CD ...

---

### Post by dhani99 on 2007-08-06
> LOL

Plug the hard drive back in ...

Set your BIOS to boot from CD, then HD ...

Then follow this guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

IMO you should NOT use partition magic as, although it often works just fine, it sometimes fails ...

Use gparted on the Ubuntu CD ... 

thanks.... 

So everything is  okay now...

So the hard disk is Formatted and it's about 15.3 GB and I also want to have WIndows so Suggestion.....plz

---

### Post by bodhi.zazen on 2007-08-07
not sure what the question is ...

boot the live cd and install 

where exactly are your having questions ?

---

### Post by dhani99 on 2007-08-07
Oaky ... 

SO HDD is Empty.. No partition nothin...

 I want to dual boot (ubuntu and XP ) and HDD capacity 15.3 GIB, and the question is can u help me for partioning that... ( like what Should i set space for XP and ubuntu...) and as i said HDD is empty, it's bit hard to partition on ubuntu Bcaz I don't know abot mount point and those things ....

---

### Post by bodhi.zazen on 2007-08-07
OK, so you have a clean disk, 15 Gb, no OS ? And you want to install windows and Ubuntu ?

OK, but 15 Gb is tight for two OS ...

First partition the drive.

Make a primary partition for windows, size = 9 Gb

Make a primary partition for Ubuntu = 5 Gb

Make a  primary partition for Linux Swap = 1 Gb

Boot the Window CD, install windows to the window 9 Gb partiion

Boot Ubuntu, install to the 5 Gb partition.

Follow the guide I gave you ...

See here for partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by bren on 2007-08-07
a computer which has such a small HD is likely to be quite old.... and low mem and processor.

maybe ubuntu is not best option for you...

that is why i asked you to run 

lshw -short and post results....

but you ignore til now....

bren

---

### Post by dhani99 on 2007-08-07
ubuntu@ubuntu:~$ lshw -short
WARNING: you should run this program as super-user.
H/W path             Device      Class          Description
===========================================================
                                 system         Computer
/0                               bus            Motherboard
/0/0                             memory         254MB System memory
/0/1                             processor      Pentium III (Coppermine)
/0/1/0                           memory         32KB L1 cache
/0/1/1                           memory         256KB L2 cache
/0/100                           bridge         82810E DC-133 GMCH [Graphics Mem
/0/100/1                         display        82810E DC-133 CGC [Chipset Graph
/0/100/1e                        bridge         82801AA PCI Bridge
/0/100/1e/b                      communication  536EP Data Fax Modem
/0/100/1e/c          eth0        network        3c905C-TX/TX-M [Tornado]
/0/100/1f                        bridge         82801AA ISA Bridge (LPC)
/0/100/1f.1          scsi0       storage        82801AA IDE
/0/100/1f.1/0.0.0    /dev/cdrom  disk           CD-ROM SC-148C
/0/100/1f.1/0.0.0/0  /dev/cdrom  disk           
/0/100/1f.1/0.1.0    /dev/scd1   disk           CD-RW GCE-8525B
/0/100/1f.1/0.1.0/0  /dev/scd1   disk           
/0/100/1f.2                      bus            82801AA USB
/0/100/1f.2/1        usb1        bus            UHCI Host Controller
/0/100/1f.3                      bus            82801AA SMBus
/0/100/1f.5                      multimedia     82801AA AC'97 Audio
ubuntu@ubuntu:~$

---

### Post by dhani99 on 2007-08-07
> **bodhi.zazen said:**
> OK, so you have a clean disk, 15 Gb, no OS ? And you want to install windows and Ubuntu ?

OK, but 15 Gb is tight for two OS ...

First partition the drive.

Make a primary partition for windows, size = 9 Gb

Make a primary partition for Ubuntu = 5 Gb

Make a  primary partition for Linux Swap = 1 Gb

Boot the Window CD, install windows to the window 9 Gb partiion

Boot Ubuntu, install to the 5 Gb partition.

Follow the guide I gave you ...

See here for partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

DO i install WIndows First ?
So say I have made 9 gb partition for WIndows From WIN Installation and 6 GIB un partitioned left... 
so after Installing Windows when i try to install UBuntu Will i be able o see that 6 GIB un partitioned space... and say i do see that space and i make 5 gb partition and then 1 GIb Swap.. but what abt th 5 GIB which format i use to Create ?

---

### Post by steve.horsley on 2007-08-07
Once you have the installer CD booted and able to see the hard disk, I suggest that you choose the option to "use the largest contigutou free space". This avoids any need for you to manually partition that space - the installer will create the two partitions it needs, and format them appropriately.

---

### Post by dhani99 on 2007-08-07
bu i want to install Windows as well................

---

### Post by bodhi.zazen on 2007-08-07
I would boot the Ubuntu CD and use gparted to make the partitions.

Then install windows.

Then install ubuntu.

---

### Post by dhani99 on 2007-08-09
but now I don't want to install and get that space allocated to Linux ............... how !!!!!

---

### Post by dhani99 on 2007-08-09
and is this com is good enough to work with ubuntu !????

system Computer
/0 bus Motherboard
/0/0 memory 254MB System memory
/0/1 processor Pentium III (Coppermine)
/0/1/0 memory 32KB L1 cache
/0/1/1 memory 256KB L2 cache
/0/100 bridge 82810E DC-133 GMCH [Graphics Mem
/0/100/1 display 82810E DC-133 CGC [Chipset Graph
/0/100/1e bridge 82801AA PCI Bridge
/0/100/1e/b communication 536EP Data Fax Modem
/0/100/1e/c eth0 network 3c905C-TX/TX-M [Tornado]
/0/100/1f bridge 82801AA ISA Bridge (LPC)
/0/100/1f.1 scsi0 storage 82801AA IDE
/0/100/1f.1/0.0.0 /dev/cdrom disk CD-ROM SC-148C
/0/100/1f.1/0.0.0/0 /dev/cdrom disk
/0/100/1f.1/0.1.0 /dev/scd1 disk CD-RW GCE-8525B
/0/100/1f.1/0.1.0/0 /dev/scd1 disk
/0/100/1f.2 bus 82801AA USB
/0/100/1f.2/1 usb1 bus UHCI Host Controller
/0/100/1f.3 bus 82801AA SMBus
/0/100/1f.5 multimedia 82801AA AC'97 Audio

and how much space does ubuntu use ??
it has used 3.6 Gb ?? okay ??
i don't have too many application

---

### Post by dhani99 on 2007-08-09
bump

---

### Post by bren on 2007-08-09
256MB memory is quoted as required therefore you are right on the border line (check the wiki)

for lower memory it is recommended to use the "alternate" non-graphical install cd.

so do as bodhi says in post #28.
try first with the cd you have
if you have problems use the "alternate" CD

don't worry about the fact that you are using gparted to create the partitions .... windows will still install on the 10GB one

bren

---

### Post by NickXxRitzXxVamp on 2007-08-25
ugh I'm new at Ubuntu soo I have goten XP and Vista Dual booted fine on my computer however partiton magic starts step one of creating a new partition and says too many errors occured press any key to restart or something like that i know lots about computers but this ones driving me crazy :mad: can anyone help me?

---

### Post by NickXxRitzXxVamp on 2007-08-25
oh yeah and in gnome partiton editor it has locks next to all of the partitons and wont let me do anything to them and in the installer it only lets me use the full hard drive ? >.< helps please thanx in advance

---

### Post by bren on 2007-08-28
locks means that you have those partitions mounted and therefore you cannot manipulate them....

use gparted LIVE CD (free download and burn .iso)  or use umount command after boot from Ubuntu Live CD

i think there is some troubles when installing with VISTA and have seen previous recommendation to create partition for ubuntu within VISTA first

sorry dont know if this is still current or old rumour

bren

---

### Post by NickXxRitzXxVamp on 2007-08-28
I used gparted live cd and it didn't work. and yeah i made a partition for the ext3 partition but couldnt make a swap partiton.ok so i managed to not bother with my laptop because i have too many primary partitons already only because dell had to make a stupid primary partion only to not even need it bootable >.< so i installed it on my desktop the only thing I need is how to get the wireless internet working the adapter is a Proxim Orinco 802.11 g usb adapter and the light doesent come on so i know its not working so how do i set up wireless internet? a

---

### Post by bren on 2007-08-31
HI NICK

i dont have experience of your particular wireless card .... but the search function is an amazing tool.....

have a look at post #20 in this thread

[http://ubuntuforums.org/showthread.php?t=527488&highlight=Proxim+Orinco](http://ubuntuforums.org/showthread.php?t=527488&highlight=Proxim+Orinco)

bren

---

### Post by Paul133 on 2007-08-31
Ubuntu worked fine for me. I didn't even defrag Vista first. :D

---


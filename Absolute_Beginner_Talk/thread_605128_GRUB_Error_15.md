---
title: "GRUB Error 15"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by AstroBomber on 2007-11-06
I 've been trying for a few days now to get Ubuntu to run on my system without the disk. So far, I've gotten a wide variety of Errors, Error 15 being the most recent. I've partitioned, repartitioned, installed, reinstalled, and I have run out of things to try. 

I am running a single hard drive, and don't care about dual booting. If anyone is going to tell me to repartition, tell me *exactly* what I need to do, because repartitioning has not worked thus far. I am an inch away from giving up.

---

### Post by tlages on 2007-11-06
Make sure you have all your drivers handy before doing this.
Alright
Wipe your hard drive completely
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Create one partition, the root partition, with ext3 and name it /.
Create a 200-2000 MegaByte partition and format it as swap.

Install.

---

### Post by tlages on 2007-11-06
Nothing.
There is no text in this post.

---

### Post by AstroBomber on 2007-11-06
> **tlages said:**
> Make sure you have all your drivers handy before doing this.


By drivers do you mean absolutely everything? Because I have no peripherals except keyboard and mouse. Would I have to get drivers for the CD drives?

---

### Post by Pumalite on 2007-11-06
Post your specs.

---

### Post by AstroBomber on 2007-11-06
Stats are as follows:

Compaq Presario
Disk: Quantum Fireball lct2040
CD Roms: Compaq DVD Rom DVD-116
Phillips CDD4801 CD-R/RW
Network Adapter: Realtek RTL8139 Family PCI Fast Ethernet NIC
Processor: AMD Duron
Sound: SoundMAX Integrated Digital Audio

---

### Post by oldos2er on 2007-11-06
I see you have two cdrom drives; be sure your hard disk (if IDE) is set as primary master in your bios.

---

### Post by Pumalite on 2007-11-06
You left out the most important: graphics and memory.

---

### Post by Duck2006 on 2007-11-06
From the live cd in the terminal type

sudo fdisk -l

and post the output

---

### Post by Pumalite on 2007-11-06
While you are at it post also:

cat /boot/grub/menu.lst

---

### Post by AstroBomber on 2007-11-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4729    37985661   83  Linux
/dev/hdb2            4730        4866     1100452+   5  Extended
/dev/hdb5            4730        4866     1100421   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory


As for the memory and graphics card, I'm unsmart and forgot to write that bit down when I recorded that information. Is there any way to check it with the Live CD in?

---

### Post by Pumalite on 2007-11-07
If you are running Windows, you can go to 'Computer' and right click (I think) and know everything about your system. Is very important to know your graphics and memory.

---

### Post by AstroBomber on 2007-11-07
I'm not using Windows though, I'm not even sure if I can use Windows anymore, considering I get the GRUB Error in question when I boot up.

---

### Post by AstroBomber on 2007-11-07
This is what I got off of Wikipedia (which does sound vaguely familiar):

# 700-1200MHz AMD Duron/Athlon Processor
# 63-384MB PC133 SDRAM
# 8-64MB S3 or nVidia Graphics Controller

Although I think I updated the RAM at one point or another. It should have at least 512MB of RAM. 

Is there any way I can figure out for sure? Through the CMOS or something?

---

### Post by Pumalite on 2007-11-07
Boot your Live CD and from Terminal post the output of:

free -m

---

### Post by AstroBomber on 2007-11-07
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           368        364          4          0         15        161
-/+ buffers/cache:        187        180
Swap:            0          0          0

I hope you can read that okay.

---

### Post by Pumalite on 2007-11-07
You are at the limit. Maybe Xubuntu Alternate CD would be better:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by AstroBomber on 2007-11-07
What limit am I at? Memory? What's different about Xubuntu?

---

### Post by Pumalite on 2007-11-07
Lighter Desktop. Uses less memory. Runs faster in you system. All the programs available in Ubuntu.

---

### Post by jaybombalous on 2007-11-07
grub error 15 means there is something generically wrong with that partition because it won't boot, for whatever reason.


If u have installed an OS u can try gparted to see if u can mount the partition and boot, then u know if its just a grub problem which u can fix with supergrub. If you can mount it with Gparted then u know its a problem with that partition and u will need to reinstall OS after deleting all the partitions and starting over.

---

### Post by jaybombalous on 2007-11-07
> **AstroBomber said:**
> ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           368        364          4          0         15        161
-/+ buffers/cache:        187        180
Swap:            0          0          0

I hope you can read that okay.


You have no swap??? and u have 4 mb free system memory out of 368mb. :( recommended to have at least 800mb swap partition.

---

### Post by AstroBomber on 2007-11-07
What does the swap do?

Btw, will the .iso for Xubuntu burn onto a DVD-R?

---

### Post by jaybombalous on 2007-11-07
a swap partition is used to hold data for programs like your memory does. When your memory gets full then u start swapping out data to the swap partition on the HD to free up memory space.

If u run out of memory with no swap or cache/buffers u will crash the PC.

Use gparted and make a swap partition.


Yes it will fit on a DVD-R

---

### Post by AstroBomber on 2007-11-07
Well, I tried loading Xubuntu, and all I'm getting right now is a black screen with a bunch of errors on it (now I can say I've had a computer say "huh" to me)

---

### Post by jaybombalous on 2007-11-08
something is not right, either its a bad cd or u have other hardware problems.

---

### Post by AstroBomber on 2007-11-09
> **jaybombalous said:**
> ....and u will need to reinstall OS after deleting all the partitions and starting over.

I've deleted partitions and restarted 20-30 times already, and it's still not booting.

---

### Post by AstroBomber on 2007-11-09
> **jaybombalous said:**
> something is not right, either its a bad cd or u have other hardware problems.

I really hope it's the CD, because I'm going to try to make new ones and see how that works. Will it matter if I make the CD in Windows or Ubuntu?

---

### Post by Pumalite on 2007-11-09
No.

---

### Post by Pumalite on 2007-11-09
Clean the lens in your burner, try the CD in a different computer, change your burner if necessary.

---

### Post by AstroBomber on 2007-11-10
I managed to get Xubuntu installed. The problem is I'm still getting an error (GRUB Error 17)

---

### Post by bharris25 on 2007-11-10
What size hard drive do you have?

---

### Post by AstroBomber on 2007-11-10
I believe it's 40GB

---

### Post by Pumalite on 2007-11-10
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Pumalite on 2007-11-10
Boot your Live CD, mount drives/partitions and post from Terminal:

sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by AstroBomber on 2007-11-10
Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    38539934    19269936   83  Linux
/dev/hdb2        74316690    78172289     1927800    5  Extended
/dev/hdb3   *    38539935    74316689    17888377+  83  Linux
/dev/hdb5        75971448    78172289     1100421   82  Linux swap / Solaris
/dev/hdb6        74316816    75971384      827284+  82  Linux swap / Solaris

Partition table entries are not in disk order


As for the second thing you asked me to post (assuming I typed it in correctly):

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by Pumalite on 2007-11-10
You didn't your partition, that's why you couldn't get menu.lst:

Get a Knopix Live CD(it boots your drives/partitions automatically at boot):
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by AstroBomber on 2007-11-10
What option do I use to download Knoppix? There's too many options and I have no idea which one to use.

---

### Post by Pumalite on 2007-11-10
ecn.purdue.edu

Or torrent: Download via BitTorrent: [http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)

---

### Post by Frak on 2007-11-10
> **Pumalite said:**
> You didn't your partition, that's why you couldn't get menu.lst:

Get a Knopix Live CD(it boots your drives/partitions automatically at boot):
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Go for [GParted]("http://gparted-livecd.tuxfamily.org/") instead.

---

### Post by AstroBomber on 2007-11-10
So, I assume once this is finished downloading, I burn the disk image to a CD and run it from startup like I do the Live CD?

---

### Post by Pumalite on 2007-11-10
Yes. And then, boot from it and from the Terminal post the commands I gave you. For cat..etc you have to put the path of the partition that contains Ubuntu.

---

### Post by AstroBomber on 2007-11-10
The partition that contains Ubuntu would be the boot drive?

---

### Post by Pumalite on 2007-11-10
Check your sudo fdisk -lu and you'll know.

---

### Post by AstroBomber on 2007-11-10
Both the /dev/hbd1 and /dev/hbd3 partitions say they are of the Linux system

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63    38539934    19269936   83  Linux
/dev/hdb2        74316690    78172289     1927800    5  Extended
/dev/hdb3   *    38539935    74316689    17888377+  83  Linux
/dev/hdb5        75971448    78172289     1100421   82  Linux swap / Solaris
/dev/hdb6        74316816    75971384      827284+  82  Linux swap / Solaris

Knoppix is 77% done downloading.

---

### Post by Frak on 2007-11-10
No support for the GParted disc? It was built to partition, and partition fast.

---

### Post by AstroBomber on 2007-11-10
I got Knoppix up and running, it was loading the desktop, and I right clicked and selected "run command.." and now all I'm getting is a black screen with a cursor. 

Do you have AIM or something Puma, or are you on IRC? It might make this easier

---

### Post by AstroBomber on 2007-11-10
> **Frak said:**
> No support for the GParted disc? It was built to partition, and partition fast.

GParted seems to be failing me time and time again. I'm not sure what the problem is, but I believe it has something to do with partitioning, and I've been using GParted. Part of the problem could be I don't know EXACTLY what I should be doing in terms of partitioning.

---

### Post by Frak on 2007-11-10
> **AstroBomber said:**
> I got Knoppix up and running, it was loading the desktop, and I right clicked and selected "run command.." and now all I'm getting is a black screen with a cursor. 

Do you have AIM or something Puma, or are you on IRC? It might make this easier
Welcome to the reason why people say Linux is so powerful. The Terminal.

As for GParted, if you don't know what to do with GParted, you'll have a VERY difficult time with Knoppix.

---

### Post by AstroBomber on 2007-11-10
> **Frak said:**
> Welcome to the reason why people say Linux is so powerful. The Terminal.

As for GParted, if you don't know what to do with GParted, you'll have a VERY difficult time with Knoppix.

Do you have any suggestions for what I should do with GParted?

---

### Post by Frak on 2007-11-10
> **AstroBomber said:**
> Do you have any suggestions for what I should do with GParted?
Sorry, read the problem wrong, then Knoppix is a good choice; I thought partitioning was the problem.

---

### Post by bulldog on 2007-11-10
What's bothering me is,why is your hdd called hdb instead of hda?

In my opinion is your cd-rom connected to the first primary ide and your hdd at the second one.
It should be the other way around,hdd always on the first primary IDE and the cd on the second or as a slave.

---

### Post by AstroBomber on 2007-11-10
> **bulldog said:**
> What's bothering me is,why is your hdd called hdb instead of hda?

Is that a huge problem? Or just a peculiarity?

---

### Post by AstroBomber on 2007-11-10
This is the cat command. I must have done something wrong again:

knoppix@Knoppix:~$ cat /dev/hdb3/boot/grub/menu.lst
cat: /dev/hdb3/boot/grub/menu.lst: Not a directory

---

### Post by bulldog on 2007-11-10
> **AstroBomber said:**
> This is the cat command. I must have done something wrong again:

knoppix@Knoppix:~$ cat /dev/hdb3/boot/grub/menu.lst
cat: /dev/hdb3/boot/grub/menu.lst: Not a directory

The command would be ```
cat /dev/hdb/boot/grub/menu.lst
```

About hdb,yes it **can** make a difference,but if you can install normally without any error from grub when it's installing,it shouldn't make a difference.
But I should,if I where you,open my case and switch both cables,just in case.
The problem is that grub will be installed on the first primary by default,which is in your case your cd-rom,but than again,you should have an error from grub.

---

### Post by AstroBomber on 2007-11-10
So, could that possibly be the cause of my problem? If it's trying to find the grub on the CD drive and doesn't find it, could that be the cause of my Error 17/18/21/everyothererror?

---

### Post by bulldog on 2007-11-10
It can ,won't say it is.
But simply switch the cables and try again.

I've seen more strange things happened :) this are computers you know.

---

### Post by AstroBomber on 2007-11-10
I've officially screwed my computer. It won't load anything past the Compaq splash screen. It won't even load the BIOS. I think maybe this is a sign I should give it up. *grumble grumble*

---

### Post by AstroBomber on 2007-11-10
I got it to work! Turns out bulldog was right, my hard drive was on a different point than it should have been. It was physically plugged into 1 when it should have been plugged into 0. Thank you guys!!

---

### Post by Frak on 2007-11-11
> **AstroBomber said:**
> I've officially screwed my computer. It won't load anything past the Compaq splash screen. It won't even load the BIOS. I think maybe this is a sign I should give it up. *grumble grumble*
For future information, the Compaq splash screen is an indication that your BIOS is loaded and the POST is being performed.

---

### Post by bobpur on 2007-11-11
I noticed in a recent post that you have PATA hard drives because of the "H" designation. Jumper placement as well as placement of the drive on the cable are both important.
I have an old Compaq presario 5WV252 that dualboots Win2K and Ubuntu "Gutsy." The hard drive issue is one that cost me a couple of six packs and most of my hair. It is fixed now and my little Presario runs great (after much modification.
I bet that if you check your jumpers on your drives and where they are plugged in on the cable, your problems will be cleared up. Been there, done that.

---


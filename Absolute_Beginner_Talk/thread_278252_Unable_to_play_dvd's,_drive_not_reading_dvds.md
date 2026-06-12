---
title: "Unable to play dvd's, drive not reading dvds?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by brian5588 on 2006-10-16
I have a thinkpad a31 with a cd-rw/dvd combo drive. i know that it can play dvds because I have played dvds under windows with no problem.

on thinkwiki.org, it says that the drive is located under /dev/hdc. I have installed all of the codecs and i have tried multiple media players, but none can seem to open up the drive or play the dvd no matter what i try. 

basically it seems like /dvd/ can't be opened, and there is nothing at /dev/hdc. i have no idea what is going on, i'm not sure what other information i could provide. any help would be greatly appreciated

---

### Post by jordanmthomas on 2006-10-16
Look in /media
is there anything related to your drive there?

---

### Post by brian5588 on 2006-10-16
nothing except cdrom, cdrom0, floppy, and floppy0 (i have no floppy drive). 

i also realized that when i put a dvd in the light on the drive only flashes a few times, it doesn't seem like it is really reading the dvd.

any thoughts? this is really frustrating.

---

### Post by Kateikyoushi on 2006-10-16
Could you post the output of this ?

```
cat /etc/fstab
```

---

### Post by brian5588 on 2006-10-16
brian@xubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
brian@xubuntu:~$

---

### Post by Kateikyoushi on 2006-10-16
Put a disc in the drive then copy the following command to terminal.

```
sudo mount /dev/hdc
```

Then check /media/cdrom0 to see the content of the disc

---

### Post by brian5588 on 2006-10-16
brian@xubuntu:~$ sudo mount /dev/hdc
Password:
mount: No medium found


this is with a working dvd in the drive. i know the drive works fine for data cds and other cds, its just dvds that it doesn't seem to read.

---

### Post by Kateikyoushi on 2006-10-16
What is the content of that disc ? Can you try it with a commercial DVD ?

---

### Post by Delkster on 2006-10-16
I take it that this is a video DVD, not a data one. If it's a commercial (protected) one, do you have libdvdcss? (It's needed for decrypting the contents of protected DVDs)

I don't think you're even supposed to mount video DVDs. You just play the video from them with a suitable video player. They just don't tend to be able to do that without the aforementioned library.

---

### Post by brian5588 on 2006-10-16
Yes, I am 100% sure i have all of the necessary codecs and I've tried with a cocktail of different media players.

I think the problem is that linux doesn't recognize my drive as a combo cd-rw /dvd drive, and it doesn't read the dvd at all.

Does anybody else have any other ideas? I might test out another distribution if this really is a dead end but i think there must be a way out.

---

### Post by brian5588 on 2006-10-16
The dvds im trying to play are commercial movie dvd's by the way, i have tried a bunch of them and none are being detected/played.

---

### Post by Kateikyoushi on 2006-10-16
I searched and found few similar cases. Seems so far that home made dvds have this problem.

> I am using Ubuntu as my operating system and I can not get it to recognize any dvd that was created in Windows.

The dvds in question play under Windows with no problem.

Under Ubuntu I can do the following:
Play standard commercial movies
Load and retrieve data from dvd-rw's
Play VCDs made by me.
Load and retrieve data from cd-rw's
[http://ubuntuforums.org/showthread.php?t=275056&page=2&highlight=no+medium+found]("http://ubuntuforums.org/showthread.php?t=275056&page=2&highlight=no+medium+found")

Final conclusion of that thread.

> It turns out that every disk made by Playo does not work in Ubuntu but works in WinXp. These disk are advertised (Staples) as 8x burn rate but only will burn at 4x. Yes they are you cheap media, at $5.00 for 50. One other point here is that 2 different machines were use to test out the disks, this in itself could be a factor in the problem.

Now the disks labeled Nexxtech play in both Ubuntu and WinXP. Again this was on 2 different machines. These disk were also cheap media at $8.00 for 50.

---

### Post by brian5588 on 2006-10-16
so basically there is no solution? i know for a fact this drive can handle dvds. and if there is a solution it won't be straightforward or easy. hmm i'm not sure what i'm going to do.

---

### Post by Bartender on 2006-10-16
brian -
Instead of dumping Ubuntu, how about trying a PCLinuxOS or Mepis or some other popular distro CD, run it Live on top of your Ubuntu install, and see if it can do what Ubuntu isn't?  This might help pin down whether it's hardware or OS or just some dopey setting that's getting missed.

---

### Post by lopzided on 2006-10-22
i am having the exact same problem...my drive reads cds fine, but it will not recognize a commercial movie DVD.  i have tried EVERYTHING.  i have googled, and spent hours in #ubuntu trying to diagnose the problem.

everything is installed right...all codecs, etc.  i am on a toshiba satellite 1850.  please help!

---

### Post by jordanmthomas on 2006-10-22
Just to make certain, could you post the output of this command?
```
dpkg --list | grep libdvd
```

Can you open a data DVD?

---

### Post by Robgould on 2006-10-22
I can't open any dvd....even a data.  

This is what I get from a data dvd burnt from WinXP with Nero.

```

rgould@rgould-laptop:~$ sudo mount /dev/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rgould@rgould-laptop:~$ dmsg | tail
bash: dmsg: command not found
rgould@rgould-laptop:~$ dmesg | tail
[17179613.604000] Bluetooth: HCI socket layer initialized
[17179613.616000] ath0: no IPv6 routers present
[17179613.896000] Bluetooth: L2CAP ver 2.8
[17179613.896000] Bluetooth: L2CAP socket layer initialized
[17179614.260000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179614.428000] Bluetooth: RFCOMM socket layer initialized
[17179614.428000] Bluetooth: RFCOMM TTY layer initialized
[17179614.428000] Bluetooth: RFCOMM ver 1.7
[17179753.108000] Unable to identify CD-ROM format.
[17190624.980000] Unable to identify CD-ROM format.


```

---

### Post by lopzided on 2006-10-22
> **jordanmthomas said:**
> Just to make certain, could you post the output of this command?
```
dpkg --list | grep libdvd
```

Can you open a data DVD?

juztin@juztin-laptop:~$ sudo dpkg --list | grep libdvd
Password:
ii  libdvdcss2                             1.2.9-1plf4                            portable abstraction library for DVD decrypt
ii  libdvdread3                            0.9.4-5.1                              Simple foundation for reading DVDs
juztin@juztin-laptop:~$

EDIT : i don't own any data DVD's :P

---

### Post by jordanmthomas on 2006-10-22
lopzided, you do in fact have the libdvdcss2 installed, so my guesses were wrong.  You and Robgould seem to have similar problems...like maybe your DVD-reading ability isn't being detected.  

I was just popping in this thread to try and help, but I don't really know anything about how to get DVD drives working, so you'll have to wait for someone who does.  :p

---

### Post by Robgould on 2006-10-24
I thought maybe it was edgy...so I did a clean install of dapper.  Same problem

---

### Post by Robgould on 2006-10-24
ok...i tried something else.

I put in a windows install CD.  The disk was read fine.

I put in a Fedora 5 install DVD that I burnt from WinXP.  It was read fine.

So I know that the issues is not with my player.  It is with the format.  The problem is that this format is read easily from windows.  I know it is not a bad disk.  It is just a format that ubuntu does not like.  

This is a data DVD made with Nero.  Any ideas?

---

### Post by Robgould on 2006-10-25
My issue is resolved....the answer is here.

[http://www.ubuntuforums.org/showthread.php?t=282515](http://www.ubuntuforums.org/showthread.php?t=282515)

---

### Post by lopzided on 2006-10-27
unfortunately, that didn't work for me.

here is the output when i try to play a commercial dvd from the console using mplayer:
```

juztin@juztin-laptop:/etc$ mplayer dvd://
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://


Exiting... (End of file)

```

help please!

---

### Post by SnTholiday on 2006-10-27
I was able to play DVD movies fine until I upgraded to Edgy, now I have the same problem as everyone else, no media players can open the disc. When I insert the disc the system is seeing it, I get the DVD icon on the desktop with the name of the title of the disc. Just no media players can open them.

---

### Post by gbinal on 2006-10-31
I'm joining the club.  

I've spent a few hours perusing the forums and some other major linux forums seeking to address this same problem.  CDs work just fine, but DVDs are ignored, and trying to get any movie player to see them gets me told that there's no disc in the drive and such.  

Question 1: Would it help if I accumulated and summarized much of the related links to these problems?  Some are similar but different and seem to result in success for people.  I've not found anything that solves my problem, but it's also worth it to me to suck it up until it works out as Ubuntu progresses.  

Obvious Question 2: How to fix this?  I seem to have the right links to my dvd drive, but...
One difference was that I had this problem with breezy and dapper, too.  Am Edgy now (nice by the way, to anyone involved there).

Peace, and thanks to everyone for posting...

---

### Post by dca on 2006-11-02
I, too, am having trouble.  The DVD-ROM in my laptop running 6.10 can read data DVDs fine, but my wife's when I drop a data DVD in her PC w/ 6.06 and a DVD burner it crashes the system...  Literally freezes the system and the CPU fan goes crazy...  DVD movies play fine in both, odd.

---

### Post by grashdur on 2006-11-02
I'm a totally new Ubuntu user, and I'm really impressed with this OS! But I'm having exactly the same problem as Brian: I've just installed Ubuntu 6.06.1 on two laptops, and on each of them Ubuntu sees the CD/DVD drive as "cdrom". I can't see movies, and I can't see the contents of my data backup DVD. 

I hope there's some really easy solution out there, as I'm not a command-line person, at least not yet. Perhaps the solution is just to wait for the next Ubuntu release....?

---

### Post by gerryg on 2006-11-18
Hi there,

I'm also having the same problem: CDs are recognized but DVDs are
not. I just get "mount: No medium found" when trying to mount a DVD,
while the identical mount command works fine for CDs.

Next to Ubuntu 6.10, I tried it with Knoppix (5.0.1) and got the same
problem. But since Knoppix is also Debian based, the behavior might
be the same.

Could it be some master/slave order problem at the IDE bus? Did
anybody solve the problem by rearranging the IDE devices (maybe
omitting some)? My setup is:
[LIST]
[*]hda: hard disk 1
[*]hdb: DVD-ROM
[*]hdc: hard disk 2
[*]hdd: CD-R/RW
[/LIST]

Or is it a BIOS related thing?

Below is the output of "lshw -C disk":
```
# lshw -C disk
  *-disk                  
       description: ATA Disk
       product: ST360020A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 3.34
       serial: 6EX057T8
       size: 55GB
       capacity: 55GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma2 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 47MB
          capabilities: primary
     *-volume:1
          description: Linux swap / Solaris partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 517MB
          capabilities: primary nofs
     *-volume:2
          description: Linux raid autodetect partition
          physical id: 3
          bus info: ide@0.0,3
          logical name: /dev/hda3
          capacity: 19GB
          capabilities: primary multi
     *-volume:3
          description: Linux filesystem partition
          physical id: 4
          bus info: ide@0.0,4
          logical name: /dev/hda4
          capacity: 36GB
          capabilities: primary
  *-cdrom
       description: DVD reader
       product: TOSHIBA DVD-ROM SD-M1612
       vendor: Toshiba
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 1004
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdb
  *-disk
       description: ATA Disk
       product: Maxtor 32049H2
       vendor: Maxtor
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: YAC614Y0
       serial: L2R1D2KC
       size: 19GB
       capacity: 19GB
       capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
     *-volume
          description: Linux raid autodetect partition
          physical id: 1
          bus info: ide@1.0,1
          logical name: /dev/hdc1
          capacity: 19GB
          capabilities: primary multi
  *-cdrom
       description: CD-R/CD-RW writer
       product: CR-48X8TE
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 1.1E
       serial: 1K13LH0194
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdd
```


And here is the IDE related output of dmesg:
```
Probing IDE interface ide0...
hda: ST360020A, ATA DISK drive
hdb: TOSHIBA DVD-ROM SD-M1612, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: Maxtor 32049H2, ATA DISK drive
hdd: CR-48X8TE, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
hda: cache flushes not supported
 hda: hda1 hda2 hda3 hda4
hdc: max request size: 128KiB
hdc: 40021632 sectors (20491 MB) w/2048KiB Cache, CHS=39704/16/63, UDMA(100)
hdc: cache flushes not supported
 hdc:<6>hdb: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
 hdc1
hdd: ATAPI 40X CD-ROM CD-R/RW drive, 8192kB Cache, UDMA(33)
```


Any help is highly appreciated!

Thx,
Gerald

---

### Post by Adanufgail on 2006-11-19
I have a similar problem. Whenever I insert a CD, Ubuntu can see it just fine. DVDs won't mount 
```
michael@Ghost:~$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
The oddity (and difference) is that I get the same problems in Windows XP as well. Is it possible that this is a hardware error caused by Ubuntu, as it was working fine in XP not 5 days ago.

Any help will be greatly appreciated,
Michael

---

### Post by daveguy on 2006-11-22
> **Robgould said:**
> I thought maybe it was edgy...so I did a clean install of dapper.  Same problem

See now, I had NO problems at all playing DVD's under dapper, but since I updated to edgy DVD's will not mount, data or movie. CD's seem to work fine, though. Frustrating, to say the least.

---

### Post by gerryg on 2006-11-22
Hi there,

I also posted this topic in the [Debian User Forums]("http://forums.debian.net/viewtopic.php?p=39587#39587") where I got the advice to compile a new kernel.

So I followed Ubuntu's [KernelCustomBuild]("https://wiki.ubuntu.com/KernelCustomBuild") instructions, obtaining the ubuntu-2.6.git kernel (2.6.19-6) by git (the simple way didn't work). Which took a lot of time... Moreover, if you don't wont to wait too long until your kernel is compiled, you should specify the flavours flag like e.g.:
```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
[NVIDIA users only: The new kernel also required to compile the NVIDIA drivers (available at nvidia.com), where you need the xserver-xorg-dev package.]

However, the good news is: DVDs are working now! :) 

Since this is a rather lenghty process, I would highly appreciate a kernel update from Ubuntu.

Gerald

---

### Post by faithsnathan on 2006-11-25
Just to make certain, could you post the output of this command?
 	Code:
 	[LEFT]dpkg --list | grep libdvd

[/LEFT]
 
I entered that, and this is what the terminal says:

```

nathan@nathan-desktop:~$ dpkg --list | grep libdvd
ii  libdvdcss2                             1.2.9-1plf4                             portable abstraction library for DVD decrypt
ii  libdvdnav4                             0.1.9-3                                 The DVD navigation library
ii  libdvdplay0                            1.0.1-6                                 portable abstraction library for DVD menus s
ii  libdvdread3                            0.9.4-5.1                               Simple foundation for reading DVDs


```


Also, when i graphically go to:  Places ---> Computer, Right Click on CD-ROM/DVD-ROM Drive, and Click on Mount Volume, then the following error message comes up:  Unable to mount the selected volume.  Show Details   mount: no medium found

This really seems to be a frustrating thread for many people.  Hopefully, someone can come up with an answer soon.

By the way:  I'm trying to play commercial DVDs in my DVD drive.

---

### Post by CtrlAltDelete on 2006-11-25
I am using Dapper.. I thought my dvd didn't work because i am an uber noob...glad I am not alone



adam@ubuntu:~$ dpkg --list | grep libdvd
ii  libdvdnav4                             0.1.9-3    The DVD navigation library
ii  libdvdread3                            0.9.4-5.1    Simple foundation for reading DVDs
adam@ubuntu:~$

---

### Post by faithsnathan on 2006-11-25
Also, in my /etc/fstab file it says

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I don't know if that will help.  Maybe a mod will stumble across this thread?

---

### Post by gerryg on 2006-11-25
> **faithsnathan said:**
> Just to make certain, could you post the output of this command?
 	Code:
 	[LEFT]dpkg --list | grep libdvd

[/LEFT]

This is what I get:
```
ii  libdvdcss2                                 1.2.5-1                              
ii  libdvdread3                                0.9.6-3ubuntu1 
```                      

> **faithsnathan said:**
> Also, when i graphically go to:  Places ---> Computer, Right Click on CD-ROM/DVD-ROM Drive, and Click on Mount Volume, then the following error message comes up:  Unable to mount the selected volume.  Show Details   mount: no medium found

That's the same problem that I had, trying to mount a DVD from the command line: no medium found.

> **faithsnathan said:**
> This really seems to be a frustrating thread for many people.  Hopefully, someone can come up with an answer soon.

The problem seems to be in the kernel's device drivers. I'm not an expert on these things, but since installing a new kernel solved the problem, it can't be anything else. Still, compiling a new kernel is not what a user usually wants to do...

Gerald

---

### Post by CtrlAltDelete on 2006-11-25
I fixed my problem following this procedure: Hope it works for you all

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html)

---

### Post by gerryg on 2006-11-25
> **CtrlAltDelete said:**
> I fixed my problem following this procedure: Hope it works for you all

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html)

Hi,

this is a different problem.
We don't even get to the point of reading (mounting) **any** DVD, while your link tackles the problem of how to read **encrypted** DVDs.

Gerald

---

### Post by faithsnathan on 2006-11-25
> **CtrlAltDelete said:**
> I fixed my problem following this procedure: Hope it works for you all

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html)

Thank you for the link, CtrlAltDelete.  I did see that in a different post and followed it before stumbling across this post.  Unfortunately, all it did for me was to add the 8th DVD "player" to my computer (not a single one works) and who knows what all behind the scenes.  I probably have more codecs than the internet has available.  Anyway, I'm still looking for the answers, as I think other members on this thread are as well.  

> 
Hi there,

I also posted this topic in the [Debian User Forums]("http://forums.debian.net/viewtopic.php?p=39587#39587") where I got the advice to compile a new kernel.

So I followed Ubuntu's [KernelCustomBuild]("https://wiki.ubuntu.com/KernelCustomBuild") instructions, obtaining the ubuntu-2.6.git kernel (2.6.19-6) by git (the simple way didn't work). Which took a lot of time... Moreover, if you don't wont to wait too long until your kernel is compiled, you should specify the flavours flag like e.g.:
     Code:
     [LEFT]AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic[/LEFT]
 
[NVIDIA users only: The new kernel also required to compile the NVIDIA drivers (available at nvidia.com), where you need the xserver-xorg-dev package.]

However, the good news is: DVDs are working now! :smile: 

Since this is a rather lenghty process, I would highly appreciate a kernel update from Ubuntu.

Gerald


That's great that that worked for you, Gerald.  However:
1.  What's a kernel?
2.  What is compiling?
3.  Is compiling something that a mortal man should actually attempt?
4.  What's so wrong with crap just working anydangway?

I'm desperately trying to get rid of Windows (in other words, my Windows partition on this raggedy old computer).  This task cannot be accomplished until I can watch DVDs in Ubuntu (then I'd try to figure out how to get Ubuntu to stretch out over Windows' partition and become the whole 30GB hard drive).  

I have two options available to me to be able to watch DVDs in Ubuntu:
1.  I have a DVD player hooked up to my TV Tuner card.  This arrangement worked perfectly in XP.  However, I've tried in vain thus far to get it to work.  ](*,)
2.  My Compaq computer came with a DVD-ROM Drive.  If I could get this to work, then I wouldn't need the whole DVD player and TV tuner thing.

Thanks for taking the time to read all this!  Any help would be appreciated.

~Nathan

---

### Post by gerryg on 2006-11-26
> **faithsnathan said:**
> 
1.  What's a kernel?
2.  What is compiling?
3.  Is compiling something that a mortal man should actually attempt?
4.  What's so wrong with crap just working anydangway?

ad 1. In computing, the kernel is the central component of most computer operating systems (OSs). Its responsibilities include managing the system's resources and the communication between hardware and software components ([Wikipedia: Kernel]("http://en.wikipedia.org/wiki/Kernel_computer_science")).

ad 2. An executable program on your computer is actually a sequence of ones and zeros. Of course, software is not written this way, but in some high level language (like C). A compiler translates such code into the executable 0-1-sequence ([Wikipedia: Compiler]("http://en.wikipedia.org/wiki/Compiler")).

ad 3. You can compile a kernel by following the recipe in the [KernelCustomBuild]("https://wiki.ubuntu.com/KernelCustomBuild") guide. However, it will be rather cryptical if you have no idea about software development, and if anything goes wrong, you probably need some expert's advice.

Hope that helps,
Gerald

---

### Post by gerryg on 2006-11-26
Hi again,

I just stumbled across another problem: My drive cannot read DVD+R disks (while DVD- disks are working). According to an Internet search, the drive (Toshiba SD-M1612) should be able to read DVD+ disks.

So I changed the drive against an older one (type "dhi-g40"), where things got even worse: The old problem of not being able to read any DVD re-emerged! Obviously the matter is more difficult...

Looks like we need some expert's help.

Regards,
Gerald

---

### Post by faithsnathan on 2006-11-26
gerryg, I'm sorry that you're having more problems with your stupid DVD drive.  Thank you for explaining the stuff I'd asked about.  I guess after you do so much searching for one specific thing, it gets like "I don't really have the time and energy to search for more weird stuff."  So even though I could have googled up all that stuff, I was just getting too tired last night to go searching around for myself the answers to my never-ending-supply-of-questions.

On the good side, I'm going to try to get my brother-in-law (who's a programmer by day) to do that recompiling kernel thing-a-mabob sometime.  We'll see if that works out.  :-k

---

### Post by David Valentine on 2006-11-28
I'm having similar troubles to others here.  I'm using the AMD64 version of Kubuntu 6.10.  When I insert a commercial DVD, it "mounts" (i.e., it shows up on my desktop), but when I double-click on it, it comes up empty.  Moreover, I can't play the DVD using any of my media players.  What I *can* do is to use K9copy to read the DVD and produce a .iso of it...  Can anyone else having similar problems replicate that?>                      Originally Posted by **faithsnathan**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=1805880#post1805880")                 
                 Just to make certain, could you post the output of this command?
     Code:
     dpkg --list | grep libdvdAnd here is what I get:```
$ dpkg --list | grep libdvd
ii  libdvdcss2                                 1.2.9+debian-1duo+etch1              library for accessing DVDs
ii  libdvdnav4                                 0.1.9-3                              The DVD navigation library
ii  libdvdplay0                                1.0.1-7                              portable abstraction library for DVD menus s
ii  libdvdread3                                0.9.6-3ubuntu1                       library for reading DVDs
```and the appropriate line from my fstab is```
/dev/hdc /media/cdrom1 auto user,atime,noauto,rw,dev,exec,suid 0 0
```

---

### Post by L34NN3 on 2007-01-13
I have the same problem. I have just installed kubuntu and am amazed with it. I am so glad I srcapped windows. Until now i have had no problems installing anything and am reasonably comfortable using terminal programs.

I have installed libdvdcss2 using synaptic and adept but when I type the command in terminal to find the file it isnt recognised. Until I am able to locate where these have gone I am at a loss what to do until I find them! 

Also a lot of the commands listed come up with unrecognised command which I thought was a bit odd. Does Kubuntu use a different language to Ubuntu or something??

Any further help would be great...

---

### Post by gerryg on 2007-04-21
Good news: Ubuntu 7.04 solved the problem!

Cheers,
Gerald

---

### Post by oky on 2007-09-15
Same problem on vaio vgn-s260 laptop.
Play cds , no movie dvds

my output
\ii  libdvdcss2                                 1.2.5-1                                a portable abstraction library for DVD decry
ii  libdvdnav4                                 0.1.10-0.1                             The DVD navigation library
ii  libdvdplay0                                1.0.1-7                                portable abstraction library for DVD menus s
ii  libdvdread3                                0.9.7-2ubuntu1                         library for reading DVDs


/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


running feisty is all the upgrades.

---


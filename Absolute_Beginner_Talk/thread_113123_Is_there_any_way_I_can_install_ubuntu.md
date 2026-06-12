---
title: "Is there any way I can install ubuntu ?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-01-05
ok here is what is happening. I have a windows 98 computer. Windows 98 is horrible. I want to run ubuntu. Now I have the burned cd. I went into my BIOS and discovered that I don't have the option to boot from a cd. I tried to do a bios upgrade from my manufacturer but I can't write to floppies ! I tried to get the smartbootmanager to work but everytime I try to format a floppy I get an error. Is there any possible way I can run ubuntu ??? I really want to -_- The I can't just install it is b/c I want to keep windows. PLEASE HELP ! I HATE WINDOWS. :KS

---

### Post by proventech on 2006-01-05
do you know someone else that has a computer?  maybe they will let you plug your hard drive in and boot to their cd?

---

### Post by xXx 0wn3d xXx on 2006-01-05
nope, I have a 12 gig hdd in this thing and it's about 10-15 pounds and it's mounted to the frame of the computer. This computer is about 10 years old but it still runs well.

---

### Post by xXx 0wn3d xXx on 2006-01-05
is there any possible way ?

---

### Post by bonzodog on 2006-01-05
it actually sounds like it will be possible, but very difficult. How is it you can't write to floppies in windows?
It also sounds like your system will be too old to support ubuntu, you might want to try ubuntu lite (link anyone???). 
Can you post what you know/can work out of your system specs?

Amount of Ram, hard disk size, graphics card/motherboard if possible?

---

### Post by achafe on 2006-01-05
Maybe you could get a friend to make a bootable floppy for you?

Then you could insert the floppy and have that trigger the install CD.  I know there's a floppy image somewhere that will do that, perphaps someone else here can tip you off!

---

### Post by xXx 0wn3d xXx on 2006-01-05
ram= 128 megs, hdd= 12 gigs, 8.491 free, graphics card = ?, motherboard= intergrated, made by compaq. I have a Compaq Presario 5630.

---

### Post by bonzodog on 2006-01-05
What processor is that?

I used to own a compaq, and changing the bios to boot from cdrom wasn't a problem. The fact that you are having problems writing to floppy discs tells me you might have a hardware set-up problem. oh, and remember, there is a tab on the floppy disk in the top corner that stops you from writing if left closed.

---

### Post by poofyhairguy on 2006-01-05
I had a problem like this. To fix I gutted another system and used it to install Ubuntu on the hard drive, then I put the hard drive back into the original computer. 

Have a friend that will let you do that?

---

### Post by d1337 on 2006-01-05
Stock Specs of that box:

Processor: Pentium II - 400Mhz
Memory: 128 MB RAM
Video Card: ATI 3D Rage Pro AGP 2X
Drives: 12.0 GB Hard Drive
2x DVD-ROM Drive (about 20x CD-ROM)
100 MB Zip Drive
3.5" Floppy Drive
Modem: Rockwell HCF 56K Winmodem
Sound: ESS Maestro-2 Sound Card
Ethernet Card: 10BaseT Card
Features: USB Ports
Firewire Ports

It is indeed a bear for harddrive removal.  Seems like there were quite a few machines during that era that didn't want you taking things apart.

Floppy disks are scary...I remember storing things on them 20 years ago.  If you haven't a bios option, a floppy install may be your best bet (or a long ide cable to hook up to another box.)  Each time I've attempted to format floppies or dd to them, I've ended up pitching about half of them.  Make sure your floppies are new or go pick some up (twice as many as you need).  Try writing smartbootmanager after acquiring a "known good" floppy.  Also, your floppy drive might be toast.  I've pitched quite a few of them over the last few years as well.

d1337

---

### Post by Nightwind on 2006-01-05
[QUOTE=MasterChief1234]is there any possible way ?[/QUOTE]
You could take the computer to a friends house, open the case undo the ribbon and the power cables from your hard drive and use the friends computers ribbon and power cable on your hard drive to install Ubuntu, how ever there could be issues because of the different mother board and other hardware specs, but it's worth a shot. I've done this several times with no issues. But that doesn't mean that it will work in every instance. 
Where are you from?

---

### Post by xXx 0wn3d xXx on 2006-01-08
What if I partion my HDD and then could I insert the dics and direct it to that partion ? Or no....am I screwed ?

---

### Post by diggs on 2006-01-08
I'm gonna be the devil's advocate here and tell you to go buy a new computer. go get something used. or refurbished. or whatever. It's time, step into 2006, burn DVD's, have dual boot systems that surf the internet wirelessly. I'm just being blunt; it's time. :)

(I'll stop posting in this thread now)

---

### Post by Lord Illidan on 2006-01-08
[quote=diggs]I'm gonna be the devil's advocate here and tell you to go buy a new computer. go get something used. or refurbished. or whatever. It's time, step into 2006, burn DVD's, have dual boot systems that surf the internet wirelessly. I'm just being blunt; it's time. :)

(I'll stop posting in this thread now)[/quote]

I second this. Also on such a computer, consider Damn Small Linux instead of Ubuntu.

---

### Post by lha on 2006-01-08
Option 1:
Install Smart Boot Manager on your hard drive and use it to boot the install cd.

Option 2:
Use can use [loadlin]("http://elserv.ffm.fgan.de/~lermen/") or [linld]("http://port.imtp.ilyichevsk.odessa.ua/linux/linld/") to load a linux kernel and start the installer. Download one of them to your hard drive. You'd be better of with linld as loadlin has had troubles with kernel images > 1MB. (Ubuntu installer's kernel is 1.2MB) Newest version of loadlin claims to able to hand bigger kernels, but I've still seen complaints on it. I can't remember which one I used to launch a netinstall on a computer with troubles reading both floppies and cds.

So now you should have linld.com somewhere. Restart in DOS-mode. Put Ubuntu installer cd in and go to the directory you have linld.com in and execute
```

linld.com image=d:\install\vmlinuz vga=normal initrd=d:\install\initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
```
where d:\ is your cd-rom drive. This should launch the Ubuntu installer. I'm not able to test this until Wednesday or Thursday, so you'll have be adventurous or wait a couple of days. :D

---

### Post by lha on 2006-01-08
[QUOTE=d1337]Stock Specs of that box:

Processor: Pentium II - 400Mhz
Memory: 128 MB RAM
Video Card: ATI 3D Rage Pro AGP 2X
Drives: 12.0 GB Hard Drive
2x DVD-ROM Drive (about 20x CD-ROM)
100 MB Zip Drive
3.5" Floppy Drive
Modem: Rockwell HCF 56K Winmodem
Sound: ESS Maestro-2 Sound Card
Ethernet Card: 10BaseT Card
Features: USB Ports
Firewire Ports

d1337[/QUOTE]

BTW, you should consider if you really want to use Gnome or KDE with only 128MB of memory and 400MHz processor because they will be quite slow. I've used Ubuntu on a 466MHz Celeron with 320 MB of memory and it was usable but a bit sluggish. Maybe [Xubuntu]("https://wiki.ubuntu.com/Xubuntu")? It has [XFCE]("http://www.xfce.org/") which is a nice desktop. And for a compact install and a snappy interface, [DSL]("http://damnsmalllinux.org/").

---

### Post by Terry of Astoria on 2006-01-08
I've run Ubuntu on PII 400s before. As long as 256-plus RAM it's OK! Even 128 will run. However you'll find you get a big improvement in performance when you add RAM from there.
   He's right. SBM will boot a CD but only if the CD drive itself can do such a thing. I've had to replace those a few times to get an old machine to boot using SBM. No big deal, though. You can get some RAM and a CD drive for just a few dollars.

---

### Post by Bartender on 2006-01-08
Master Chief -
I see you're still having fun with that old Compaq.  I went to Compaq Support, typed in "5630", followed a few links, and found online directions for your BIOS.  

[http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=93523&dest_page=product&cc=us&docname=bph07110#N1564](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=93523&dest_page=product&cc=us&docname=bph07110#N1564)

That's one heck of a long link.  Hope you can copy and paste it.  If not, try this...

[http://h10025.www1.hp.com/ewfrf/wc/siteHomeC?lc=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/siteHomeC?lc=en&cc=us) 

Type "5630" into the Search line, keep following the prompts.  At that first link there are some pretty decent directions for moving around in your BIOS.  It sure looks like you've got a boot order menu.  Unless the BIOS shown isn't anything like the one you've got!  If you absolutely can't make any progress with that old thing, diggs is on the right track.

---

### Post by lha on 2006-01-11
Ok, I just installed Dapper by loading the installer from Windows 98. You can do the same for Breezy.

First, you'll need two files, [linux]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux") and [initrd.gz]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz"). Those files are on Ubuntu install cd, too. Look into install/netboot/ubuntu-installer/i386. Put those files somewhere on your hard drive.

Then you want to get [linload]("http://elserv.ffm.fgan.de/~lermen/"). [The file you need]("ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/loadlin.exe.gz") is compressed, so you'll have to extract it. Put loadlin.exe to the same directory you have the two files we fetched earlier.

Last but not least, breezy.bat. Open notepad and paste the following lines in it.
```
smartdrv /C
loadlin.exe linux vga=normal initrd=initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
```
Save the file as breezy.bat in the same directory as used above.

Now we're ready to start installation. Restart your computer and press F8 during boot up sequence to get into the menu that allows you to boot into command line. (Restart to MS-DOS mode from Start Menu didn't work for me.) Cd to the folder where you put the four files, type breezy and hit enter.

---

### Post by linuxden on 2006-01-11
I have installed Ubuntu linux on a old compaq... also running win98.. about 9 years old... There is a really weird system to take out the harddrive its like they dont use screws just a green arm a nd a yellow button in the green arm once pushed it releases the drives from the front of the computer so you gotta pull the drive out the front... (remove the facade... Easily done...)

Ubuntu ran real smooth on celeron 600mhz 256 ram... bout ten times faster than when it had win98....

Hope that helps ya in anyway...(i first thought drive was not removable when i saw green and yellow system...)

---

### Post by jerstew on 2006-01-15
Im sure you've figured it out by now, but I just wanted to add this.
I've seen lots of complaints about being unable to install ubuntu from cd. I also have a fairly old machine and am looking forward to upgrading soon.
I've been using linux for 10 years now, since it was a baby, and have allways had good luck with old hardware. But its a trick.
If Ubuntu CD boots but locks your computer while copying files from cd:
at boot prompt type *expert*. Then load the install from iso on hd module. It will search your hd for an iso, and install from there, also install is much faster.
If you cant boot from CD use a disk or loadlin from windows.

---

### Post by Nightwind on 2006-01-17
[QUOTE=lha]Ok, I just installed Dapper by loading the installer from Windows 98. You can do the same for Breezy.

First, you'll need two files, [linux]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux") and [initrd.gz]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz"). Those files are on Ubuntu install cd, too. Look into install/netboot/ubuntu-installer/i386. Put those files somewhere on your hard drive.

Then you want to get [linload]("http://elserv.ffm.fgan.de/~lermen/"). [The file you need]("ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/loadlin.exe.gz") is compressed, so you'll have to extract it. Put loadlin.exe to the same directory you have the two files we fetched earlier.

Last but not least, breezy.bat. Open notepad and paste the following lines in it.
```
smartdrv /C
loadlin.exe linux vga=normal initrd=initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
```
Save the file as breezy.bat in the same directory as used above.

Now we're ready to start installation. Restart your computer and press F8 during boot up sequence to get into the menu that allows you to boot into command line. (Restart to MS-DOS mode from Start Menu didn't work for me.) Cd to the folder where you put the four files, type breezy and hit enter.[/QUOTE]
This would work great as long as you are installing on a computer with an existing O.S. but how would you propose to get those files to a computer with no working O.S., CD or a SCSI CD drive, network, PXE, and that SBM, Toms and the other various assorted ways to do this that have been sugested in this long running issue?

---

### Post by xXx 0wn3d xXx on 2006-01-23
do I need to create a new parton (sp?) before installing ? I am finally ready to install and I know what I am doing. I just need this final info. If I do need to create a new parton (I want to keep windows) please give me a link to some software what will allow me to do it with speed and with ease of mind.

---

### Post by xXx 0wn3d xXx on 2006-01-23
please respond soon. I want to get this done with.

---

### Post by d1337 on 2006-01-23
I'm kinda lost as to where you are now.  I have refreshed myself by reading the entire thread, but I don't know if you've gotten to a point that you can install with CD or what.  Please clarify so that we can help you.

d1337

---

### Post by xXx 0wn3d xXx on 2006-01-23
ok, I started the install. I got to the partition part and I only have one (It's windows) do I have to create a new partition so I can dual boot ?

---

### Post by d1337 on 2006-01-23
Yes, but the partitioning part of the install will likely do exactly what you need.  Have you defragged the windows partition?  Are you going to install a Gnome environment or do a server install and add xubuntu-desktop?

d1337

edit:  DO NOT SHORTCUT THE DEFRAG...Might even do it twice

---

### Post by xXx 0wn3d xXx on 2006-01-23
my question is: DO I NEED TO CREATE ANOTHER partition or can I just install it with windows ??? and I will have to defrag. and I am installing Gnome

---

### Post by d1337 on 2006-01-23
When setting up a dual boot box, the simplest way is to have windows installed first.  Defrag your windows partition.  When you boot from CD, it will take you through a few steps and bring you to a partitioning tool.  There is an option to shrink the existing partition (windows) and to use the freed space.  It usually sets  up the swap etc. for you.  Towards the end of the install (from CD), it should detect Windows and ask if it is the only other OS on your system before adding grub to the mbr.

d1337

edit- when it shrinks the existing partition it will create a new partition in the freed space as well as swap area.

2nd edit...I'd really rethink the gnome thing in regards to your machine specs.  PII with 128 is going to be very slow and frustrating.  I'd suggest a server install and adding xubuntu or choosing a lighter distro.

---


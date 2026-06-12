---
title: "G3 Powerbook - waiting for root file system.."
date: 2006-09-26
forum: Apple PPC Users
---

### Post by o2o2o2o2 on 2006-09-26
I'M STUCK!

Took awhile, but I finally got BootX working.  Trying to install Ubuntu 6.06 PPC.  Now im at the booting stage of linux and i get through a bunch of post lines, then it stops at "Begin:  Waiting for root file system" and then gives an error of "Alert! does not exist.  Dropping into a shell!"  

[IMG]http://img147.imageshack.us/img147/2527/powerbookfv2.jpg[/IMG]

To give some background, I formatted the drive in os9 at 300mb, then left the 3.8 gigs unallocated.  For BootX, i have the options set to force video and use specified ram disk and the kernal set to vmlinux which i got both from the ubuntu cd.  Maybe  I need to specify the hard drive?  But i duno what to call it, the apple format utility didnt mention anything about the drive being HDA8, or HDA9, etc... Duno what to do.

PS.  For anyone trying this on a 14" Powerbook 266Mhz the video argument for BootX that worked for me was:

video=atyfb:vmode12,cmode:8,mclk:63

The other modes i tried showed me 4 screens all doing the boot up procedure, hehe.  Took a little trial and error to get this right.

---

### Post by linear on 2006-09-26
The instructions [here]("https://help.ubuntu.com/community/Installation/OldWorldMacs") seem to require that you know where the Ubuntu partition is.

Try **fdisk -l** (that's a lowercase "L") to get a list of partitions.

---

### Post by o2o2o2o2 on 2006-09-26
Its saying "/bin/sh: fdisk: not found"

---

### Post by o2o2o2o2 on 2006-09-26
Im wondering if I should have partitioned the drive in the apple drive utility as: 

Partition 1:  hfs
Partition 2:  Linux Home

Instead of: 

Partition 1:  hfs
Partition 2:  Unallocated


???

---

### Post by beanmarine101 on 2006-09-27
Well, this probably won't solve your problem. But do you intend on using Ubuntu as your primary system? If so, it should probably go in your first partition.

Also, you might want to create your root directory from that command line. It might not work because necessary files will be missing, but you could do a "sudo mkdir " and then put the address where the root system should be. I can't recall what it is right now. 

Actually, doing that would probably make your root's home folder, not the directory. >.<

---

### Post by o2o2o2o2 on 2006-10-01
Ugg... spent 3 days on this so far.  I'm determined to get it.

Tried tons of open firmware things, tried installing mklinux and the mklinux bootloader (kinda like bootx) tried other ubuntu dist, suse, yellowdog 4.1.

Cant get anything to work.  CD-Rom works good, I just dont know enough about linux to troubleshoot.  I still cant get to the installer screen, not even close to booting... 

UGGG... help!

I have a webcam I can point at the screen if someone wants to do some kind of chat program and video with me?

Hehe, im desperate.  This is driving me nuts.

---

### Post by o2o2o2o2 on 2006-10-01
Well, I read many stories about Ubuntu 5.10 installs, so I said what the heck, I'll track down a 5.10 iso burn it and try it.  

Its booting now!!!!  Finally at the install screen!!!!

Whats so different from 5.10 and 6.06 PPC?  Wish I knew ahead of time this wasnt going to work.  Hehe.

Installing now, I'll let you know how it goes.....

---

### Post by abtabt on 2006-10-02
hello i get the same problem whith the free shipping cd 6.06 LTS

i belive its not working with oldworld  and i think that is a cd for live 
and install (before was there 2 cds one for install and one for live )

if anyone have succed whith free shipping cd 6.06 LTS

let us now

but i download the server cd 6.06 and install icewm,kde,gnome,xfce desktop or a light system   

with Synaptic

ps if you have a slow computer or like speed on the net
try webbreader  dillo  (ok its not a fullgrow webbreader but i like it)

---

### Post by o2o2o2o2 on 2006-10-03
From what I read, old world support was dropped for 6.06 because of the kernel upgrade.

Well, just wanted to update everyone.  I got unbuntu working!!!

[IMG]http://img141.imageshack.us/img141/5384/g3pe8.jpg[/IMG]

Well, Kubuntu 5.04 to be exact.  I found the problem.  At the final stage, after you have copied the files over in the shell and when everything is done in the installer, and you reboot into os9 bootX, click options and instead of the image.ramdisk.gz chosen, you want to select the new ramdisk.image.gz!!!  That last step of selecting the new gz file is what I missed.  I didnt see it anywhere in the FAQ's and I really dont know much about unix so it was easy to miss.

So for anyone who gets stuck at "waiting for root file system" this might be the solution to your problem.

As for my install. Working well.  But its stuck in 640x480 and ive tried several "video=atyfb:vmode:12,cmode:8,mclk:63" and many more number changes, just not working yet.  I'll keep trying.

---

### Post by abtabt on 2006-10-03
you can install 6.06 to, but i have not succed with with shipping cd 

i use the server cd 6.06 and then i install what i wont
i have ppc4400.G3 begie.and a 7300 running 6.06

 if you like speed 
of your old mac use a low memory desktop
and do a xorg.conf tuning to get more memory to the system 

this link is howto install on oldworld

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

its not complete but you get some tip 

if you have problem with X

you say that try diffrents arg in bootex for the video but nothing happends 
some times i have to delete the old bootex file in macos and then it works
 or you can tray too use macs video support

check xorg.conf ( /etc/X11/xorg.conf)

you can check the log of the X (/var/log/Xorg.0.log)

that tells you whats wrong 

rekonfigure X
 
do a backup of your orginal xorg.conf

sudo dpkg-reconfigure -phigh xserver-xorg

if that not fixit try

sudo dpkg-reconfigure xserver-xorg

and you get a new xorg.conf file

when i try diffrents xorg.conf i start in single mod
its easy to brake and adjuste xorg.conf to try diffrent configrations

---

### Post by o2o2o2o2 on 2006-10-03
Good news / bad news

GOOD:  tried editing the conf file and it worked great.  Thanks.

I pasted this info into it:


Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. 3D Rage LT Pro"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Then went to the control panel for the monitor and selected 1024x768, but coulnt see the ok or apply button because of the low resolution so i guessed and hit enter and it worked. 

 
BAD:
Well, i tried my new found knowlege with the option of clicking the new ramdisk, but it dodnt work with other distros.  Uggg!

O well, i got Kubuntu 5.04 to work and it looks like that is the best im going to do which is fine.  I like it.

One thing i did notice is that in fstab the info was always empty, except in this kubuntu install.  it prefilled everything out.  this showed where my /dev/hda10 root and hda11 swap was.  

Like I said I know very little of linux but I think this may have  had something to do with it.  

So, if you want a painless install of ubuntu on a Apple Powerbook Wallstreet G3 try Kubuntu 5.04.  Worked for me!

---

### Post by Ruedin on 2007-04-07
> **o2o2o2o2 said:**
> Well, just wanted to update everyone.  I got unbuntu working!!!

Well, Kubuntu 5.04 to be exact.  I found the problem.  At the final stage, after you have copied the files over in the shell and when everything is done in the installer, and you reboot into os9 bootX, click options and instead of the image.ramdisk.gz chosen, you want to select the new ramdisk.image.gz!!!  

OK, but what did you before? When I click on "Linux" at BootX, after 10 min it happens exatcly the same. G3 beige. Etienne

---


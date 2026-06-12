---
title: "beige/gray Power Mac G3 wont boot Ubuntu CD"
date: 2009-11-18
forum: Apple Hardware Users
---

### Post by zonemikel on 2009-11-18
hello, I know this has been asked but i believe my case is unique. 

I have downloaded the ppc version of xubuntu specifically "xubuntu-9.04-desktop-powerpc.iso" and burnt it to a cd. I burnt the iso in ubuntu on another machine that is a "pc"

The mac normally boots to Mac OS 9.2. So i put the cd in and hold down 'c' and nothing happens it just boots to 9.2. Once i've booted into the mac os i can see the cd has been mounted and i can read the files on the cd just fine, so i know the cdrom is working at least. 

I've also tried command-control-o-f at startup to try and manually tell it to boot from the cd but it just boots to 9.2 never gives me a option to type anything. 

I dont know a lot about macs but this one is so cute and it makes that awesome sound when you start it, I would love to have it as another system for the kids to play on in the downstairs network. 

Now that I think of it maybe the keyboard is malfunctioning ? I'll have to check that, any other ideas ?

UPDATE: 
well my suspicions were right ! when i went into mac os and opened a simplewriter? thing only the right half of the keyboard would work. Fortunately i had another keyboard i plugged that in and checked that it worked right.
When i boot holding down 'c' nothing happens
when i boot and hit (cmd+alt?+o+f) i get the "open frimware" then i type boot "cd:,\install\yaboot" but then it just boots into mac os anyway. Its weird it types it all in caps could it not find it because its lowercase ? I'm thinking the cd is working because it can read it when i boot into macOS i see that /install/yaboot does exist ? 

Not sure what to do now.

---

### Post by linuxopjemac on 2009-11-18
You have an oldworld mac probably and you need BootX? Or you do something wrong in open firmware...check out my site:


[http://mac.linux.be/content/installation-linux-ppc-based-macs](http://mac.linux.be/content/installation-linux-ppc-based-macs)

Can you tell me exactly what model you are trying to put Linux on?

---

### Post by zonemikel on 2009-11-18
> **linuxopjemac said:**
> You have an oldworld mac probably and you need BootX? Or you do something wrong in open firmware...check out my site:


[http://mac.linux.be/content/installation-linux-ppc-based-macs](http://mac.linux.be/content/installation-linux-ppc-based-macs)

Can you tell me exactly what model you are trying to put Linux on?

Ill check out your site, i'm also going to try and burn the cd at a lower speed, do you think i should try with the alternate installer ? 

When i get to work on it next ill reply with the exact model number and such. 

thanks !

---

### Post by abtabt on 2009-11-19
[QUOTE=zonemikel;8345285]Ill check out your site, i'm also going to try and burn the cd at a lower speed, do you think i should try with the alternate installer ? 



hi
 
you must use BootX if you have beige/gray Power Mac G3 or 604 CPU
(OLD WORLD Macs)

and the    Alternate install CD or Server install CD 
NOT THE Desktop CD (only for NEW WORLD Macs )

i use this on my own beige/gray Power Mac G3

Alternate install CD


[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

---

### Post by tiresia on 2009-11-19
> **abtabt said:**
> 
NOT THE Desktop CD (only for NEW WORLD Macs )

Actually you can boot the Desktop-CD also on Old World Macs. You must give as Kernel Options in BootX the same Options you find in the yaboot.conf of the CD

Of course it can be quite slow according to the installed RAM and Processor

---

### Post by abtabt on 2009-11-19
> **tiresia said:**
> Actually you can boot the Desktop-CD also on Old World Macs. You must give as Kernel Options in BootX the same Options you find in the yaboot.conf of the CD

Of course it can be quite slow according to the installed RAM and Processor

good news :o

can you explain how 



this is yaboot.conf 

# PowerPC subarch 
image=/casper/powerpc/vmlinux
	label=live
	alias=live-powerpc
	initrd=/casper/powerpc/initrd.gz
	append=" boot=casper quiet splash --"
	initrd-size=1048576
	read-only

---

### Post by tiresia on 2009-11-19
If I remember well, you should just add to the options you wrote in the box 'more kernel arguments' what you find after 'append' ie boot=casper quiet nosplash --
(use nosplash NOT splash as in the yaboot.conf)
Let me know, if it works Be patient, it can take long...

---

### Post by iBookClamshell on 2009-11-19
It definitely needs some sort of hack. Installing it onto older machines is so annoying. Even installing an old OSX over 9.2 was somewhat stressful.

Good luck with it.

---

### Post by zonemikel on 2009-11-19
Thanks for all the help. I'm downloading the alternate install cd now, I'll try and install bootx on it when i have time and see how that goes. Maybe this weekend, I'll post back here the results.

---

### Post by abtabt on 2009-11-20
> **tiresia said:**
> If I remember well, you should just add to the options you wrote in the box 'more kernel arguments' what you find after 'append' ie boot=casper quiet nosplash --
(use nosplash NOT splash as in the yaboot.conf)
Let me know, if it works Be patient, it can take long...



hi i tried that on 6.06 LTS Desktop cd


More Kernel arguments in BootX

boot=casper quiet splash --

and the live cd start and boot up (not so slow begie g3 380MB ram)::p

and of course copy kernel to the kernel folder in system folder in Mac OS
and the image in system folder

and restart computer


Alternate install CD or Server install CD

is a better choice for old world (but you can get lost in the djungel);)

copy kernel to the kernel folder in system folder in Mac OS
and the image in system folder

and reboot and then the install begin (no boot arg need )

---

### Post by tiresia on 2009-11-20
Yes, casper is the Directory in the Ubuntu Desktop CD where the Kernel is. In New World machines you boot Yaboot as first, that reads in the yaboot.conf file where to find the kernel. But since in  Old World computers you use BootX, you must instruct it where to find the Kernel. In the same way you can pass other options to the Kernel.

The last time I booted a Live CD on my beige G3 was with Xubuntu 9.04 - 192MB Ram and 315MHz (overlocked) - btw it is not so difficult to overlock a beige G3 to give it a bit more power

---

### Post by zonemikel on 2009-11-20
Finally got some time to work on this, well that time has now gone so i'm here again to see if you guys can help. 

I tried to get the mac to connect to the internet, i did it a long time ago but now it does not want to work. It would not have done me any good anyway because what i got on the internet i cant use. 

Since i couldnt get the inet working i just burnt bootx??.sit on a cd then transfered it over ... well my mac has no idea wth .sit is so it tried to open it in adobe, of course that didnt work. 

So i got "unstuff" and unpacked the .sit on my ubnutu pc and burnt another cd. I put that in the mac and it does not seem to know what those files are either .... 

How do i go about installing bootx, I know that afterwords you are supposed to put the kernel off your install cd into a dir or something of that sort but i cant get that far because i cant get bootx to run. 

I really know very little about the mac os thats why im trying to get ubuntu on there. 

I also noticed that the files have nice names in ubuntu like bootxapp and bootx.readme and such but when i look at them on the mac it is BOOTX_AP did they get messed up when i burnt them? this is turning into a nightmare really quick.

---

### Post by linuxopjemac on 2009-11-20
you need Stuffit expander or something, to unzip that .sit file. I know from experience that it is a hell installing Linux on Oldworld Macs. You need OS 9 or something similar plus some tools like Stuffit as I told. I don't know another way to unstuff it.

---

### Post by linuxopjemac on 2009-11-20
try here
[http://www.pure-mac.com/downloads/stuffitexpanderclassicdl.html](http://www.pure-mac.com/downloads/stuffitexpanderclassicdl.html)

I hope you can unzip hqx files without extra tools....

---

### Post by zonemikel on 2009-11-21
> **linuxopjemac said:**
> try here
[http://www.pure-mac.com/downloads/stuffitexpanderclassicdl.html](http://www.pure-mac.com/downloads/stuffitexpanderclassicdl.html)

I hope you can unzip hqx files without extra tools....

Thanks ... I'll get it on the internet before i try again, that way i can download these files directly and i dont have to burn cd's and such. 

I was trying to install more memory in the machine, it only had 92Mb. I had a bunch of pc133 128Mb sticks but it would not take them, I ended up putting 3x pc100 64Mb's in there to give 192 but now when it boots it says "error pci bus" or something like that. It might be more trouble than its worth. 

Just picked up a nvidia geforce 6800 GTO today for $20 at a garage sale, maybe dual display on my current working (much faster) system would be a better alternative. 

I just hate having this neat mac sitting there, its been sitting there forever. 

Not sure when i'll have time to fuss with it again, finals are coming up. Thanks for all the help! I also have a sun sparcstation 10 ... dont think i'll try and get that running ubuntu though :D

---

### Post by linuxopjemac on 2009-11-22
You need to install BootX in classic MacOS (MacOS7, MacOS 8 or MacOS9). You have to download Stuffix Expander inside the MacOS. Then unstuff that BootX.sit file and put the BootX in the System Preferences, I don't know exactly where now, read my website. You can use iCab as a browser for MacOS. iCab is the only normal browser left for classic MacOS. From here you should have enough tips to get BootX working...Next time I want to see you have the BootX in the right folder and we can progress from there ;)

---

### Post by zonemikel on 2009-11-24
> **linuxopjemac said:**
> You need to install BootX in classic MacOS (MacOS7, MacOS 8 or MacOS9). You have to download Stuffix Expander inside the MacOS. Then unstuff that BootX.sit file and put the BootX in the System Preferences, I don't know exactly where now, read my website. You can use iCab as a browser for MacOS. iCab is the only normal browser left for classic MacOS. From here you should have enough tips to get BootX working...Next time I want to see you have the BootX in the right folder and we can progress from there ;)

Thanks for being so patient and helpful. I actually had to do other things with my server before i could even get the mac on the internet, all that is solved now, the mac works on the net. 

I installed more memory in it so it has 192MB now. I downloaded bootx, I put it in the system folder and it told me it needed to put it in the control panel so i said ok. Then I moved over the bootX extension into the system folder and it told me i should put it in the extensions folder so i said ok. 

BootX wants the "linux kernel" directory to be in the same dir as it .... so i could put the linux kernel dir in the control panel directory also ... ? This is what i have now

system->control panels->BootX App
system->Linux Kernel->vmlinux
also on the desktop i have the same thing.

I'm not sure if all that even matters so ill stop there. BootX runs but i have no idea what my root drive is ? I tried putting in hda and i hit linux and got a kernel panic eventually, i think it said it could not find it. 

If somone could tell me how to find out what my "root device" is i might be able to manage from there. I was trying to use the kernel arguments with 
video=atyfb: vmode: 18, cmode: 15 not sure which ones i should use though.

thanks again, this might actually work. Will i be able to delete os9.2 ? because if not the hdd is only like 4 gigs ...

update:
oh when it boots it says something about not being able to find a suitble kernel module bootx.c line 1050
I tried hda again and it said hda was cdrom and hdc was the boot hdd in the scrolling linux stuff, but that didnt work either. 

It keeps saying append correct root= boot option here are the available partitions:
kernel panic - not syncing: VGS: Unable to mount root fs on unknonw block
(it never tells me the "available partitions")
rebooting in 180 sections. 

but up at 2 seconds it says hdc: quantum fireball ata disk drive 
hdc: mwdma3 mode selected
ide1 at 0xcd....... on irq 26

im gonna try it again at root= /dev/hdc1

..... nope VFS: Cannot open root device "hdc1" or unknown-block(0,0)

I give up for now, balls in your court

---

### Post by linuxopjemac on 2009-11-25
What you need is a program called pdisk to actually read your partition table

[http://homepage.mac.com/alk/downloads/pdisk.sit.hqx](http://homepage.mac.com/alk/downloads/pdisk.sit.hqx)

Here you find information how to use the program. I want you to print the partition tables of your disks and paste it in the forum:

[http://ftp.sunet.se/pub/os/Linux/distributions/mklinux.apple.com/DR3/MacOS_Utilities/pdisk.html](http://ftp.sunet.se/pub/os/Linux/distributions/mklinux.apple.com/DR3/MacOS_Utilities/pdisk.html)

If we know where your linux root on the CD is, we can set BootX properly.

Read my manual at [http://mac.linux.be/content/installation-linux-ppc-based-macs](http://mac.linux.be/content/installation-linux-ppc-based-macs), especially the part about Booting your Mac with BootX if you own an OldWorld Mac and What I did to get Mandrake 8.2 working.

You are getting closer now...

---

### Post by zonemikel on 2009-11-25
> **linuxopjemac said:**
> What you need is a program called pdisk to actually read your partition table

[http://homepage.mac.com/alk/downloads/pdisk.sit.hqx](http://homepage.mac.com/alk/downloads/pdisk.sit.hqx)

Here you find information how to use the program. I want you to print the partition tables of your disks and paste it in the forum:

[http://ftp.sunet.se/pub/os/Linux/distributions/mklinux.apple.com/DR3/MacOS_Utilities/pdisk.html](http://ftp.sunet.se/pub/os/Linux/distributions/mklinux.apple.com/DR3/MacOS_Utilities/pdisk.html)

If we know where your linux root on the CD is, we can set BootX properly.

Read my manual at [http://mac.linux.be/content/installation-linux-ppc-based-macs](http://mac.linux.be/content/installation-linux-ppc-based-macs), especially the part about Booting your Mac with BootX if you own an OldWorld Mac and What I did to get Mandrake 8.2 working.

You are getting closer now...

I'm writing this from the mac. the browser is so old everything looks messed up but i was able to log in. Here isthe output, sorry i cant get the code highlighting to work.

Top level command (? for help): l
Name of device: /dev/hdc

Partition map (with 512 byte blocks) on '/dev/hdc'
 #:                type name             length   base    ( size )
 1: Apple_partition_map Apple                63 @ 1      
 2:    Apple_Driver_ATA*Macintosh            64 @ 64     
 3:    Apple_Driver_ATA*Macintosh            64 @ 128    
 4:       Apple_Patches Patch Partition     512 @ 192    
 5:           Apple_HFS MacOS           8418102 @ 704     (  4.0G)
 6:          Apple_Free Extra                10 @ 8418806

Device block size=512, Number of Blocks=8418815 (4.0G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 21, type=0x701
2: @ 128 for 34, type=0xf8ff

when i do it for /dev/hda it prints out like 45k lines and i can only see up to 32k so idk if there is somthing usefull at the begining. I also dont know how to "control c" on a mac to stop it

---

### Post by abtabt on 2009-11-25
> **zonemikel said:**
> Thanks for being so patient and helpful. I actually had to do other things with my server before i could even get the mac on the internet, all that is solved now, the mac works on the net. 

I installed more memory in it so it has 192MB now. I downloaded bootx, I put it in the system folder and it told me it needed to put it in the control panel so i said ok. Then I moved over the bootX extension into the system folder and it told me i should put it in the extensions folder so i said ok. 

BootX wants the "linux kernel" directory to be in the same dir as it .... so i could put the linux kernel dir in the control panel directory also ... ? This is what i have now

system->control panels->BootX App
system->Linux Kernel->vmlinux
also on the desktop i have the same thing.

I'm not sure if all that even matters so ill stop there. BootX runs but i have no idea what my root drive is ? I tried putting in hda and i hit linux and got a kernel panic eventually, i think it said it could not find it. 

If somone could tell me how to find out what my "root device" is i might be able to manage from there. I was trying to use the kernel arguments with 
video=atyfb: vmode: 18, cmode: 15 not sure which ones i should use though.

thanks again, this might actually work. Will i be able to delete os9.2 ? because if not the hdd is only like 4 gigs ...

update:
oh when it boots it says something about not being able to find a suitble kernel module bootx.c line 1050
I tried hda again and it said hda was cdrom and hdc was the boot hdd in the scrolling linux stuff, but that didnt work either. 

It keeps saying append correct root= boot option here are the available partitions:
kernel panic - not syncing: VGS: Unable to mount root fs on unknonw block
(it never tells me the "available partitions")
rebooting in 180 sections. 

but up at 2 seconds it says hdc: quantum fireball ata disk drive 
hdc: mwdma3 mode selected
ide1 at 0xcd....... on irq 26

im gonna try it again at root= /dev/hdc1

..... nope VFS: Cannot open root device "hdc1" or unknown-block(0,0)

I give up for now, balls in your court





hi
i dont see that you have copy the image from cd to system folder ????

if you use Alternate install CD or Server install CD

copy kernel to the kernel folder in system folder in Mac OS
and the image in system folder

and chose the kernel and the image in bootx and save it

and reboot and then the install process begin (no boot arg need in bootx )


if you use the Destop CD 
then you need 

More Kernel arguments in BootX

boot=casper quiet splash --



after install then you must have kernel arg like
root=/dev/hdax   (or sdax x=number of partion)

---

### Post by abtabt on 2009-11-25
> **zonemikel said:**
> I'm writing this from the mac. the browser is so old everything looks messed up but i was able to log in. Here isthe output, sorry i cant get the code highlighting to work.

Top level command (? for help): l
Name of device: /dev/hdc

Partition map (with 512 byte blocks) on '/dev/hdc'
 #:                type name             length   base    ( size )
 1: Apple_partition_map Apple                63 @ 1      
 2:    Apple_Driver_ATA*Macintosh            64 @ 64     
 3:    Apple_Driver_ATA*Macintosh            64 @ 128    
 4:       Apple_Patches Patch Partition     512 @ 192    
 5:           Apple_HFS MacOS           8418102 @ 704     (  4.0G)
 6:          Apple_Free Extra                10 @ 8418806

Device block size=512, Number of Blocks=8418815 (4.0G)
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 21, type=0x701
2: @ 128 for 34, type=0xf8ff

when i do it for /dev/hda it prints out like 45k lines and i can only see up to 32k so idk if there is somthing usefull at the begining. I also dont know how to "control c" on a mac to stop it


hi you need space for linux on own partion or hd

---

### Post by abtabt on 2009-11-25
> **abtabt said:**
> hi you need space for linux on own partion or hd

have look on this page  ???

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by zonemikel on 2009-11-25
So, i need to install another hdd ? 
I'm using alternate install cd! 

About the copying to system folder there is a icon(looks like hdd) on the desktop that says "station 16" i open it and there are folders like "applications, documents, stationary, System folder" so i open the ubuntu cd and go to cd->install->powerpc then i copy vmlinux from there to this system folder, I also have a folder called "Linux Kernel" inside this system folder that also has vmlinux. 

what do you mean by image ?

---

### Post by abtabt on 2009-11-25
> **zonemikel said:**
> So, i need to install another hdd ? 
I'm using alternate install cd! 

About the copying to system folder there is a icon(looks like hdd) on the desktop that says "station 16" i open it and there are folders like "applications, documents, stationary, System folder" so i open the ubuntu cd and go to cd->install->powerpc then i copy vmlinux from there to this system folder, I also have a folder called "Linux Kernel" inside this system folder that also has vmlinux. 

what do you mean by image ?

you have a file with name image in the install folder on the linux cd its needs on the boot for installation

---

### Post by zonemikel on 2009-11-25
> to &#8220;System Folder/Linux Kernels&#8221;. Copy initrd.gz (the init ramdisk image) to &#8220;System Folder&#8221; and rename it to ramdisk.image.gz Ya i musta missed that step somewhere ... well it booted into linux install when i clicked linux this time ... im staring at the choose language thing, lets see how far i get ? 

Do i need to leave os9.2 on there ? i hope when i get something going maybe i can pull the drive out and dd it to another disk so i dont have to do this again, and maybe i can get some more space ... i have tons of 30 and 40 gig drives around

nevermind about the "do i need os9.2" im reading that link i do need it let me read on i'm at the partitioning part now

I knew this was coming ... there is not enough free space to install ... not sure what kinda hdd this thing uses can i just pop in a second hdd or do i need to somehow partition the freespace using that program pdisk? .. i'm gonna open here up and see if i can put another hdd in

---

### Post by abtabt on 2009-11-25
> **abtabt said:**
> you have a file with name image in the install folder on the linux cd its needs on the boot for installation

initrd.gz is the name of the file

---

### Post by abtabt on 2009-11-25
> **zonemikel said:**
> Ya i musta missed that step somewhere ... well it booted into linux install when i clicked linux this time ... im staring at the choose language thing, lets see how far i get ? 

Do i need to leave os9.2 on there ? i hope when i get something going maybe i can pull the drive out and dd it to another disk so i dont have to do this again, and maybe i can get some more space ... i have tons of 30 and 40 gig drives around

you always need macos when you use bootx but you can do a small partion like 
200mb and let linux use the rest

or install a second hdd

---

### Post by zonemikel on 2009-11-25
I took out the quantum fireball 4gig ... my plan is to dd the partition off of that and put it on a 4 gig partition on a 20 gig drive, then i will have enough free space ... not sure if the dd will go well though, have to make sure everything is right. ... bout to start it now

update.
Had to stick them both on the same ide cable, @ aprox 4MB/s it will take about 17 minutes to copy the whole thing over.

---

### Post by linuxopjemac on 2009-11-25
If you have another drive, I would use that to put Linux on (4 Gb is not a lot). I hope for you that MacOS will be able to "see" that drive otherwise you are in trouble and you have to tweak in the resource fork and stuff, unless your have a program called FWH Hard Disk Toolkit which can partition non-Apple drives. You can also install on the Apple drive but then you need to do repartition. Indeed a 200 Mb HFS partition for classic MacOS and the rest for linux.

---

### Post by zonemikel on 2009-11-25
Well the dd *seems* to be ok i just started the mac os 9.2 off the duplicate 20gig drive, but then the mouse and keyboard were not responsive ... not sure if the system was frozen because the mouse was moving during startup. Also sometimes when i start it the screen is shifted to the right about a inch and it just stays at a white screen with a nonblinking cursor in the upper left.

The bootX thing works on startup now too, I clicked the linux thing and it looked as if the install disk were starting but it gave me a garbled vout. Then i unchecked use video driver and then i got a kernel panic. 

Anyway i started mac os and then started bootx clicked linux and i'm installing again. If all goes well i should be able to install compleatly this time. I'm assuming i use the instructions on the link yall sent me under **"**Copying /boot to the HFS* System Folder" section. 

Well the partitioning thing just went through i used largest conigugu.... free space. I should have checked that hdd before doing this, at least if the hdd is bad i know what to do. I should have like 16gig hdd space for ubuntu. Actually its Xubuntu, not sure if that matters.

I'll update this post as i progress, i dont wanna double post a lot.

---

### Post by linuxopjemac on 2009-11-25
These old macs get their drivers for mouse and stuff from a few very small partitions (number 1-4). You can see it from the partition table. You only dd'ed the HFS partition on that other drive, so you miss those drivers,,,If you want all that you need to clone the whole scheme. Don't know if that is possible though...

---

### Post by zonemikel on 2009-11-25
> **linuxopjemac said:**
> These old macs get their drivers for mouse and stuff from a few very small partitions (number 1-4). You can see it from the partition table. You only dd'ed the HFS partition on that other drive, so you miss those drivers,,,If you want all that you need to clone the whole scheme. Don't know if that is possible though...

Yes i saw that ... there were four very small partitions and indeed gparted would not let me do anything with them. However this copied over those small partitions and the hfs partition just fine. 
sudo dd if=/dev/hda of=/dev/hdb bs=512
where hda was the mac hdd and hdb was the drive i was duplicating it on. When i looked at it after it was done it showed the partitions (all 5) exactly as they were on the mac hdd. 

I'm about 83% of the way through the installer. I got a red screen twice, i think it was unable to install a package because of bad cd or cdrom. I thought it would just download those packages, guess not. Its still chugging though though so it might work. 

I notice there are no usb ports on this machine. The keyboard/mouse i have for it is very crappy, is there an adapter i can get to use a normal pc keyboard or mouse ? A keyboard/mouse combo on ebay start at like $17, i'm not paying that much. 

its almost finished now . . .

---

### Post by zonemikel on 2009-11-25
Well after all that i got another red screen and it quit at "select and install software" I continued and did the rest of it, copied over the vmlinux and such now when i boot i get a disk icon with a blinking question mark which i know means no os. 

Guess i need to burn another cd and check it first ... I got to see wth is wrong with the hdd too, might have to dupe it again, at least its not the original :)

---

### Post by linuxopjemac on 2009-11-25
When you are finished you have to set the boot partition in BootX to the one you have in Linux, otherwise you boot from CD again. Take a kernel (something like vmlinuz-name) from the CD and copy this file to the kernel directory in the system folder as well as initrd-name.img) and select initrd-name.img as ramdisk. Hopefully you have a booting machine then.

I had this in more kernel arguments in the past:

```
root=/dev/sdb8 devfs=mount
```

---

### Post by zonemikel on 2009-11-25
> **linuxopjemac said:**
> When you are finished you have to set the boot partition in BootX to the one you have in Linux, otherwise you boot from CD again. Take a kernel (something like vmlinuz-name) from the CD and copy this file to the kernel directory in the system folder as well as initrd-name.img) and select initrd-name.img as ramdisk. Hopefully you have a booting machine then.

I had this in more kernel arguments in the past:

```
root=/dev/sdb8 devfs=mount
```

I'm really puzzled why i get the floppy with question mark icon ? I dont get a happy face or anything about mac ox 9.2  i followed all the instructions on the site and copied over the files like you say> cp boot/vmlinux hfs/System\ Folder/Linux\ Kernels/vmlinux
cp boot/initrd.img hfs/System\ Folder/ramdisk.image.gzall of it seemed to go ok. None the less why would any of this totally mess up the apple drive so it does not even find a os anymore ? Well its not the apple drive but the duplicate anyway. 

I'm duplicating it on another drive, writing a new cd at lower speed and i'm gonna try again.

UPDATE: 
I burnt a new cd and duplicated the apple drive onto another 10gig drive this time. I'm going through the install with the new cd, i'm gonna get it as far as i can and go play tennis for a few hours, maybe by the time i get back it will be mostly through.

I'm thinking maybe the installer somehow messed up the boot partitions on the mac drive ? If it does it again ill look at the drives in another pc and ensure that the filesystem is still ok

---

### Post by zonemikel on 2009-11-25
Well the other install cd gave me the same problems so i must have a bad download or something. I aborted the installation and when i restart i get the disk with question mark icon that means "cant find OS". Why just from attempting to install ubuntu and then canceling does it mess up the old filesystem so much that it cant even find the os ?  


I'm downloading yet another cd this one is "xubuntu-9.04-alternate-powerpc.iso" this will be the third cd yet ... I'll check the md5 and burn it on another machine really slowly, and try again for the last fing time. 

If i suceed in a install just to be greeted by a disk with question mark icon or it(I) fail again I'm going to take it outside and beat the hell out of it with a metal pipe.

---

### Post by tiresia on 2009-11-25
Don't loose your time trying with different cd's. It looks like they are ok.
If you can't boot in MacOS after installing, you can always just reset pram (Command-Option-P-R keys). It should work again.
Are you sure you installed the second hard disk correctly (slave/master - jumpering)? Maybe you need to jumper both correctly.

You must be patient and read instructions slowly - also because you can have still problems when you reboot in linux. But you will learn also a lot about linux world and how it works. It is not the easiest installation process...

---

### Post by zonemikel on 2009-11-25
> **tiresia said:**
> Don't loose your time trying with different cd's. It looks like they are ok.
If you can't boot in MacOS after installing, you can always just reset pram (Command-Option-P-R keys). It should work again.
Are you sure you installed the second hard disk correctly (slave/master - jumpering)? Maybe you need to jumper both correctly.

You must be patient and read instructions slowly - also because you can have still problems when you reboot in linux. But you will learn also a lot about linux world and how it works. It is not the easiest installation process...

I know linux, have been using it for a while, thats why i want to put it on this pc. I have also ran into this same problem before with cheep media and/or a messed up download of the iso. Really i should run the "check disk" before installing but i'm allways in too much of a hurry.

---

### Post by linuxopjemac on 2009-11-26
The problem could be that you didn't format that drive from withing MacOS, but just copied the data to it. Macs are built to not recognise non-Apple hardware...

---

### Post by linuxopjemac on 2009-11-26
The problem is that you are trying to install MacOS and Linux on a non-Apple hard disk. **Listen to me** and don't waste your time. If I were you, I would repartition the original 4 Gb HD into two partitions with a classic MacOS CD. One of 200 Mb in HFS for MacOS and the other one you can make Unix for example. The latter is not important as you will install Linux on that partition and the installer will recognise any kind of format. After partitioning you have to reinstall MacOS on the 200 Mb partition. You have to boot into your new MacOS system to see if it works. You also have that 20 Gb drive of yours which is non-Apple. This drive you will just use for data under Linux. You will install the Linux system on the 4Gb-200Mb partition. The big drive is going to be recognised in Linux only. The small drive you need to boot MacOS and Linux. The problem  with these old Macs is that you need MacOS to boot from, there is no other way. So, After you coupled the second drive, you reinstall Linux on the small drive just like you did before. After installation you change BootX to boot from the root  (root=/dev/sda6 or something). From within Linux, you format that big drive as ext4 and you will use that one to put data on. Maybe you can even set /home there if you are clever. Good luck.

---

### Post by abtabt on 2009-11-26
[QUOTE=zonemikel;8386825]I'm really puzzled why i get the floppy with question mark icon ? I dont get a happy face or anything about mac ox 9.2  

hi
hmm  if i get  question mark icon i will take the MACOS CD

and boot up and reinstall the driver

Sometimes will the linux install messup the driver 
that will give you question mark (not allways but some time (yaaboot))

---

### Post by zonemikel on 2009-11-26
Success !! 
Its not so much as the apple computer does not like "non apple" hardware its that it setup the partition table and then we go to install linux and mess it all up, then we restart and the mac is like wth happened to my partition table. 

So this is what i did ! 
I installed a second hdd where the zip drive was supposed to be using a multitap ide cable from a normal pc and some ingenuity. Then i started the install and installed to that hdd. After rebooting it didnt know where the root hdd was so i had to pass it the root=/dev/hdb3 option and then it worked I'm now looking at a login prompt for ubuntu !!! 

Also my cd rom drive was bad so i installed a new one, thats why i was getting errors when i was installing before. 

So, you could dd the drive but as soon as you mess with the partition table using the linux install disk you are screwed. Thats why you guys want to install linux then use the mac os disk again to install the mac os again, which also would have worked but i dont have a mac install disk :(

Anyway its working now.... im wanting to do a sudo apt-get install xfce4 but thats another story . . . 

thanks for all the help, i hope i can make something outof this machine.

---

### Post by zonemikel on 2009-11-26
i cant login ... it never made a user account ! 
If i give it the wrong root= argument it will give me a ash shell from there i can cat /etc/passwd and /etc/shadow I dont see my username in either one! 

How can i make a user using only ash so i can login ? Or is there a kernel argument that i can type into bootx so it will drop to root shell like in the "rescue mode" of ubuntu ?

---

### Post by zonemikel on 2009-11-26
> **zonemikel said:**
> i cant login ... it never made a user account ! 
If i give it the wrong root= argument it will give me a ash shell from there i can cat /etc/passwd and /etc/shadow I dont see my username in either one! 

How can i make a user using only ash so i can login ? Or is there a kernel argument that i can type into bootx so it will drop to root shell like in the "rescue mode" of ubuntu ?

nevermind ... i edited the /etc/shadow and /etc/passwd files manually using ash by doing stuff like 
echo 'stuff into file' >> /etc/shadow 
after mounting it using -t ext3 of course 
My keyboard is messed up and i cant type any strange chars beside numbers and letters so i found a online des encrypter (to not use the $1$) type options. .. 

anyway i logged in now, be sure to add yourself to the sudoers file ... i have to go do that

---

### Post by linuxopjemac on 2009-11-26
sudo adduser name
...

done

---

### Post by zonemikel on 2009-11-27
> **linuxopjemac said:**
> sudo adduser name
...

done
Well duh! thats if you can log in using another username or something. The only way i can get a prompt were 
1.) put a bad root=/bad/place option so it gives me a ash prompt
2.) boot from cd and get a ash prompt 

either way there is no "adduser" there isnt even "vi" so you have do do what i did. 

So is there anyway I can get X running on this ? I did sudo apt-get install xubuntu-desktop but afterwards startx has problems, mainily locking some authority file or something like that.

---

### Post by abtabt on 2009-11-27
[QUOTE=zonemikel;8392511]Success !! 


Q   So, you could dd the drive but as soon as you mess with the partition table using the linux install disk you are screwed. Thats why you guys want to install linux then use the mac os disk again to install the mac os again, which also would have worked but i dont have a mac install disk :(

A   hi

you dont need to reinstall macos only the driver (if you dont have 
the cd maby you have the the aid floppy ) 

this way that you done this install is not the easyeist way
and remember that is a OLD WORLD not supported but it can be done
even with 604 CPU 

Q QUOTE=zonemikel
  So is there anyway I can get X running on this ? I did sudo apt-get install xubuntu-desktop but afterwards startx has problems, mainily locking some authority file or something like that.

A.  have you any xorg.conf file ???? if you dont generate one


A   you can start in single mod by add single in the end of more kernel arg    in bootx  (then you can be root )

---

### Post by zonemikel on 2009-11-27
> **abtabt said:**
> [quote=zonemikel;8392511]Success !! 


Q   So, you could dd the drive but as soon as you mess with the partition table using the linux install disk you are screwed. Thats why you guys want to install linux then use the mac os disk again to install the mac os again, which also would have worked but i dont have a mac install disk :(

A   hi

you dont need to reinstall macos only the driver (if you dont have 
the cd maby you have the the aid floppy ) 

this way that you done this install is not the easyeist way
and remember that is a OLD WORLD not supported but it can be done
even with 604 CPU 

Q QUOTE=zonemikel
  So is there anyway I can get X running on this ? I did sudo apt-get install xubuntu-desktop but afterwards startx has problems, mainily locking some authority file or something like that.

A.  have you any xorg.conf file ???? if you dont generate one


A   you can start in single mod by add single in the end of more kernel arg    in bootx  (then you can be root )

Nope no aid cd either ... Its all working now X was not working because i had a screwed up user account. I fixed everything though. Xubuntu is working and it logs in and stuff, its just really slow. Also the sound is really low, i turn it up in the mixer and it does not go very high at all. 

I'm sure it would just be one hurdle after another for all the basic little things. I've set it aside for now. If it can emulate snes roms using a snes emulator then ill hook gamepads to it somehow and have it do that. However I wanted it as a snes station because of the built in speakers and nice sound, but the sound is so low that wouldnt work anymore. 

I spent three days doing this, including thanksgiving. I'm kinda tired of it now.

---

### Post by boprestoration on 2009-11-28
Wow, i have been living a parallel life to you. I too have spent the last 3 days doing this as well. I am working with a Blue White 450MHz Blue White with 480MB RAM. 

I have had some of the exact same issues that you have, and now i found this novel on here, i had to write in. I still don't have mine going, i will now reinstall Mac OS 9.2 and try BootX again. 

This has been a great learning experience, i have picked up enough tips now i think i can get this up and going this evening. I wanna use this old mac a test for audio recording. I am totally new to the Linux world. But not for long. 

If i have any problems i will post them here instead of starting a new thread, since this is exactly along the lines to what i am doing.

Jason

---

### Post by tiresia on 2009-11-28
> **boprestoration said:**
> I am working with a Blue White 450MHz Blue White with 480MB RAM. 

I have had some of the exact same issues that you have, and now i found this novel on here, i had to write in. I still don't have mine going, i will now reinstall Mac OS 9.2 and try BootX again. 

Your G3 is a NewWorld Mac, so you don't need BootX. Just boot from the CD pressing the C-key. If it does not work, you downloaded the wrong CD, or the CD is corrupted, or you burned it not correctly (use the Apple Disk Utility if you have MACOSX and burn it very slowly)

---

### Post by zonemikel on 2009-11-28
> **tiresia said:**
> Your G3 is a NewWorld Mac, so you don't need BootX. Just boot from the CD pressing the C-key. If it does not work, you downloaded the wrong CD, or the CD is corrupted, or you burned it not correctly (use the Apple Disk Utility if you have MACOSX and burn it very slowly)

Lucky . . .

---

### Post by boprestoration on 2009-11-28
UGH!!!

I really thought from all that i have read, that some of the G3's are oldworld and some are new world. I guess is should have been using a regular install disk then... 

I am still stumped on how the disk should first be prepared, do i need to have it formatted in a special manner, HFS* or i think there was a linux option i saw too. This is such a gray area, i swear i was crying blood 2 days ago, i know this would work somehow. 

Does anyone know of any video tutorials on metacafe or youtube, i have not found anymyself. but i am considering making one once i get this all figured out. 

I am going further with this later this evening, if i should post a new thread i will, or if anyone knows of an older thread that has a step by step procedure fore me please post a link on here. 

Thanks everyone, this is such a great board, hrs and hrs of reading here.

Jason

---


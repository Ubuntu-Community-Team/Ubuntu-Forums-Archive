---
title: "[SOLVED] Multiple OS installs and a Geforce 8800 question."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by mark_t50 on 2007-08-07
Hello,

I'm completely new to Ubuntu and Linux, and there is a good chance I might be trying to do too much for a first go, but basically I'd like to know if the following is possible please.

I would like to have a triple boot system with XP Pro, Vista 32bit and Ubuntu 32bit. My system specs are as follows: Asus A8N-SLI Premium, AMD X2 4400, 2gb RAM, BFG 8800GTX, 2 x WD Raptor 74gb SATA, 2 x 160gb WD Caviar SATA, Creative X-Fi Fatality, Dell 2407 monitor.

The first stumbling block I can see is my graphics card, I've already tried booting up from the 7.04 CD and it gets so far and then the screen just goes black forever. I've searched the forums and some people with the same card as me seem to have the same problem, so I suppose my first question is, given my graphics card, can I even get Ubuntu installed ? if so do I need to use the alternative CD or a different install method to get it started ?

Secondly, presuming I can work around my graphics card and get to the point where I can attempt an install, I'm really confused about what order to install the 3 OS's and if it is even possible, Ideally I'd like my system installed as follows:

1 x 74gb Raptor - Vista
1 x 74gb Raptor - Formated NTFS for use when booted into Vista.
1 x 160gb WD - Windows XP
1 x 160gb WS - Ubuntu

So I basically have each OS installed on it's own physical drive, is this recommended ? would I be able to do this and from a boot menu choose the OS I want to boot into ? Most importantly, what order do I install the OS's in is it: XP first, then Vista and Finally Ubuntu ?

Sorry this is a long first post, I'm just trying to get an idea as to whether what I'd like to do is even possible.

Thankyou.

---

### Post by cobrn1 on 2007-08-07
Hi and welcome to the forums!

To start with, I'm not sure about your graphics problems (I can only long for such a nice card... ;)), but the rest I may be able to help with.

That said, it might be possible to use the alternate install CD to text-based install, then use the commandline to download the newest nvidia-drivers and install them. Not quite sure how you'd do that, or if it's even necessary, so I'll let someone else advise you on that...

Anyway, you don't have to give each OS its own hard-drive, as long as they have their own partition. Also, linux requires a swap partition, and you might want an extra partition to which you can dump data from all the other OSs.

Anyway, you can have a max of 4 primary (or logical) partitions, or 3 primaries + 1extended which can be divided into many logical drives (which are basically the same thing, although vista doesn't like to be installed on a logical drive) on the harddrive (I think that's the right terminology. Basically, they turn the last primary into several new partitions - quite clever). If you need a tool to do this I reccoment the GParted CD if you're not doing the ubuntu-graphical install. If you have to use the text based installer then using this graphical tool to do the partitioning will make your life much, much easier - just google it and burn the .iso.

Given that you have 4 harddrives tho, you might as well use them...

My (humble) reccomendation is:

Raptor1 - Partition 1 - Vista (formatted as NTFS)

Raptor2 - Partition 1 - Format as Fat32 and use as a partition to share data between the OSs

WD1 - Partition1 - XP (formatted as NTFS)

WD2 - Partition 1 - Ubuntu (formatted as ex3)
           Partition 2 - /swap (1gig formatted as linux swap)


Id reccoment using the Gparted CD to do all your partitioning first, and then install in the order, XP, vista then ubuntu.

EDIT: when you install ubuntu it gives you the option of installing GRUB bootloader. Say yes and then you'll have GRUb, which will give you a choice of OS when you boot up. You can configure the timeout, default, order of the list, etc, but lest get you installed first, yes?!

Oh, and BTW, nice rig...

Hope I've helped. Hope you get your answers for the graphics question too. :D

---

### Post by mark_t50 on 2007-08-07
Thankyou very much for the reply.

I found that by booting from the CD in 'safe graphics mode' it would allow me to run through the install so I've kinda jumped in at the deep end tonight and just tried things to see what worked.

So far I've managed to get my system setup as follows:

Raptor 1 - XP
Raptor 2 - Vista
WD1 - Ubuntu
WD2 - nothing at the minute, but like the idea of a Fat32 for sharing stuff.

The problem I seem to be having is that after installing Ubuntu I reboot, but the only options I get on the boot screen are XP and Vista. I've done a bit of forum searching and so far I have installed EasyBCD 1.6 on Vista, however I'm struggling to add my Linux system. I think I need to tell EasyBCD what boot loader Ubuntu installed (if any, seeing as I just seemed to click 'forward' past most things on the Install) and what drive. I'm starting to think I might have to reinstall Ubuntu and pay more attention to the options this time :lolflag:

---

### Post by cobrn1 on 2007-08-07
interesting problem... did you install ubuntu last (and did it ask you to install GRUB?)

Are you using GRUB as the bootloader (it should say somewhere on the screen with the list of OSs)

Anyway, you might want to look up super grub disk, burn the.iso and run that. Lok through some of the documantation, but basically you can use it to restore GRUB to the MBR, and with any luck it'll pick up on all the installed OS and fix the boot up list.

---

### Post by BobCFC on 2007-08-07
I have an 8800GTS and it works great in Ubuntu if you use the drivers from the Nvidia web site. I have dual monitors working with all the 3D bling of compiz fusion!

Once you have installed Ubuntu the way you want it download the latest 32 bit driver [100.14.11]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run")

If you have tried the built in  Ubuntu restricted drivers you must remove them otherwise it will say Error API mismatch. If you have not you can skip this step: 

```
sudo apt-get remove nvidia*
```


Now to install the drivers reboot and choose recovery mode from the boot menu this will let you log into the   command line as root without the desktop.

change to the directory where you saved the drivers and type:

```
apt-get install build-essentials
```

This will install the c compiler, you only need to do this once not in future if you install new drivers. Then you can run 

```
sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```

note you can use TAB to auto complete you don't need to type all that 

Answer yes to all the questions. It will say cannot find match for your kernel do you  wan t to build your own choose yes and it will do it for you,  Just keep pressing OK it isn't hard.  It may complain about a missing .so file but it will be OK.   Choose yes to save changes to xorg.conf file and reboot.

When you next boot up in the desktop you can use the nice new control panel to change resolutions and setup dual monitors and stuff.  Type **gksu nvidia-settings**  at a terminal, and when done press the button to save changes to xorg.conf file.

---

### Post by cobrn1 on 2007-08-07
Excellent - I love it when the community gets together! :D

Try using the super GRUB cd to fix your booting problems, I doubt you'll need to re-install, but If you do have to it won't take long with a rig like yours. Just be careful to install GRUB to the MBR!

Then follow BobCFC's instructions and you'll be laughing!

---

### Post by mark_t50 on 2007-08-08
Thanks for the suggestions.

I seem to be struggling a bit with getting the bootloader working at the minute. I cannot get EasyBCD to work, even tried the 1.61 Beta (Although I'm sure it's me doing it wrong). 

I think I might be writing the boot loader to the wrong drive when installing Linux, because I seem to be in a position where If I change the drive order in the BIOS and set RAPTOR1 as the first drive I can boot into XP or Vista but not Ubuntu, however if I set WD1 as the first drive then I can boot into Linux but not XP/Vista.

At the end of the install options there is an advanced tab where it has HD1 as the drive for the Bootloader, do I need to change this to the same drive that the Vista bootloader is on ?

---

### Post by Ram0ne on 2007-08-08
Hi Sparky. :) 

Try booting from from your Ubuntu disk, 

Press F11 on the initial boot up.

Select your Ubuntu disk. 

Hopefully it will boot. 

Then check out this thread.

[http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html](http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html)


Ram

---

### Post by cobrn1 on 2007-08-08
I think all that matters is that GRUB is on the MBR of the first hard disk, and the menu.lst file that contains the listings recognises that the different OS's are on different harddrives, ie, hd0 and hd1, etc.

My best advice is to download and try the super GRUB cd - worked like a charm on my pc 9 times out of ten, (on attempt 10 pc pc was completely buggered up, so not the cd's fault...)

Then boot up the cd and follow the menu... It's reasonably easy to use, if you're unsure there is documentation on the web to help you. In any case it sounds easier than what you're trying to do with EasyBCD

---

### Post by skymera on 2007-08-08
nice card.
its a beast,.

mines at home in the box, itdosent fit right.
god dam dell.

but try the envy script for drivers.

if im on the wrong subjrct sorry.

---

### Post by igknighted on 2007-08-08
> **mark_t50 said:**
> Raptor 1 - XP
Raptor 2 - Vista
WD1 - Ubuntu
WD2 - nothing at the minute, but like the idea of a Fat32 for sharing stuff.

Ubuntu can read NTFS without issue, and there are drivers for WinXP (and possibly Vista, not 100% sure tho) to read linux's ext3 format.  FAT32 is just a bad file system.  It corrupts easily, has file size limits that are easily reachable (a ripped DVD for example could be too big, or a DVD iso), and fragments quickly.  I **strongly** recommend using linux's ext3 or NTFS in any kind of extra storage drive and never using FAT32.

---

### Post by cobrn1 on 2007-08-08
> **igknighted said:**
> Ubuntu can read NTFS without issue, and there are drivers for WinXP (and possibly Vista, not 100% sure tho) to read linux's ext3 format.  FAT32 is just a bad file system.  It corrupts easily, has file size limits that are easily reachable (a ripped DVD for example could be too big, or a DVD iso), and fragments quickly.  I **strongly** recommend using linux's ext3 or NTFS in any kind of extra storage drive and never using FAT32.

FAT32 has it's faults, granted, however,

1> reading from an ext3 partition in windoes is a pain and requires extra software... If you know of software that will mount the partition properly, then fire away, but the software I used allowed me to browse and copy files across, but wouldn't really be suitable for using to watch movies from...

2> the NTFS situation, I'm not 100% sure if the driver for read _AND_ write has been proved safe yet, but at the moment NTFS is still write-only.

This leaves FAT32 as the best file system that both can use...

You are right tho, NTFS and ext3 are far superior, just not useable right now. When the NTFS read/write driver goes gold, then you can convert to NTFS and wave bye bye to FAT forever...

---

### Post by Ram0ne on 2007-08-08
Mark, 

I've not read this yet but it may help.

[http://www.linuxformat.co.uk/modules.php?op=modload&name=News&file=article&sid=577&mode=thread&order=0&thold=0](http://www.linuxformat.co.uk/modules.php?op=modload&name=News&file=article&sid=577&mode=thread&order=0&thold=0)


Ram

---

### Post by igknighted on 2007-08-08
> **cobrn1 said:**
> FAT32 has it's faults, granted, however,

1> reading from an ext3 partition in windoes is a pain and requires extra software... If you know of software that will mount the partition properly, then fire away, but the software I used allowed me to browse and copy files across, but wouldn't really be suitable for using to watch movies from...

2> the NTFS situation, I'm not 100% sure if the driver for read _AND_ write has been proved safe yet, but at the moment NTFS is still write-only.

This leaves FAT32 as the best file system that both can use...

You are right tho, NTFS and ext3 are far superior, just not useable right now. When the NTFS read/write driver goes gold, then you can convert to NTFS and wave bye bye to FAT forever...

NTFS driver went final in March, it is fine and done.  It is a userspace only driver (so you cannot install linux onto it), but for the users needs (such as storing files) it is perfectly fine.  It is not a beta or anything like that.  I'm pretty sure it is now included in the kernel as well.

As far as ext3 in windows, I never had an issue with it.  The ext3 drive was listed as drive "L" (my choice, L for linux) and could be accessed like any other attached file system.  There were no slowdowns or anything.  Yes, you do need to install a 3rd party driver, but what doesn't require a 3rd party driver in windows?  I know many people who find ext3 so superior to NTFS that they install windows onto a small NTFS partition and then install all their apps onto the ext3 partition because its faster.  If gamers find it faster to use ext3 than NTFS in windows, I'll take their word for it, those people are insane about that stuff.

Link: [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
And: [http://www.fs-driver.org/](http://www.fs-driver.org/)

I do not remember which I liked better, but both should work fine.

---

### Post by cobrn1 on 2007-08-08
Cool, well if you're able to just mount an ext3 partition like a FAT of NFTS one, then go ahead and use ext3 for your sharing partition - as we both say, it's far superior to FAT, and now compatability issues seem to have been worked out, you'll have no problems.

So igknighted, id I understand you correctly I could now mount my windows partition read/write in feisty (and gutsy). Do you know if NTFS will be read/write by default in gutsy?

---

### Post by igknighted on 2007-08-08
> **cobrn1 said:**
> Cool, well if you're able to just mount an ext3 partition like a FAT of NFTS one, then go ahead and use ext3 for your sharing partition - as we both say, it's far superior to FAT, and now compatability issues seem to have been worked out, you'll have no problems.

So igknighted, id I understand you correctly I could now mount my windows partition read/write in feisty (and gutsy). Do you know if NTFS will be read/write by default in gutsy?

If it is not, it is only for philosophical reasons (ie, its proprietary).  I haven't tried Gutsy yet, but I don't see any technical reason why it wouldn't be included.

---

### Post by mark_t50 on 2007-08-08
Thanks again everyone for the help, it's much appreciated and I certainly have made some progress.

I now have managed to get my system setup so I can boot between all three OS's. I have no idea why it's working, I was trying all the suggestions posted on here along with others I'd found, to no avail. In the end I wondered if it was maybe the Nvidia RAID controller the SATA drives were plugged into, so I moved all 4 drives onto the sil 3114 controller on my motherboard. I spent an hour trying to get this to work and couldn't even get XP to install with the drives on the sil. So, I decided to plug all 4 drives back onto the nvidia controller and it just worked straight away! I've no idea if I maybe plugged the sata leads into different slots or what, but my system boots up to the GRUB loader and will let me boot into the OS of my choice :)

I'm just downloading all the updates for Ubuntu and will then have a crack at sorting out the graphics for my 8800. Looks like I also need to look into how to get a Creative X-Fi to work as it doesn't seem to pickup my soundcard :(

---

### Post by cobrn1 on 2007-08-08
Congrats and welcome to linux then!

I think someone posted the commands to install the nvidia-drivers. You could (if you were feeling lazy) look up something called envy, and this should do all the hard work for you, but it's probably safer just to use the commands previously poster.

Good luck with the sound card... Try doing a search on the forums or on google to see if you can find the answer. If not then you may want to start a new thread for it (as you're unlikely to get sound-card experts reading a dualboot and graphics thread). Best of luck!

---

### Post by igknighted on 2007-08-08
> **mark_t50 said:**
> Thanks again everyone for the help, it's much appreciated and I certainly have made some progress.

I now have managed to get my system setup so I can boot between all three OS's. I have no idea why it's working, I was trying all the suggestions posted on here along with others I'd found, to no avail. In the end I wondered if it was maybe the Nvidia RAID controller the SATA drives were plugged into, so I moved all 4 drives onto the sil 3114 controller on my motherboard. I spent an hour trying to get this to work and couldn't even get XP to install with the drives on the sil. So, I decided to plug all 4 drives back onto the nvidia controller and it just worked straight away! I've no idea if I maybe plugged the sata leads into different slots or what, but my system boots up to the GRUB loader and will let me boot into the OS of my choice :)

I'm just downloading all the updates for Ubuntu and will then have a crack at sorting out the graphics for my 8800. Looks like I also need to look into how to get a Creative X-Fi to work as it doesn't seem to pickup my soundcard :(

X-Fi's are notorious, Creative has refused to release any drivers for them.  I dunno if there are any ways to make the sound card work in linux, but if not, try this workaround:

I would get one of those cables that splits the sound (usually used to plug 2 headphones into one jack... like $2 at most stores) and have both your mobo's sound card and the X-Fi plugged in to the speakers.  This way you can have sound on linux, and still use your X-Fi in windows.

---

### Post by cobrn1 on 2007-08-08
> **igknighted said:**
> X-Fi's are notorious, Creative has refused to release any drivers for them. 

Some companies are just shitty like that... :(:mad: My advice, vote with your wallet next time and don't buy their stuff until they wake up...:)

---

### Post by bwtranch on 2007-08-08
Very interestin' series of posts. Makes a nice lab rat box. Too many things that can go wrong to be trusted in my opinion. My brother works for IBM and he won't have more than one OS per box period. Too many beans in the box:popcorn:

---

### Post by cobrn1 on 2007-08-08
> **bwtranch said:**
> Very interestin' series of posts. Makes a nice lab rat box. Too many things that can go wrong to be trusted in my opinion. My brother works for IBM and he won't have more than one OS per box period. Too many beans in the box:popcorn:

I dunno, I think the main complication was using several harddisks, not several OS. And as long as you're carful, and have recovery tools you'll be fine.

IE, please look up and download the super GRUB disc (follow like in sig to it's manual w/ link to download)... It's great! It has saved me a few times. If you have that, and a windows installation cd multi-OSs is really quite safe...

Maybe your brother is just lucky enough to have so amny computers (seeing as he works for IBM) that he doesn't need to dual/trip - boot. Lucky him :) :p

---

### Post by mark_t50 on 2007-08-08
I managed to get my 8800GTX working. I ended up using Envy, which was wonderful because it just seemed to do it all for me. I now have a wonderful desktop GUI at 1920x1200 with all the fancy 3d effects on :popcorn:

As for the X-Fi, I think I'm going to pull it out of this system, I've had nothing but trouble with the Creative drivers for Vista as well. I think I'll just use the onboard sound whilst I look for a nice card that works well in Linux and Vista.

I must say that I have had a few hurdles to overcome in the last 24 hours, but with the help of the wonderful community here it has been an enjoyable experience and I'm really looking forward to exploring the possibilities with Ubuntu. 

So, a big thankyou again to everyone.

---

### Post by SilverWave on 2007-08-08
Very pleased to see you have managed to overcome all of the problems :)

---


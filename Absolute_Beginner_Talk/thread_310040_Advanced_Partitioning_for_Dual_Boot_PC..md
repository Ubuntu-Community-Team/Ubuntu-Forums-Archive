---
title: "Advanced Partitioning for Dual Boot PC."
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by ImmigrantUS on 2006-11-30
Help me with partitioning for Dual Boot, please! 
 
  I will set up Dual Boot system Win98(no Internet access)/Ubuntu DD 6.06 LTS on 800 Mhz Celeron (P III class), 256 MB SDRAM, 40 GB IDE HD for my friend's kids. Reason for Dual - in School they use Windows, and I have games for it as well, and they'll see both worlds, also Ubuntu will be for Internet access (as Win 98 is not supported anymore).

   I've read most posts about Dual Boot and have general procedure understanding, but did not see my concern addressed... All recomendations for partitioning advise to put Windows on first partition, than put Ubuntu on other partitions, and make Shared FAT 32 partition for sharing files.
   But we all know that Windows will get bugged down to the point that it'll require reinstall of OS in awhile later... especially with kids beeing let loose on PC :). And common wisdom for advanced users is to put Windows OS on its own Partition, then make more Partitions for Documents, Programs, etc., so that in case of Windows OS necessary reinstall will not harm Docs, Progs, etc. Unfortunately I do not see this issue addressed in forums...

 :confused:  ? - what would be the best Partitioning practice with future Windows OS reinstall in mind? 
   Should I just simply put all Documents and Programs in "Shared" Partition? (I think it'll create problems, because if kids will  try to launch these Win programs from Ubuntu, they'll run into errors...).
   Or should I partition: 1)Win98 OS(Primary - FAT 32), 2)Win Programs & Docs (Primary? - FAT32) 3)"Shared"(Primary? - FAT32), 4)Ubuntu root(Primary/Extended(?) - EXT3), 4)Ubuntu swap(?-EXT3(?), or FAT32(?). 
 Do I also need Wndows 98 swap partition??? (and what should it be - Primary?)

 Is there a good way to do it?    Thanks in advance!

=====================================================================================
  *_**[COLOR="Lime"]Decision made[/COLOR]**_*: Install Win98 first, 10GB, FAT32, partitioning and formatting only enough for it and window's programs. Then install Ubuntu, using Gparted on Ubuntu CD  for partitioning and formatting remaining space: ~10GB for"/", ext3; ~ 2GB Linux swap; ~18GB for Shared Data partition, FAT32. Then - we'll see what happens ;-)   Summary:
  P1 - 10GB FAT32 Win98 + Progs,
          P2 - 10GB "/" ext3,
          P3 - 2GB Swap,
          P4 - 18GB FAT32 Shared Data.
=====================================================================================

---

### Post by SZorg on 2006-11-30
Personally I'd reverse that, I'm no expert (Although I've been taking classes at college), but I'd switch it to:

1) Ubuntu swap 2) Ubuntu Root 3) Shared (What format? [EXT3](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)?) 4) Windows Programs 5) Windows root

It should work, if you can partition it properly. Which would be:


Linux-swap, reiserfs/ext3, ext3/fat32, ntfs, ntfs?

---

### Post by Crakie on 2006-11-30
Your last suggestion seems ok to me. You do not explicitly mention this, but you do realize that you´ll need to make one extended partition, right?

Also, be aware that reinstalling Windows will screw up your MBR, so you'll need to reinstall Grub (or whatever bootloader you prefer) if you want the dual boot option back.

@SZorg: your suggestion favours Ubuntu in that the first part of a HD is a little faster. I have a bad experience NOT putting Windows first, though.

As for the two swap spaces, you can make the Windows one NTFS. I'd make the Linux one FAT32 in order to cross-use files.

---

### Post by ImmigrantUS on 2006-11-30
Thank guys!
 
 Win 98 is FAT32, so NTFS out of concern, and Win NEEDS 1st partition to work properly.

 I'm not sure if creating Win Data(Progs, Docs) partition will cause errors in Ubuntu, because it'll be FAT32 - same as "Shared" partition, and probably accessable from Ubuntu(?) :confused: 
 On the same note if I put Win Data(Progs, Docs) in "Shared" it might cause the same problems when accessed from Ubuntu..? But I hate to put all Win staff in a single partition... :confused:

  What is a best way?

---

### Post by bodhi.zazen on 2006-11-30
ImmigrantUS:

I wrote a brief guide to partitioning it may help

[Basic Partitioning](http://ubuntuforums.org/showthread.php?t=282018)

My advice is:

FAT 1 -> Windows c:\

FAT 2 -> Share. You will have no problems with shared windows programs here. HOWEVER, many programs in windows insist on installing into c:\ so it may be a moot point.

Swap -> Swap has it's own file system and in not ext2, ext3, vfat, etc.. it is swap.
Size = RAM X2

Ubuntu Root -> You can mount the FAT 2 as a shared drive.

This is a simple partitioning scheme and I see no obvious conflict with this. If you like to keep you windows programs separate, on the FAT 2 partition create a "Programs" folder for windows stuff, "linux" for linux stuff, and "share" for shared stuff (music perhaps).

HTH

:)

---

### Post by xabbott on 2006-11-30
The only thing you dont want on your Windows partition (or your /) is your data. Music, movies, pictures, etc. You shouldn't try to keep the windows programs on another partition. 
So all you would need is (windows  fat32)(/ ext3)(data fat32)(swap). A /home partition would be nice too.

---

### Post by ImmigrantUS on 2006-11-30
Thanks again guys!

  Bodhi.Zazen - I read your How To: Partitioning Basics and all links in it. Your guide is good, and helped me to understand partitioning better!  
 Yet on my newbie opinion (that's for who it's written for, right?) it needs some clarification:

 *_TYPO?_* - > Note: Some *_OS_* (Windows, BSD) can *_OLNY_*  *_by_* installed into a PRIMARY partition. ("_OSs_", "_ONLY_" and "_be_" intended, I guess)


 I) > Primary, secondary, and logical partitions.
 You mention "secondary" partitions in the heading, but no explanation below...

 II) In "Basic partitioning scheme" it would be much more helpful if there would be some sort of summary in the end with clear list - e.g.:
 A) For Linux only HD - P-n #1(info: specs - size, file type, etc), P-n #2 (info), and so on.;
 B) For Dual Boot (Win/Linux) - P-n #1(info), P-n #2 (info), and so on.;
 C) For Multi Boot Linux - P-n #1(info), P-n #2 (info), and so on.
 
 1 - ?  Understandably I need "/" and "swap" for Ubuntu, but did I get it right in "Options" that
"/home" or "/data" are additional partitions that I can create also, making it four Linux partitions total?
 2 - ?  If > "/home" can be backed up to "/data" does it mean that for every Linux distro I need separate "/home"? (I guess not, but if they use different DEs than probably need?)
 3 - ? If > /Data partition can be shared with other OS (Windows or other distro's) easier then /home. Than what file system it should have?
 4 - ? Since it is "/data" it'll probably be "Ext3"? and to share it with Windows there is a need for additional Linux program/utility - Which one?
 5 - ? I'm planning to create FAT32 "Shared" with Windows and Linux Data in it, will it be "as good" as "/data" or should I create both? - what way is better for sharing data between OSs?
 6 - ? Do I need additional Windows "Virtual Memory" ~ 2 GB Partition (Windows "swap- like") as some people recommend for increasing OS speed?

   III) Advanced partitioning - is absolutely unclear for me... (no wonder... :rolleyes:).
  Please tell us what system directory is.
 6 - ? Is it - /boot, /tmp, /var ?
 7 - ? How to give separate mounting point to them.
 8 - ? How to mount them and when, anyway?

   *_TYPO?_* - > Partitioning and formatting can be done *_form_* the CLI. (_"[U]from_"[/U] intended?)
 9 - ? What the animal is SLI? And how to handle it?

 10 - ? Is there "Multi Linux/Windows Partitioning guide"?
 That's what I'm planning to do on my own PC (AMD Athlon 1.8 GHz 2500 (Burton core), 1GB DDR, 120 GB PATA and 250 GB SATA). Already have Windows XP Pro, Ubuntu 6.10 EE, Linspire, Xandros and even Corel Linux discs. :D Planning to test ~ 10 distros, including Debian, openSUSE, FC 6, CentOS, PCLinuxOS, Mandriva(?) and Hikarunix ;).  

   Thank you again!!!

P.s. 1. Major problem with Internet development now, according to research, is user's stupidity, err  - ignorance... OK, lets just call me ignorant (for now):)
     2. Knowledge is relative - the more we know - the more we don't know..! (or - Stupidity never ends!.. Have fun fighting it!) :mrgreen:

---

### Post by bodhi.zazen on 2006-11-30
> **ImmigrantUS said:**
> Thanks again guys!

  Bodhi.Zazen - I read your How To: Partitioning Basics and all links in it. Your guide is good, and helped me to understand partitioning better!  
 Yet on my newbie opinion (that's for who it's written for, right?) it needs some clarification:

Like OMG thank you sooo very much for your review !

>  *_TYPO?_* -  ("_OSs_", "_ONLY_" and "_be_" intended, I guess)

Fixed....


>  I) 
 You mention "secondary" partitions in the heading, but no explanation below...

should read extended.... Fixed...

>  II) In "Basic partitioning scheme" it would be much more helpful if there would be some sort of summary in the end with clear list - e.g.:
 A) For Linux only HD - P-n #1(info: specs - size, file type, etc), P-n #2 (info), and so on.;
 B) For Dual Boot (Win/Linux) - P-n #1(info), P-n #2 (info), and so on.;
 C) For Multi Boot Linux - P-n #1(info), P-n #2 (info), and so on.

I thought it was a summary !

Let me ponder that, you see partitioning is an art and I'm just trying to introduce the tools :p
 
>  1 - ?  Understandably I need "/" and "swap" for Ubuntu, ....

Yes. A minimal install in Ubuntu (or any distro) requires two partitions. Root and swap.

Root is the linux = of c:\ and will now be referred to as /

Your root partition will then have several directories under /
/home
/usr
/var
/boot

> bodhi@Arch:~$ls /
etc  tmp  dev  media  root  sys  proc  sbin  usr  mnt  opt  lib  boot  var  bin  home  lost+found

> ... but did I get it right in "Options" that
"/home" or "/data" are additional partitions that I can create also, making it four Linux partitions total?

You can mount a partition as /home

mount /dev/hda5 /home

This is done with [fstab ](http://www.ubuntuforums.org/showthread.php?t=283131) (/etc/fstab)

```
/dev/hda5 /home auto defaults 0 2
```

and so on with /var /tmp ....

A data partition is typically mounted in /mnt or /media with links in home/user_name

>  2 - ?  If  does it mean that for every Linux distro I need separate "/home"? (I guess not, but if they use different DEs than probably need?)

Each distro needs a /home, but /home does not need to be a partition separate from /.

You can share /home across distors, but I advise against it.

See here for a discussion of why: [http://ubuntuforums.org/showthread.php?&t=300246](http://ubuntuforums.org/showthread.php?&t=300246)
[indent]See posts # 10 and 13....[/indent]

> 3 - ? If . Than what file system it should have?
 4 - ? Since it is "/data" it'll probably be "Ext3"? and to share it with Windows there is a need for additional Linux program/utility - Which one?
 5 - ? I'm planning to create FAT32 "Shared" with Windows and Linux Data in it, will it be "as good" as "/data" or should I create both? - what way is better for sharing data between OSs?

The easiest file system for sharing with windows is FAT as both Linux and windows read write FAT without any customization.

for ext2 or ext3 on windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

for ntfs on Linux: [ntfs-3g](http://ubuntuforums.org/showthread.php?&t=217009)

> 6 - ? Do I need additional Windows "Virtual Memory" ~ 2 GB Partition (Windows "swap- like") as some people recommend for increasing OS speed?

I do not know that one, Linux only here....

> III) Advanced partitioning - is absolutely unclear for me... (no wonder... :rolleyes:).
  Please tell us what system directory is.
 6 - ? Is it - /boot, /tmp, /var ?
 7 - ? How to give separate mounting point to them.
 8 - ? How to mount them and when, anyway?

That is why it is advanced !

I hope it is clear from what I have written above. The links in my guide go over the gory details :p

YOU DO NOT NEED TO DO THIS. In a nutshell this partitioning scheme is used for servers for security and other reasons.....

> *_TYPO?_* - . (_"[U]from_"[/U] intended?)

Arrgh..... Fixed

>  9 - ? What the animal is SLI? And how to handle it?

LOL :lol: CLI = Command Line Interface = tty1 (Crtl-Alt-F1 ; Ctrl-Alt-F7 to retrun to your GUI) or a terminal.

Some of us are addicted to the CLI :rolleyes:

>  10 - ? Is there "Multi Linux/Windows Partitioning guide"?
 That's what I'm planning to do on my own PC (AMD Athlon 1.8 GHz 2500 (Burton core), 1GB DDR, 120 GB PATA and 250 GB SATA). Already have Windows XP Pro, Ubuntu 6.10 EE, Linspire, Xandros and even Corel Linux discs. :D Planning to test ~ 10 distros, including Debian, openSUSE, FC 6, CentOS, PCLinuxOS, Mandriva(?) and Hikarunix ;).  

You're lookin at it :p

I use 10-15 Gb per distro with a large data shared partition.

You can share swap between distros as well !

>    Thank you again!!! 

LOL, no thank you.

Hey check out this: [http://ubuntuforums.org/showthread.php?t=282018&](http://ubuntuforums.org/showthread.php?t=282018&)

---

### Post by Crakie on 2006-12-01
Putting your Windows partition file on another partition but on the same drive decreases performance. On another drive speeds things up a little.

---

### Post by ImmigrantUS on 2006-12-03
OK, thanks guys! 
  Bodhi.Zazen, your tutorial looks good, will wait on partitioning, mounting summaries ;), and look at me - I'm already propelled to geek celebrity with your dedication! \\:D/ Now, with dual boot system, am I entitled to double geek status? (OK, OK, lets just call me less ignorant :-#).

   After reading and advise received - *_[COLOR="Lime"]Decision was made[/COLOR]_*: Install Win98 first, 10GB, FAT32, partitioning and formatting only enough for it and window's programs. Then install Ubuntu, using Gparted om Ubuntu CD for partitioning and formatting remaining space: ~10GB for"/", ext3; ~ 2GB Linux swap; ~18GB for Shared Data partition, FAT32.
 Summary: P1 - 10GB FAT32 Win98 + Progs,
          P2 - 10GB "/" ext3,
          P3 - 2GB Swap,
          P4 - 18GB FAT32 Shared Data.
---------------------------------------------
 Now fun part - [COLOR="Red"]**Dual Install**[/COLOR]:

  I.***_ [COLOR="Blue"] Windows 98 install [/COLOR]_*** ...painful...:rolleyes: Had to use DOS interface, forced by Win98 CD (!) to partition new drive, and then format. ] After that could not start install, because was forced to prompt again A:\   
  Somehow was able to come up with SETUP command, and it started to install...
   After total of 5(!) necessary reboots and more goofed ] reboots(because PC was set up to boot from CD, and every reboot was going back to command prompt... until I accidentally #-o  figured out that I need to open CD tray during boot, so it'd start booting from HD, then put CD back in to continue install...) -> Windows98 installed... =D> Rebooted OK.
 *_Except_*, lost sound in Windows (in Ubuntu OK), and display resolution went down to 640x480 with 16 colors... And I cannot increase it, changed monitors, checked BIOS (found nothing on it there), can't change it thru control panel... Probably lost driver...
 
 [COLOR="Red"]?[/COLOR] - By the way, how to check display resolution in Ubuntu?

   II.***_[COLOR="Sienna"] Ubuntu install !!![/COLOR]_*** !!!Pleasant!!! Nice GUI all the way, with only one final reboot!!! :-({|= Althou lighter color scheme I'd like more - will change. Overall looks awesome - I love it already!!! GRUB is working fine also, booted to both OSs several times!
 Was glad to see games for kids included!

 [COLOR="Red"]?[/COLOR] - Where can I get more games, preferably board( checkers, chess) and educational for kids?

 Only scary part was before partitioning. Because CD warns about all data loss during installation, yet it starts to install without any assurance, that it's possible to partition HD and put Ubuntu on remaining empty space, BEFORE any possible data loss may occur. It has thou statement, that you'll see a summary of changes ...
  I'm sure that lack of clear assurance put off some people, and made them quit Ubuntu install out of fear of data loss... I proceeded only because of extensive reading and familiarizing ahead of install, but not everybody will have possibility to do it.
   Partitioning with Gparted went fine, but althou it detected first FAT32 partition, it did not indicated that it has Windows.
  More upfront info on mounting would be nice too. Mounting of partitions on directories seems counter intuitive for me newbie. Would be more logical opposite - mounting directories(info) on partitions (physical parts of HD), but it was already prearranged, went fine as well.
   
 _*Except*_ fourth partition (18 GB Fat32 Shared Data) was not showing any mounting info, and as I found later was not formatted (maybe my fault?). Windows started to tell me that Partition D:\ is not formatted, and I Ok'd formatting it, and now running scan check.
   Another strange(?)thing is - I have HD icon signed Windows on Ubuntu desktop!?...:confused: Is it how it suppose to be? When I open it, there are Ubuntu icons inside on Windows folders.
 
 [COLOR="Red"]?[/COLOR] Should I delete this Windows HD icon form Ubuntu desktop? I think it will not be possible to run Win programs in Ubuntu without additional program(Wine or ?) right?

  [COLOR="Red"]?[/COLOR] -  Seems that if I install Win program and reboot strait to Ubuntu (not switching into Win on time in GRUB), than it puts Window's program icon on Ubuntu desktop. Is it normal behavior?

   Thank you everybody!

---

### Post by gn2 on 2006-12-03
Seen this? [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by ImmigrantUS on 2006-12-03
Thanks Gn2! 
 I'll need to read it over when I'll start working on my own multi boot PC - two HDs (SATA & PATA), Win XP Pro + Ubuntu + other linuxes.
  ? - SATA is OK for EE 6.10 ?

---

### Post by bodhi.zazen on 2006-12-03
gn2: Hi gn2, good to see ya

ImmigrantUS: Welcome, you made it !

Now you know why I laugh at all those who complain that Ubuntu is oh so hard to install and it should be more like windows !

---

### Post by ImmigrantUS on 2006-12-03
Hey body Bodhi.Zazen, would you please look in my post #10 here, and if you have time maybe even answer my questions.

    Thank you!

---

### Post by bodhi.zazen on 2006-12-03
> **ImmigrantUS said:**
> Now, with dual boot system, am I entitled to double geek status? 

No, I am afraid booting Linux only qualifies you a a geek :p
[indent]Bash scripting = doubble geek[/indent]
 

> ... lost sound in Windows (in Ubuntu OK), and display resolution went down to 640x480 with 16 colors... And I cannot increase it, changed monitors, checked BIOS (found nothing on it there), can't change it thru control panel... Probably lost driver...

LOL :lol: you need to install a windows driver or two....

Contact your manufacturer or see if you have some kind of a system restore disk...

> By the way, how to check display resolution in Ubuntu?

System -> Preferences -> Screen Resolution

>  II.***_[COLOR="Sienna"] Ubuntu install !!![/COLOR]_*** !!!Pleasant!!! - Where can I get more games, preferably board( checkers, chess) and educational for kids?

[Enable some repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

In a terminal, open synaptic, search for games....

> Only scary part was before partitioning. Because CD warns about all data loss during installation, yet it starts to install without any assurance, that it's possible to partition HD and put Ubuntu on remaining empty space, BEFORE any possible data loss may occur.

That was you warning...

Although rare, data loss can occur with resizing of partitions. The Install of Ubuntu should not cause data loss beyond partitioning....

> More upfront info on mounting would be nice too. Mounting of partitions on directories seems counter intuitive for me newbie. Would be more logical opposite - mounting directories(info) on partitions (physical parts of HD), but it was already prearranged, went fine as well.

Yes, I agree this is not intuitive, but it is not so hard once you learn the syntax....

> _*Except*_ fourth partition (18 GB Fat32 Shared Data) was not showing any mounting info, and as I found later was not formatted (maybe my fault?). Windows started to tell me that Partition D:\ is not formatted, and I Ok'd formatting it, and now running scan check.
   Another strange(?)thing is - I have HD icon signed Windows on Ubuntu desktop!?...:confused: Is it how it suppose to be? When I open it, there are Ubuntu icons inside on Windows folders. Should I delete this Windows icon form Ubuntu desktop?

Yes, that is normal behavior. No, do not delete the desktop icon. It should automatically go away when you un-mount your windows partition....

If you prefer, you can [edit fstab](http://www.ubuntuforums.org/showthread.php?&t=283131) and either not auto mount the partition at boot time or mount it in /mnt rather then /media....
 
> I think it will not be possible to run Win programs in Ubuntu without additional program(Wine or ?) right?

Correct, Linux will in general not run windows programs. Wine is a possibility but will take some work....

[How to wine](http://doc.gwos.org/index.php/HowToWine)

> Seems that if I install Win program and reboot strait to Ubuntu (not switching into Win on time in GRUB), than it puts Window's program icon on Ubuntu desktop. Is it normal behavior?

Not sure if I am following you there :confused: but I agree it sounds strange.....

---


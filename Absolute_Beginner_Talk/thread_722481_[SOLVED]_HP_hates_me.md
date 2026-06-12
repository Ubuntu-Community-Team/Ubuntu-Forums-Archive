---
title: "[SOLVED] HP hates me"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by zaivala on 2008-03-12
I have attempted to install OpenSuSE or Kubuntu on my computer for a total of 4 attempts.  I know, I should have learned the first time, but...

When I get it installed, my computer's HP software detects that the MBR has been altered, and then looks at my Windows Registry and sees that it has been changed from initial installation.  (DUH, like who wants AOL on their computer)  It then wipes the MBR and makes me insert the Installation disks to re-install all the crap I uninstalled, and since that changes the Registry I then have to reinstall all the non-HP programs I had running (like antivirus, Firefox, etc.) to restore their Registry entries.

I then have my Windows back, and Linux installed -- but no bootloader to get to Linux.

If anyone knows a way to turn off the HP detection software -- or a way to run the bootloader from a CD, which is not the preferred fix -- please let me know.

System Info:  I have an HP Pavillion a1020n, 3.04 GHz, SATA 200 Gb hard drive, a measly 512 Mb of RAM, with lots of USB, firewire, card-reader ports and a DVD+/-RW and CDR drives.

Moss

---

### Post by wednesday allfather on 2008-03-12
Is there a little partition at the beginning of the HDD that HP made?  Where is the MBR stored, that HP sofware can diagnose and fix MBR?  (I use the word "Fix" very loosely here)

Maybe you are booting to that partition.  Maybe HP hates you.  They seem to hate lots of Linux users.   

If you are booting to some kind of special, Window's lovin' partition, I would back the partition up and delete it.  You can always get back with Puppy Linux or something.

---

### Post by neurostu on 2008-03-12
Wow that sucks.  

If you have the time and the patients the easiest thing I believe would be boot into GParted and delete all your partitions. Then create a WinXP partition then create a Linux partition.

Reinstall winxp to the win partition. 
Reinstall ubuntu to the linux partition.

This will fix any HP related problems you have, granted it will also require that you do a complete windows reinstall which can suck.

---

### Post by zaivala on 2008-03-12
Nice thought, but... reinstalling XP would mean loading the Setup disks, which would set up the same software/hardware configuration I'm fighting now.  Loading a separate version of XP would take away all my motherboard drivers, which are not downloadable, and would cut way back on what I can do on my computer (including the DVDRW).

What I'm hoping is that someone has experience fighting with this, and knows something in Setup (at bootup) that I can disable, ending the problem.

As I said earlier, perhaps not as clearly as I should have, I get my partitions just fine, and it doesn't delete my Linux files... just wipes the bootloader from the MBR and then messes up my Windows installation.  after fixing my Windows, I wind up with working Windows, and a fully-installed Linux but no way to get to it.  So using GPartEd would not change anything.  IMO

Moss

---

### Post by neurostu on 2008-03-12
What you can do is use the windows boot loader to load lilo or to load into linux directly. this way you're mbr isn't changed

MBR --> Windows boot loader --> both Xp and Ubuntu.

You might want to look at these
[http://highlandsun.com/hyc/linuxboot.html](http://highlandsun.com/hyc/linuxboot.html)
[http://ubuntuforums.org/showthread.php?t=151454](http://ubuntuforums.org/showthread.php?t=151454)
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

Using the windows boot loader is rare but people sometimes do (when they want to preservere some hibernation features in windows) so you should be able to find some documentation

---

### Post by zaivala on 2008-03-14
OK, so I assume from all this that nobody has the generation of HP that I do, and has no information that I'm asking for.  It should be something I tweak in Setup, not an arcane workaround.  Well, I was hoping.

---

### Post by smurphy_it on 2008-03-14
I don't have anything like that, but need to ask.  After you get Ubuntu installed at what point does the HP software kick in and state that it found a change in the MBR and Registry files.

If this is happening before loading any Operating System, it is something in the bios (unlikely).  If it happens in windows, then it is a program installed in Windows (by HP) which is looking for changes to the Master Boot Record and windows Registry files.

That being said, it is possible to remove the HP software using Add/Remove programs, typing MSCONFIG in the run dialogue and seeing what is loaded under the Startup tab, or by downloading Hijack this! and see what is loaded.

Note:  It could be something loaded as a Windows service by HP.

I'd recommend using MSCONFIG's startup and with the help of google you should be able to find out which process is doing this.

---

### Post by alphaniner on 2008-03-14
> **zaivala said:**
> OK, so I assume from all this that nobody has the generation of HP that I do, and has no information that I'm asking for.  It should be something I tweak in Setup, not an arcane workaround.  Well, I was hoping.

Whatever is activating the 'fix' can't be on your HDD.  If it were, overwriting the MBR would effectively neutralize it.  There must be another module on the mobo that activates the 'fix.'

Have you checked your BIOS thoroughly?  Have you tried contacting HP customer support, gone to their website or forums?

edit: I got the impression this was happening during boot.  If it happens while in windows then nevermind.

---

### Post by zaivala on 2008-03-14
Smurphy, it detects the change at the next reboot, i.e., as soon as Linux is done installing.  No bootloader, and I'm directed to insert the Setup Disk 1.

alphaniner, HP Tech Support informs me that they DO NOT SUPPORT LINUX on this machine, and refuse to talk to me.  I have not checked the BIOS "thoroughly", I'm not familiar enough with it to know what I'm doing and could easily F* up my whole system trying things... was hoping someone with experience with this model or similar could help.  I have seen (in a Google Search) that I'm not the only HP user with SOME problem loading Linux, was hoping to find someone with THIS problem.

Moss

---

### Post by smurphy_it on 2008-03-14
If it's fixing the MBR on the next reboot (before loading an Operating System) it could be something stored either on a chip on the motherboard forcing the check, (like in the BIOS) or a specialized boot loader.  HP is famous for having a restore partition on the hard drive as well (sometimes hidden, sometimes not). The specialized boot loader could be redirected to ask for the Setup disk to fix the change.

I'd reset, power off/on your computer and go into it's setup.  Usually it's displayed on the screen.  Alot of times it's like hit F1, F2, F10, F12, etc... sometimes it's a key sequence.  It's usually printed on the screen.

Once you get into the BIOS, just browse around looking for anything dealing with Master Boot Record Protection, Anti-VIrus protection, boot loader protection etc....  If/Once you find it, change it to Disabled, then save your settings and reboot.

---

### Post by wirelessmonkey on 2008-03-14
Also, those HP desktops come with an app called "HP RECOVERY SOFTWARE SUITE", which sounds like it may be the source of your problem.  After getting Windows back in order, use Add/Remove programs to remove it, and you'll probably be a lot happier.

---

### Post by jeffus_il on 2008-03-14
I wonder if you have a lawsuit against them for forcing you to use Windows on a machine you purchased from them. It's something like Ford forcing you to drive around with your grandmother in the car every time you go out.

---

### Post by artilec on 2008-03-14
I know people that have had to pay for these recovery disks as they didn,t come with the computer originally.  U paid for your xp licence but dont get the disks!!! Pants!!!

---

### Post by zaivala on 2008-03-14
smurphy, thanks for the tip, but I'm sorry to say that I found nothing in my BIOS that intimated that my guessed diagnosis (MBR protection) was correct.

Maybe it's a problem with Kubuntu writing to an SATA disk?  I have read of others with my machine that did not have that problem... maybe I need a newer version of Kubuntu?  just guessing around, hoping to hit something.

---

### Post by artilec on 2008-03-14
If all else fails you could try this [http://wubi-installer.org/](http://wubi-installer.org/) for the meantime anyway!!

---

### Post by zaivala on 2008-03-14
wirelessmonkey, I don't show that HP Recovery in my Add/Control Programs.  I deleted a couple of other HP programs I wasn't using.  I own the setup disks... so I suppose it is safe to delete the HP Recovery files...?  I think there is a separate partition for some of this stuff... I'm smart enough to know how to do this, and dumb enough to be afraid to... I've certainly dicked up systems before by deleting "unnecessary" files...

Moss

---

### Post by zaivala on 2008-03-14
Naw, it's more like Ford forcing you to use regular gasoline even though you have a flex-fuel car, because they don't support flex fuels...  or they void your warranty if you put a different engine in the car...  nice try though

---

### Post by zaivala on 2008-03-14
LOL I downloaded the installer, and Windows reported an error loading it.  I'll try again later.

BTW, my HP Recovery stuff is the whole D: partition... I'm about to use GPartEd to wipe it... hope it's not the wrong thing...

---

### Post by por100pre1 on 2008-03-14
Please read [this]("http://ubuntuforums.org/showthread.php?t=585703"). I install Ubuntu installing GRUB in the Ubuntu partition and then using EasyBCD. Check this post:

[http://ubuntuforums.org/showthread.php?t=544013](http://ubuntuforums.org/showthread.php?t=544013)

---

### Post by artilec on 2008-03-14
ignore this post

---

### Post by zaivala on 2008-03-14
GPartEd is still working... the weird thing is the HP Recovery partition is labeled as D: but it's AHEAD of the C: partition... so it really COULD intercept changes prior to Windows loading on C:.

I deleted the HP Recovery partition, and GPartEd spent about an hour growing the C: partition to include the deleted space... then started over, saying it will take about 2 hours...  I hope I didn't just dick up the whole system.

Another user says he used this model to set up Ubuntu, but did NOT set up dual-booting.  The problem I see with that is that I would have to purchase video and sound cards, since this motherboard has some excellent video and sound built in but they will not run without the drivers, which are Windows specific.

Ah well... I'll let you know what happens.  I am afraid I'll have to run Setup again, and just forget about Linux for now.

Oh yeah... I have an old computer, an eMachines that works ok for the most part, and I'm using that to write this message.

Moss

---

### Post by zaivala on 2008-03-14
> **artilec said:**
> If all else fails you could try this [http://wubi-installer.org/](http://wubi-installer.org/) for the meantime anyway!!

the article you reference here regards Vista... I'm running XP...  is it still valid?

---

### Post by artilec on 2008-03-14
Yes It works on XP,  letme know how u get on!   sorry I cant help u more.

---

### Post by zaivala on 2008-03-14
Well, my fears were realized.  GPartEd finished the job "successfully", I rebooted, and got the following message:

Windows could not start because of a computer disk hardware configurations problem.
Could not read from the selected boot disk.  Check boot path and disk hardware.
Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.,


The most interesting part of that is that the only documentation I got with this system was on the hard drive... hard to check documentation.  Anyhow, here we go loop de loo...

Moss

---

### Post by fourscore on 2008-03-15
> **zaivala said:**
> ...
I then have my Windows back, and Linux installed -- but no bootloader to get to Linux.
...


Once you get to this step try this .
1. Reboot the computer with the kubuntu LiveCD.
2. Run GParted and note down the partition number where  Kubuntu is installed  for eg. sda2 or sda3 
3. Open the Terminal window and type
     -  sudo grub  (enter)
     -  root (sd0,partitionnumber)   (enter) -  note if  Kubuntu is on partition say 2 you need to enter1   and if it is on partition 3 you need to enter 2 and  so on.
     - setup (sd0,partionnumber)  (enter)  - similar note on partition number as above.
     - quit
4.  Next we need to get the  Linux bootsector info 
5. Reboot the computer and enter windows
6. Download bootpart  from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
7. Follow the instructions to add the linux bootsector info to the windows bootloader. Note ensure that the filename you give to the linux bootsector info is not more than 8 characters.
8.  You should be able to dualboot now

The above steps worked for me many a time to recover after some screwups.

---

### Post by fourscore on 2008-03-15
My prev reply was based on the assumption that you are running XP.  If you are running vista then search for info on dual boot setup for vista & linux.

You can avoid steps  1 to 3  by  installing the grub to the kubuntu partition  directly at the time of install instead of  disturbing the  MBR.

---

### Post by stalkingwolf on 2008-03-15
try this.  In windows click Start > Run,  then type in msconfig > OK
when msconfig opens click startup.    look for the hp thingy , probably under "services".
uncheck it , click OK  and reboot at prompt.

Hope that helps.

---

### Post by zaivala on 2008-03-15
> **stalkingwolf said:**
> try this.  In windows click Start > Run,  then type in msconfig > OK
when msconfig opens click startup.    look for the hp thingy , probably under "services".
uncheck it , click OK  and reboot at prompt.

Hope that helps.

Thanks, I'll check that when I get my machine restored from my previous exploits... on Disk 6 now...

Moss

---

### Post by zaivala on 2008-04-28
It may (or may not) be slow, but Wubi successfully installed K(4)ubuntu on my machine.  I don't know how they did the bootloader without running up the red flags the HP software has been looking for, and it's all in the Windows partition, but it's here and I can finally begin to learn how to use it.

Thanks for all your comments.  I lost a ton of data going through the mess described above, but fortunately recovered major chunks of it (thanks to emailing things to people and saving the emails...)

Hugs,
Moss

---

### Post by zaivala on 2008-05-24
> **zaivala said:**
> It may (or may not) be slow, but Wubi successfully installed K(4)ubuntu on my machine.  I don't know how they did the bootloader without running up the red flags the HP software has been looking for, and it's all in the Windows partition, but it's here and I can finally begin to learn how to use it.

Thanks for all your comments.  I lost a ton of data going through the mess described above, but fortunately recovered major chunks of it (thanks to emailing things to people and saving the emails...)

Hugs,
Moss

Just in case anyone is reading this and making a choice of what (or how) to install... I want it known that KDE4 is NOT ready for prime time.  The system dragged horribly and didn't have enough things that worked.  I uninstalled and reinstalled using Ubuntu (Gnome) and have been mostly thrilled ever since -- things run faster than Windows, even though I'm in a Windows folder formatted NTFS.  (For instance, PySol takes about 15-20 seconds to load using a Windows version in Windows XP, less than 5 seconds using the Linux version in Ubuntu through Wubi.)

Moss

---


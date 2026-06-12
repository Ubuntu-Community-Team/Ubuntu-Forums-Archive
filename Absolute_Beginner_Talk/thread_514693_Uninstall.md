---
title: "Uninstall"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by gbala on 2007-08-01
I don't know what happened to ubuntu i was trying to install my graphic card in my system i found a way to do that in a url and i blindly follow the step in the website url [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) after that i notice my desktop effect was not there and even the effect they specify is not working after that i try rebooting my system it dosent happened but my other os windows xp was working fine. And then i try to boot my ubuntu from cd even that was not happening it was saying some of the file was not able to load.
i don't know how to  uninstall the ubuntu from my system 
Is there any way to uninstall or repair my ubuntu without affecting my other OS...
Plz help me

---

### Post by aquavitae on 2007-08-01
What graphics card do you have?
What file does it say won't load - what's the exact error message?
How far does it get before stopping?

---

### Post by carloslosgrande on 2007-08-01
The simplest way to uninstall is to delete the partition its on, [COLOR="Red"]BUT[/COLOR] that will also delete GRUB which points to MBR which points XP, [COLOR="Indigo"]so you won't be able to access any OS[/COLOR]
Have you tried using the live CD in safe mode?

It sounds like there's a problem with X

I've had this problem from time to time, ie whenever I try to use the 'desktop effects'.( My video card is an ATI and it doesn't play well with some others).

If you can get to a terminal screen, try 
```
cd /etc/X11
``` then copy your current setup ```
sudo cp xorg.conf xorg.conf.old
```
and then run ```
sudo dpkg-reconfigure xserver-xorg
```
You'll probably be in root there anyway so you may not need 'sudo' in front.
just keep the defaults.
If you are using Feisty, you'll find the video card drivers in >system>administration>restricted drivers manager.
hope this helps
Go slowly.

---

### Post by gbala on 2007-08-01
I am having inbuild graphiccard ATI express200 when i try booting it says instaling the kernel and then it show some undifined mount and get stopen, then i tryd with the CD even that fails so i am not atall able to enter my ubuntu even i tryed safe mode no use

---

### Post by aquavitae on 2007-08-01
Can you post the exact error message you get when it stops?  It would be helpful if you could post everything thats on the screen when it stops.

---

### Post by carloslosgrande on 2007-08-01
[FONT="Comic Sans MS"]On a normal start-up, after the kernel loads, and you get the undefined mount, try pressing the 'alt' and 'f2' keys together.
This may take you to a terminal where you can sign in and then carefully type this;
> sudo dpkg-reconfigure xserver-xorg[/FONT]

---

### Post by gbala on 2007-08-01
i don't know what happened to my system..... 
i try all your ways but no improvement...
so i try to uninstall it from my windows and then my boot file was crashed so there was no way i reinstall my xp also  but now i try install ubuntu7.04 but strange the same problem...
i selected running my ubuntu from my cd...
it first said loading the kernel then it shows the loading bar of the ubuntu then
it shows the message as follow

BusyBox V1.13(Debain 1:1._3-3 ubuntu3) Build in shell(ash)
Enter 'Help' for a list of build in commands

/bin/sh: can't access tty; job control turned off (initramfs)
[35.863818] ata1.00: failed to set XFermod(err_mask=0x4)
[71.317191] ata1.00: failed to set XFermod(err_mask=0x4)
[106.778539] ata1.00: failed to set XFermod(err_mask=0x4)

Plz any one help what to do... do i need to set any of my BIOS setting...???:confused::confused::confused:
i want ubuntu in my system....
Plz help me

---

### Post by aquavitae on 2007-08-02
Whats the current state of your system - do you have xp installed?  Its weird that you can't run the cd though - did you have any problems last time you ran it?  Try it with safe graphics mode (from the cd boot menu).

---

### Post by anewguy on 2007-08-02
If you really want to delete Ubuntu, follow this guide:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

:)

---

### Post by gbala on 2007-08-02
I installed Xp there is no problem with that Xp is working fine but when i try installing ubuntu  from CD it gave me that error i tryed safe mode but the same error.... When i was installing Ubuntu first time with the same cd there was no problem....

---

### Post by carloslosgrande on 2007-08-02
Maybe you could download and burn another copy of the Live CD.

---

### Post by gbala on 2007-08-02
I cant understand your answer if i burn two copy of CD it will not work or what...???
or you are asking to download a nwe copy and try...???

---

### Post by carloslosgrande on 2007-08-02
[FONT="Comic Sans MS"]Sorry to take so long.
Yeah, I think you should try downloading a NEW copy and burn it to another cd.
It sounds like you have XP running just fine, yes?
You've followed the instructions here without any result, yes? then it_ may_ be that there is something wrong with your cd (did you check it? The site you downloaded from should have details about this.) and so your install is unstable.
I know it takes a while but it may be your best option..[/FONT]

---

### Post by anewguy on 2007-08-02
I agree with carlosgrande - download the ISO for the LiveCD again and burn it to a new cd-r (not rw - that way you don't have to worry about accidently messing it up later).

I would also add a couple of things:

In Windows, go to control panel/administrative tools/computer management.  When the computer management screen is up, click on disk management on the right hand side.

This will open a window where you can see your hard drive and the partitions/free space on it.  I would be sure that outside of the Windows partition(s) that no Linux partitions (ext3, swap, etc.) show - if they do delete them.  Then exit back out to the Windows desktop.

Put the new LiveCD in your drive and reboot.  It should come up with no problem.  When you go to install, select manual for the partitioning, and reverse where your old LInux partitions were - i.e., if the swap was first, put the ext3 first, being sure to leave enough free space for your swap to follow it.  It may sound a little crazy, but at least that way you can't have old data hanging out that could interfere.  Also be sure that the format option is on for the new Linux partitions before going forward with the install.

Once you've done all of that, post back here with the results - hopefully good!:)

---

### Post by gbala on 2007-08-02
Ok Thanks for your replays i will download a new vertion and try installing and get back to you soon

---

### Post by aquavitae on 2007-08-02
> **anewguy said:**
> This will open a window where you can see your hard drive and the partitions/free space on it.  I would be sure that outside of the Windows partition(s) that no Linux partitions (ext3, swap, etc.) show - if they do delete them.  Then exit back out to the Windows desktop.
Windows doesn't believe in linux, so the partitions won't show up as ext3, etc.  If they sow up at all they will be "Unknown partition", but on my computer at the moment, windows shows them as unpartitioned space.

---

### Post by anewguy on 2007-08-02
> **aquavitae said:**
> Windows doesn't believe in linux, so the partitions won't show up as ext3, etc.  If they sow up at all they will be "Unknown partition", but on my computer at the moment, windows shows them as unpartitioned space.

Of course they don't show as Linux partitions - I was telling him to delete his non-Windows partitions, and therefore assumed Linux partitions.  My Windows XP always shows them, just not as Linux partitions - as you say, unknown partitions. Never had the unpartitioned space thing, as long as the partitions are there, Windows will see them, just not always now their file system type.:)

---

### Post by aquavitae on 2007-08-03
> **anewguy said:**
> Never had the unpartitioned space thing, as long as the partitions are there, Windows will see them, just not always now their file system type.:)Yes, its kinda weird that mine doesn't.  I got a fright the first time I saw that - thought my linux installation had disappeared! But it booted quite happily and linux sees all.;-)

---


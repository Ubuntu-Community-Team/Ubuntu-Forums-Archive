---
title: "WallStreet PWRBK Hoary Install - it rocks - Need Help?"
date: 2005-04-17
forum: Apple PPC Users
---

### Post by Bug on 2005-04-17
Hi everyone,

I just installed Hoary on a couple machines, one of which is a Wallstreet Powerbook 292 (1st gen). If anyone needs help installing, let me know. It's wasn't too bad (I did Warty, then dist upgrade to Hoary) but I figured I could save someone some time looking for answers if they are trying to install Ubuntu on it. It works really well, and I'm happy to let you know (on this machine at least) that it's pretty snappy. I might also be able to help with OS X/Linux issues since that's the environment I'm in. 

And just posted this in another thread;

---

I'm still going to use OS X often, because it's through a KVM, however I just installed Hoary on an old WallStreet Powerbook with 192mb of ram. It's amazing how much life is still in this machine after playing with Hoary on it. It's not bad at all! just turn off as much background stuff as you can (ie- thumbnail generators, font antialiasing (just leave hinting on or it looks like dirt), and other odds and ends I dont remember. And make sure you have enough Ram, I had 64 for the initial install and after thinking I'm stuck with OS 9 on this thing (omg does 9 suck, I forgot how badly) I found a 128mb dimm I put it. Preso! 192mb and 10x faster! The swapping to the drive just crippled the thing.

---

Adam

---

### Post by chascon on 2005-04-18
Why don't you right it up at
[http://ubuntuppc.webplazahosting.com/](http://ubuntuppc.webplazahosting.com/)

Then maybe reference it inot your signature or something.

---

### Post by Debido on 2005-05-05
Have Wallstreet 266. Burned .iso on a PC. What speed should I use, cause it did not even see the disk at 48x. Went to 16x, then 8x. OS9 will read the disk. But it will not boot off of cd. Holding C or Opt-Cmd-Shift-Del. Do I have to burn the .iso on a Mac? I've done a preview disk for a Sawtooth once and it worked fine. The .iso was burned on a PC as well. 

Using Alcohol 120%. 

PS, the media I am using is the same for the backup OS 9.2.1 cd I made. Which installed just fine. So I don't think it's media/old style cdrom problem.

This thing doen't have OpenFirmware, right?

---

### Post by Bug on 2005-05-06
Missing open firmware is more of a hassle than a problem. Using bootx is painless once you get your kernel & ram disk over to the hfs partition to boot from (usb drive, network copy, etc).

But you can't even boot it, so I'd suggest burning it on the Mac as your first step. Most(all?) PC cd-r drives will plug into a ata bus on a G3/G4 tower and burn with disk utility under X. If not, toast under 9 would be my other suggestion. I also found some of the newer burns I've done do not work in this 6(+?) year old CD-Drive, and slower burning seems to fix some of the high speed burns I tried. I ended up having to pull a superdrive from an older 867 to use on my other tower with a $35 firewire bridge board to get me a bootable cd. I feel it was my usisng disk utility in X that ws the answer howver, so any burner should work. The CD worked without a problem after that. 

Make sure you have at least 128mb of ram (64 makes it SLOW with the disk trashing around) too.  

Let me know how it goes, write back if it's not working for you,

Adam

---

### Post by Bug on 2005-05-06
I missed something, sorry, it's real real late over here in NY... (or early for some).

you need to do two things to boot and install;

1) download a copy of BootX (google it)
2) copy the linux kernel and the ramdisk to you system folder. You can find those copies on the actual linux CD (in install or something, PPC/Install maybe?) 

Then, you can open up the control panel that is half of Bootx, pick you kernel image (should already be in there), and then pick your ramdisk file (should be in the system folder also). Click 'linux' and you'll start. By taking the install files from the CD, you don't have to boot for it. So your PC disk might still work. I forgot I was speaking abut thes oldworld machines. 

Let me know if you need help, I can  zip this stuff up and email it (Gmail is great) to you but it might be a couple days until this weekend before I can find my CD again.

Adam

---

### Post by Tommy on 2005-07-07
[QUOTE=Bug](I did Warty, then dist upgrade to Hoary)[/QUOTE]

I was hoping it's possible to install straight from Hoary -- not only is it a hassle to do the dist-upgrade, I've had a few small issues with machines I've upgraded that way, so I wanted to do a clean install of Hoary if I could.

I have a 1998 PowerBook G3 Series 266 Mhz (PDQ/Wallstreet) formerly running Debian. I believe it has 192Mb RAM, and it has a 20 Gig Fujitsu drive. The Mac OS 9 part of the drive hiccoughed yesterday and needed reformatting so I decided it might be time to try Ubuntu on it.

I got BootX to start the install CD (though frustratingly the needed video=atyfb parameters are differet from the ones that worked in Debian). The installer makes it all the way to the "Installing the Base System" step, then it says it can't detect an Ubuntu image to install from. (And of course it was reading items from that very image in the preceeding steps!)

I've tried the hints on the wiki at
[https://wiki.ubuntu.com/InstallOnOldWorldMacs](https://wiki.ubuntu.com/InstallOnOldWorldMacs)   but no luck. The relevant modules do seem to load... the mesh module loads fine, mace is not on the Hoary CD but the ethernet gets detected and configured so I presume it's not needed in Hoary.

As I said, the installer is able to detect the CD and load the first small group of packages including the partitioner, it lets you partition the drive, and then it says it can't find an Ubuntu CD. On one try, I loaded the custom package that lets you point to another repository, and it seemed to successfully download and install
packages from the UK repository (sorry about the bandwidth), but that installation attempt failed in a different place.

Nobody has responded to my message on the Ubuntu Users list in about 18 hours, so I'm guessing the Warty install is the only way...

---

### Post by Bug on 2005-07-08
Hey Tommy,

Sorry to hear thats not going well, I don't remember why I couldn't do the install exactly but this sounds familar. It might take alot longer going to the dist-upgrade route, but I know for sure it works. Are you using the original CD module with the powerbook? That's what I have, and I might (might!) have run into the same problem. The hardest part for me was figuring out how to transfer the kernal and parms file over after the install, I ended up using an os x server for that. Good luck, it's worth the effort!

Adam

---

### Post by Tommy on 2005-07-09
[QUOTE=Bug]
It might take alot longer going to the dist-upgrade route, but I know for sure it works. Are you using the original CD module with the powerbook? That's what I have, and I might (might!) have run into the same problem. The hardest part for me was figuring out how to transfer the kernal and parms file over after the install
[/QUOTE]

Yes, it took awhile, but (thank goodness for ubuntu repositories and broadband) the results are VERY good. I used the information on the wiki at [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs) (except I'm using BootX instead of miboot), and the pivot_root trick for copying the kernel files to the hfs partition work fine. (Actually I edited his instructions on the wiki -- the original instructions said he pivoted into the new system, but had to start the installer again -- I pivoted BACK into the installer system and it worked fine. I've had no end of trouble trying to run the installer more than once so I wanted to avoid it, and the pivot works BOTH ways.)

Yes, I'm using the original CD, and I have the floppy on the other side even though I never use it. (My power battery finally completely died about a year ago and it's not seemed worth $140 to replace it. I have a ZIP drive but I never use it, either....)

Anyway, Ubuntu Hoary works VERY well on this system. The "Kubuntu version" of KDE is very interesting, and works better than the "stock" KDE on this system. And since GNOME may never have the "Mac Style Modifier Keys" option I will probably continue using KDE on this Ubuntu setup....

Just a few small things -- ongoing projects -- please weigh in if you know any of these off the top of your head:

o Suspend and resume actually works great, EXCEPT it only happens once per boot. After the first suspend and resume, it won't do it again. (This was true in Debian, too.)

o The drive never spins down, so the machine runs hot. I set the pbbuttonsd.conf to "custom," and I set hdparm spindown time to 60 seconds, and I set the noatime parameter for the root partition in /etc/fstab but there must be a process that constantly writes to the drive and I'll have to remember or figure out what that is. It's the system log daemon or something.

o I suspect there's a slight problem with my X config -- when I switch back and forth to MOL under GNOME I get some bizarre colors on the screen that don't go away until I log out. BUT it seems to be less of a problem under KDE. I think the default settings aren't quite right, so I will look through my old Xfree86 config and see if I can come up with an xorg config that works as well as it did. I just pulled up the KInfoCenter panel showing the X server and it has all sorts of X modes activated that I'm pretty sure aren't valid.

o One strange thing is the atyfb driver is VERY "chatty" under Hoary (I didn't notice this at all in Debian, and I didn't look in Warty). Every time I boot or do something that affects the screen resolution or depth, there are about 50 lines of messages (in dmesg, etc.) starting with "atyfb:" and "debug atyfb:". I was surprised that the video=atyfb kernel parameter was different in Warty & Hoary -- the Debian version allows the parameter in a much more readable form, such as 1024x768-8, but ubuntu needs the vmode cmode and hclk numbers, so maybe I got mine wrong.

---

### Post by DavidTheNew on 2005-07-21
[QUOTE=Bug]Hi everyone,

I just installed Hoary on a couple machines, one of which is a Wallstreet Powerbook 292 (1st gen). If anyone needs help installing, let me know. It's wasn't too bad (I did Warty, then dist upgrade to Hoary) but I figured I could save someone some time looking for answers if they are trying to install Ubuntu on it. It works really well, and I'm happy to let you know (on this machine at least) that it's pretty snappy. I might also be able to help with OS X/Linux issues since that's the environment I'm in. 

And just posted this in another thread;

---

I'm still going to use OS X often, because it's through a KVM, however I just installed Hoary on an old WallStreet Powerbook with 192mb of ram. It's amazing how much life is still in this machine after playing with Hoary on it. It's not bad at all! just turn off as much background stuff as you can (ie- thumbnail generators, font antialiasing (just leave hinting on or it looks like dirt), and other odds and ends I dont remember. And make sure you have enough Ram, I had 64 for the initial install and after thinking I'm stuck with OS 9 on this thing (omg does 9 suck, I forgot how badly) I found a 128mb dimm I put it. Preso! 192mb and 10x faster! The swapping to the drive just crippled the thing.

---

Adam[/QUOTE]


I would like some help, if possible. I followed the following steps to install Ubuntu on my Wallstreet:
1) Make three partions on the hard drive: first one I formatted as a Mac OS+, the next was Mac OS, the third I left unformatted.

2) I installed Mac OS 9.2 on the first partion.

3) Installed BootX and the required kernal. I inserted the Ubuntu CD.

4) Started BootX and started the install disk successfully.

5) Installed the system, no problem until the end.

6) The install program said the boot kernel was not in hda11, so it had to be moved there...

7) I tried to copy the kernel but I had problems doing it. I tried the pivot table stuff but it did not work. What did you do?

Also, do I have to redo the install procedure?

Thanks for your time,
DavidTheNew

---

### Post by Tommy on 2005-07-22
[QUOTE=DavidTheNew]
1) Make three partions on the hard drive: first one I formatted as a Mac OS+, the next was Mac OS, the third I left unformatted.
[/QUOTE]

Assuming your first partition is the boot partition, I recommend formatting it HFS rather than HFS+. (I can't recall for sure what the Mac HD Setup utility calls it -- I think it calls HFS Plus "Mac OS Extended.") You might want to avoid HFS Plus / aka Mac OS Extended on your boot partition because the older Mac OS / aka HFS drivers have been out a lot longer and have fewer bugs and are more likely to be loadable when you need them.

> 
6) The install program said the boot kernel was not in hda11, so it had to be moved there...

7) I tried to copy the kernel but I had problems doing it. I tried the pivot table stuff but it did not work. What did you do?

Also, do I have to redo the install procedure?


I personally would redo the procedure because I have had very poor luck restarting the installer, even though the guy who started the wiki entry here said it worked for him:

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

I recommend using whatever procedure you used to get BootX going, and then skip down to the section in the Wiki with the heading "Install." Here's a link directly to that portion:

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs#head-6baba7d43477af8faa090a6c456cb78232ec3870](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs#head-6baba7d43477af8faa090a6c456cb78232ec3870)

On my PowerBook G3 I did NOT have to modprobe mesh and modprobe mace because the installer successfully loaded them. In the original version he described doing a pivot_root so he could load the hfs modules, copy the kernel and initrd, and then he said he restarted the installer because it wasn't finished. I added the lines describing how to pivot_root BACK to the installer kernel and letting the installer finish. It's much cleaner that way and not much harder, though obviously there are two places to make a big mistake. But it's not like a patient will die or anything like that.

So I would recommend starting again from the beginning by reformatting and repartitioning the drive, this time with a small hfs (Mac OS) boot partition. Install Mac OS 9.x as you did, using a very minimal install because BootX does NOT need much, though you may want to include some basics like Startup Disk, and maybe Monitors Control Panel (Sadly the OS 9 version needs a lot of junk like Apple Help to operate the Monitors control panel. Maybe the Control Strip components need less. But I digress.)

If what it says in the Wiki does NOT work for you, post your exact experience here -- write down what error you get. If I misunderstood and you are already booting from the hfs partition, then let us know what messages you see.

And a note of encouragement -- this is by far the hardest part! You're almost there!

---

### Post by Tommy on 2005-07-22
[QUOTE=Tommy]
o The drive never spins down, so the machine runs hot.[/QUOTE]
I forgot to update this thread -- I have figured this one out, though I haven't completely fixed it. I did file a bug about it: [https://bugzilla.ubuntu.com/show_bug.cgi?id=12701](https://bugzilla.ubuntu.com/show_bug.cgi?id=12701) 

For some reason laptop mode doesn't start automatically. Open a terminal window and issue this command:

```
sudo laptop-mode start
```

and the drive will spin down (and maybe other things happen) just as expected until the next boot. It would be ULTRA simple to add this line to a shell script but I have been trying to learn what was supposed to call it (and isn't) in the first place.

---

### Post by DavidTheNew on 2005-08-21
[QUOTE=Tommy]Assuming your first partition is the boot partition, I recommend formatting it HFS rather than HFS+. (I can't recall for sure what the Mac HD Setup utility calls it -- I think it calls HFS Plus "Mac OS Extended.") You might want to avoid HFS Plus / aka Mac OS Extended on your boot partition because the older Mac OS / aka HFS drivers have been out a lot longer and have fewer bugs and are more likely to be loadable when you need them.



I personally would redo the procedure because I have had very poor luck restarting the installer, even though the guy who started the wiki entry here said it worked for him:

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

I recommend using whatever procedure you used to get BootX going, and then skip down to the section in the Wiki with the heading "Install." Here's a link directly to that portion:

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs#head-6baba7d43477af8faa090a6c456cb78232ec3870](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs#head-6baba7d43477af8faa090a6c456cb78232ec3870)

On my PowerBook G3 I did NOT have to modprobe mesh and modprobe mace because the installer successfully loaded them. In the original version he described doing a pivot_root so he could load the hfs modules, copy the kernel and initrd, and then he said he restarted the installer because it wasn't finished. I added the lines describing how to pivot_root BACK to the installer kernel and letting the installer finish. It's much cleaner that way and not much harder, though obviously there are two places to make a big mistake. But it's not like a patient will die or anything like that.

So I would recommend starting again from the beginning by reformatting and repartitioning the drive, this time with a small hfs (Mac OS) boot partition. Install Mac OS 9.x as you did, using a very minimal install because BootX does NOT need much, though you may want to include some basics like Startup Disk, and maybe Monitors Control Panel (Sadly the OS 9 version needs a lot of junk like Apple Help to operate the Monitors control panel. Maybe the Control Strip components need less. But I digress.)

If what it says in the Wiki does NOT work for you, post your exact experience here -- write down what error you get. If I misunderstood and you are already booting from the hfs partition, then let us know what messages you see.

And a note of encouragement -- this is by far the hardest part! You're almost there![/QUOTE]
 I did what you suggested. When I was trying to copy the stuff to the boot sector. I tried this command: 
mount -t hts /dev/hda11 /mnt/foo2

I got an error /dev/.hda11 already mounted or mnt/foo2 busy

any idea why?

---

### Post by DavidTheNew on 2005-08-21
[QUOTE=Tommy]Assuming your first partition is the boot partition, I recommend formatting it HFS rather than HFS+. (I can't recall for sure what the Mac HD Setup utility calls it -- I think it calls HFS Plus "Mac OS Extended.") You might want to avoid HFS Plus / aka Mac OS Extended on your boot partition because the older Mac OS / aka HFS drivers have been out a lot longer and have fewer bugs and are more likely to be loadable when you need them.



I personally would redo the procedure because I have had very poor luck restarting the installer, even though the guy who started the wiki entry here said it worked for him:

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

I recommend using whatever procedure you used to get BootX going, and then skip down to the section in the Wiki with the heading "Install." Here's a link directly to that portion:

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs#head-6baba7d43477af8faa090a6c456cb78232ec3870](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs#head-6baba7d43477af8faa090a6c456cb78232ec3870)

On my PowerBook G3 I did NOT have to modprobe mesh and modprobe mace because the installer successfully loaded them. In the original version he described doing a pivot_root so he could load the hfs modules, copy the kernel and initrd, and then he said he restarted the installer because it wasn't finished. I added the lines describing how to pivot_root BACK to the installer kernel and letting the installer finish. It's much cleaner that way and not much harder, though obviously there are two places to make a big mistake. But it's not like a patient will die or anything like that.

So I would recommend starting again from the beginning by reformatting and repartitioning the drive, this time with a small hfs (Mac OS) boot partition. Install Mac OS 9.x as you did, using a very minimal install because BootX does NOT need much, though you may want to include some basics like Startup Disk, and maybe Monitors Control Panel (Sadly the OS 9 version needs a lot of junk like Apple Help to operate the Monitors control panel. Maybe the Control Strip components need less. But I digress.)

If what it says in the Wiki does NOT work for you, post your exact experience here -- write down what error you get. If I misunderstood and you are already booting from the hfs partition, then let us know what messages you see.

And a note of encouragement -- this is by far the hardest part! You're almost there![/QUOTE]
 I did what you suggested. When I was trying to copy the stuff to the boot sector. I tried this command: 
mount -t hts /dev/hda11 /mnt/foo2

I got an error /dev/.hda11 already mounted or mnt/foo2 busy

any idea why?

Could you send me the files I ned to place in the Linuk Kernels directory? I downloaded version 2.6.8 but it was excpcting 2.6.10.something.

---

### Post by Tommy on 2005-08-21
[QUOTE=DavidTheNew]When I was trying to copy the stuff to the boot sector. I tried this command: 
mount -t hts /dev/hda11 /mnt/foo2

I got an error /dev/.hda11 already mounted or mnt/foo2 busy

any idea why?
[/QUOTE]

My first guess is that you accidentally picked the partition you're installing into OR when you were running the partition tool you accidentally chose the MacOS partition. When I am installing it helps me to write the partitions I'm using on a sticky note that I keep posted until everything is working correctly. On a MacOS / HFS / HFS+ system there are SEVEN little partitions the Mac bootloader needs BEFORE the ones you use, so your partitions start at number 8.

FOR EXAMPLE... on this system, 

/dev/hda8 (hfs) contains a small system folder and bootx
  (so that would be the one I mount to copy my vmlinux and initrd into)
/dev/hda9 (hfsplus) contains another MacOS partition 
  (I use it to boot into MOL or as a "native" mac)
/dev/hda10 (hfsplus) another MacOS partition where I keep photo files
/dev/hda11 (ext3) my root ubuntu partition
/dev/hda12 (swap) my swap partition

This is not the perfect arrangement, but it's what I have. For your reference you will want to list what you have in each partition starting with /dev/hda8

> 
Could you send me the files I ned to place in the Linuk Kernels directory? I downloaded version 2.6.8 but it was excpcting 2.6.10.something.

I believe the warty kernel is 2.6.8-x-powerpc, and it will get you started, though as soon as you get online you will want to upgrade it. You could do the Hoary upgrade online or from a CD, but I would get Warty going first. You need to copy the file named initrd.img-2.6.xxxx-powerpc and the file named vmlinux-2.6.xxxx-powerpc (substitute whatever version you have for the xxxx). They need to get into the partition with bootx any way you can get it there. 

(By the way, some folks have been successful using another networked machine. If you have another Ubuntu machine -- intel or powerpc-- you can install netatalk on it and copy the vmlinux and initrd files to it using rcp, then boot into Mac OS and connect to the Ubuntu machine as an Apple file server to copy the files to your bootx partition.  HOWEVER I think you should eventually be able to mount the hfs partition and copy the files directly with a little less effort.)

By the way, you have to be sure you boot from the same kernel whose modules are installed in the linux partition(s). You can have more than one kernel to choose from, and the kernel will get the correct ones from the correct place, but you must copy the kernel manually after each upgrade to the files in your /boot directory.


I hope I haven't made this more confusing with too much explanation! Let me know.

---

### Post by DavidTheNew on 2005-09-19
Hey, good news, it works!!! It boots!!

Just two things that are strange:
1) It does not boot into gnome, it gives me a command line
2) Ste screen is off-center. It looks like I have four frames on one monitor giving me the same information.
What kernel parms do I need?

P.S> I copied a kernel from  [http://www.boomboom.com/wallstreet](http://www.boomboom.com/wallstreet), I did not copy the kernel from the boot.

Thank you for you help.

---

### Post by Tommy on 2005-09-19
[QUOTE=DavidTheNew]Hey, good news, it works!!! It boots!!

Just two things that are strange:
1) It does not boot into gnome, it gives me a command line
2) Ste screen is off-center. It looks like I have four frames on one monitor giving me the same information.
What kernel parms do I need?

P.S> I copied a kernel from  [http://www.boomboom.com/wallstreet](http://www.boomboom.com/wallstreet), I did not copy the kernel from the boot.
[/QUOTE]

It's great you got it going! I know nothing about the kernel you mentioned, but I presume from what the directory says it's an OLD version of the Hoary kernel. As soon as you get things going you'll want to get the latest version to make sure you have all the security updates.

I am presuming you were able to make it ALL THE WAY through the installer CD. If you didn't and some of the packages weren't fully installed, that would explain why X didn't start.

It's also possible X won't start because the video is messed up. Once you boot with  good parameters (see the end), try configuring X using this command

sudo dpkg-reconfigure xserver-xorg


BOOT PARAMETERS -- these may not be absolutely perfect, so if someone else has better ones, let me know. Put the following in the "More kernel arguments" field in BootX:

video=atyfb:vmode:14,cmode:32,mclk:71 root=/dev/hda8 apm=on

[The root= parameter should be YOUR root partition. The number will be /dev/hda8 or higher... mine is actually /dev/hda11 because I have several bootable partitions.)

---

### Post by DavidTheNew on 2005-09-19
Thanks for your help.

Going well, the parms worked like a charm. I tried this command to install xwindows:

sudo dpkg-reconfigure xserver-xorg

I got this error:

/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

How do I install it? I have tried dselect without success. I think I have been having problems selecting the correct repository.

---

### Post by Tommy on 2005-09-21
[QUOTE=DavidTheNew]I tried this command to install xwindows:

sudo dpkg-reconfigure xserver-xorg

I got this error:

/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

How do I install it? [/QUOTE]

That command is to reconfigure xserver-xorg (the X server) AFTER it's been installed. You CAN install the X server using 

apt-get install xserver-xorg 

OR you can use aptitude, HOWEVER it sounds like the installer didn't run, or it didn't finish. You must have the base-install going or it wouldn't boot, but who knows what packages are missing, so you probably won't get the "Ubuntu experience."

Did the installer transfer and begin to install many many packages? It takes a long time -- over an hour -- so if you didn't see that I would suspect the installer didn't finish. This may be a result of using a kernel and ramdisk other than the one on the installation disk... 

Now this doesn't mean you can't continue, but you will have to manually choose and install all the packages. If you don't have a lot of Debian experience, I would start with aptitude -- if you can't run "sudo aptitude" at the prompt, then use 

sudo apt-get install aptitude

Then you will have to choose things pretty much like a Debian installation. Aptitude will help pick them because it puts them in categories... I would FIRST choose the package Ubuntu-Desktop and see if it brings in a lot of other things. 

So if it's not too terrible a suggestion I'd just about recommend trying to get the installer kernel and initrd off of a Warty CD, boot from that, and run the installer from scratch, copy whatever kernel it tries to install, let the installer finish, and THEN try whatever custom kernel you found.

But in my experience, on a Wallstreet you HAVE to start with a Warty disk -- I have not ever been able to get Hoary to install on this Wallstreet, but it UPGRADES to Hoary just fine.

Hope that helps....

---


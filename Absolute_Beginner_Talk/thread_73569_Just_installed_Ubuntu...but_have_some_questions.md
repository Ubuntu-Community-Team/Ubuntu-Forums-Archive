---
title: "Just installed Ubuntu...but have some questions"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by VelocityMicro on 2005-10-09
First off, it's installed on my slave drive in its own partition. There is also a FAT32 partition named DATA. Here are my questions...

1 > In Ubuntu, I can't play a DVD movie and can't play MP3 songs. I need decoders - how I get them?

2 > Why can't I browse files in my DATA (FAT32) partition, which is on the same slave hard disk?

3 > In Windows XP Pro, why does PartitionMagic 8.0 tells me that my 2nd hard disk is bad...even though Ubuntu and DATA partitions on it are intact and working fine?

4 > In Ubuntu, is there a graphical partition program?

---

### Post by Kyral on 2005-10-09
1) Look Here (Used to be easy, but some legal stuff came up and now it isn't) [http://ubuntuforums.org/showthread.php?t=70227](http://ubuntuforums.org/showthread.php?t=70227)

2) Didja enter something in the /etc/fstab? Fire up the command line and paste the out put of "cat /etc/fstab"

3) I could be cynical and say that to Windows, Ubuntu IS bad, but ;P I honestly don't know why.

4) GParted or QtParted

---

### Post by aysiu on 2005-10-09
[QUOTE=VelocityMicro]
2 > Why can't I browse files in my DATA (FAT32) partition, which is on the same slave hard disk?[/QUOTE] [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by Kyral on 2005-10-09
[quote=aysiu][http://www.ubuntuguide.org/#automountfat]("http://www.ubuntuguide.org/#automountfat")[/quote]

Or that....

---

### Post by Wolki on 2005-10-09
[QUOTE=VelocityMicro]1 > In Ubuntu, I can't play a DVD movie and can't play MP3 songs. I need decoders - how I get them?[/QUOTE]

Everything you need to know: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by VelocityMicro on 2005-10-09
This isn't my first time using Linux...I have used Mandrake and Slax Live CD.

I have no idea on what the Starter Guide is saying...I have read the starter guide about many things, and I still can't play songs/video or read/write files to the DATA (FAT32) partition.

I installed Ubuntu, thinking that it would be a friendly OS - Unfortuanetly it is more convaluted than any other linux OS I've tried. The update manager did nothing (updated over 100 packages, and still can't do anything). 

Are their simpler instructions about getting my sound/video files playing and write/read on my DATA (FAT32) partition?

sudo gedit /etc/apt/sources.list

When Gedit appears, enter the following line, then save and close gedit:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

Next update and install packages, this will also add other misc codecs/plugins:

sudo apt-get update
sudo apt-get install w32codecs 
sudo gedit /etc/apt/sources.list

- What the hell does this mean - can anyone give me step by step instructions?

---

### Post by Wolki on 2005-10-09
[QUOTE=VelocityMicro]
sudo gedit /etc/apt/sources.list

When Gedit appears, enter the following line, then save and close gedit:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

Next update and install packages, this will also add other misc codecs/plugins:

sudo apt-get update
sudo apt-get install w32codecs 
sudo gedit /etc/apt/sources.list

- What the hell does this mean - can anyone give me step by step instructions?[/QUOTE]

Sure.

Open a Terminal (Applications -> System Tools -> Terminal
Paste "sudo gedit /etc/apt/sources.list" there. Enter your password if asked.
A window with a text editor should appear. Go to the end and paste the following: ```
deb ftp://ftp.nerim.net/debian-marillat/ etch main
```.
Save, then run the following commands:
sudo apt-get update
sudo apt-get install w32codecs 
Now the special windows codecs are installed. Since that line you've added above can really confuse your system if you do a security update, remove them again by doing: "sudo gedit /etc/apt/sources.list", then deleting what you've added and saving again.

If you have more questions, feel free to ask.

---

### Post by VelocityMicro on 2005-10-09
I just did exactly that and no cigar. Still can't play any basic multimedia format.

"Linux for Human Beings" - I don't want to offend the people who make this distro, but that simply is not true.

---

### Post by aysiu on 2005-10-09
Those are simple instructions.
The only way those could be hard to follow is if you didn't know how to open a terminal. Maybe that's the problem.

In Gnome, you go to the Gnome foot logo, System, and Terminal. Then you can copy and paste whatever commands people ask you to copy and paste in.

As for Ubuntu being easy to use, there are a few things you have to understand. First of all, *use* is different from *installation and configuration*. If you want everything to "just work" out of the box, you're better off with Mepis, Blag, or Linspire.

One of the reasons Ubuntu doesn't "just work" out of the box is its dedication to only free software--free in cost, free in license, free as in open. That's why you have to enable extra repositories to get non-free codecs.

As for the automounting of FAT drives--that's probably more of a Gnome/KDE issue than anything else. Honestly, though, it isn't so difficult to copy and paste a few commands. If you want the FAT partition to magically appear and automount without having to follow any instructions, I'd highly recommend Mepis.

---

### Post by aysiu on 2005-10-09
[QUOTE=VelocityMicro]
"Linux for Human Beings" - I don't want to offend the people who make this distro, but that simply is not true.[/QUOTE] None taken. [I wrote this thread just for you](http://ubuntuforums.org/showthread.php?t=70603), even before you joined the forums.

---

### Post by Wolki on 2005-10-09
> **VelocityMicro]I just did exactly that and no cigar. Still can't play any basic multimedia format.[/QUOTE]

You did not ask about basic mulitmedia formats, but for a walkthrough to the part you've quoted. ^^ said:**
> https://wiki.ubuntu.com/RestrictedFormats)[/url]. The Important part is this:
[QUOTE=Wiki]sudo apt-get update
sudo apt-get install totem-xine gstreamer0.8-misc gstreamer0.8-plugins gstreamer0.8-plugins-multiverse 
sudo apt-get install gstreamer0.8-mad gstreamer0.8-ffmpeg libmad0 msttcorefonts libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
gst-register-0.8

Make sure you have Universe and Multiverse installed. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) contains a graphical guide (with pictures!) on how to do it.

If things do not work after that, we need more specifics - exactly what kind of media do you want to play, and which player are you using? Oh, and post any errors you might get.

---

### Post by VelocityMicro on 2005-10-09
[QUOTE=aysiu]Those are simple instructions.
The only way those could be hard to follow is if you didn't know how to open a terminal. Maybe that's the problem.

In Gnome, you go to the Gnome foot logo, System, and Terminal. Then you can copy and paste whatever commands people ask you to copy and paste in.

As for Ubuntu being easy to use, there are a few things you have to understand. First of all, *use* is different from *installation and configuration*. If you want everything to "just work" out of the box, you're better off with Mepis, Blag, or Linspire.

One of the reasons Ubuntu doesn't "just work" out of the box is its dedication to only free software--free in cost, free in license, free as in open. That's why you have to enable extra repositories to get non-free codecs.

As for the automounting of FAT drives--that's probably more of a Gnome/KDE issue than anything else. Honestly, though, it isn't so difficult to copy and paste a few commands. If you want the FAT partition to magically appear and automount without having to follow any instructions, I'd highly recommend Mepis.[/QUOTE]

Okay, I'm running Slax Live CD now...And guess what I can play every song and movie format. I can read/write all info from the DATA and Ubuntu partitions...also Win XP (NTFS) as well. Slax is based on Slackware and it peforms beautifullu OUT OF THE BOX (no command line, no nothing) works perfectly. My only question now is how I can delete Ubuntu and install Slax (Slackware.

---

### Post by Wolki on 2005-10-09
[QUOTE=VelocityMicro]Okay, I'm running Slax Live CD now...And guess what I can play every song and movie format. I can read/write all info from the DATA and Ubuntu partitions...also Win XP (NTFS) as well. Slax is based on Slackware and it peforms beautifullu OUT OF THE BOX (no command line, no nothing) works perfectly. My only question now is how I can delete Ubuntu and install Slax (Slackware.[/QUOTE]

Well, I don't want to sound harsh, but it's better to ask that at a Slackware forum, as the people there have more experience with that distribution. You should be able to just install it over your ubuntu partition though. Have fun with Slackware.

---

### Post by aysiu on 2005-10-09
[QUOTE=VelocityMicro]Okay, I'm running Slax Live CD now...And guess what I can play every song and movie format. I can read/write all info from the DATA and Ubuntu partitions...also Win XP (NTFS) as well. Slax is based on Slackware and it peforms beautifullu OUT OF THE BOX (no command line, no nothing) works perfectly.[/QUOTE] What part of Ubuntu uses only free software did you not understand? There are plenty Linux distributions (including Slax, apparently), which include proprietary codecs and software (I listed a few above--Mepis, Linspire, Blag). Ubuntu is not one of these. Clearly, Ubuntu is not for you.

> My only question now is how I can delete Ubuntu and install Slax (Slackware. Just install Slackware. You don't need to delete Ubuntu--just install right over it.

---

### Post by VelocityMicro on 2005-10-09
[QUOTE=aysiu]Just install Slackware. You don't need to delete Ubuntu--just install right over it.[/QUOTE]
Hold up...When installing Ubuntu, I also created a created a Master bootloader with Grub on my first hard disk (Win XP NTFS). Slackware uses LILO bootloader...if I just install Slackware on top of Ubuntu won't I screw up the boot loader?

---

### Post by Wolki on 2005-10-09
[QUOTE=VelocityMicro]Hold up...When installing Ubuntu, I also created a created a Master bootloader with Grub on my first hard disk (Win XP NTFS). Slackware uses LILO bootloader...if I just install Slackware on top of Ubuntu won't I screw up the boot loader?[/QUOTE]

Slackware should install its own boot loader during installation. Like I said, more and more accurate information is available on Slack forums.

---

### Post by zerhacke on 2005-10-09
[QUOTE=VelocityMicro]3 > In Windows XP Pro, why does PartitionMagic 8.0 tells me that my 2nd hard disk is bad...even though Ubuntu and DATA partitions on it are intact and working fine?[/QUOTE]
It is entirely possible to have a bad disk and still install Ubuntu or write data to the disk.  To illustrate, I'll use an example including another operating system called FreeBSD.

I tried to install FreeBSD to my third IDE drive about a week ago.  sysinstall (the program that installs FreeBSD) complained that the disk was bad and wouldn't even write a partition table to it.  I killed the install, booted Windows, and downloaded some disk checking software.  The disk indeed did have errors, multiple types.  Bad sectors, geometry errors from BIOS, and another kind of error I can't remember right now.

Then I installed Ubuntu to the drive.  As long as it's got enough good usable space without bad sectors, Linux will install because it doesn't do too many intensive checks to the drive itself during install.  So long as it gets to write the system and a bootloader, along with partition information, it's happy.  Ubuntu installed fine on a known bad drive.

I don't really know if that's a good thing or a bad thing, to tell the truth.

---

### Post by Kyral on 2005-10-09
Offtopic: When did Asyiu become a Mod? Congrats dude!

Ontopic: Yah, I don't like that its a pain in a half to get multimedia working, but then again it isn't the first time I spat in the face of unfair IP practices. You gotta understand, its just Canonical trying to protect itself from a lawsuit. You can't include most of the stuff we take for granted because of licensing. But you can snag it from repos. Then again Linux is for choices, so if you like Slack go ahead. I cut my teeth on Slack all those years ago.

---


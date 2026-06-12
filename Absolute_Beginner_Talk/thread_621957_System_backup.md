---
title: "System backup"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-11-24
Hi, I need to reinstall Ubuntu 7.10 and backup my files and programs. This would be my first time backing up and I need a little help.

What program should I use? I have Simple Backup right now, but I could get another.

Are files compressed when they are backed up? Or does the backup contain exact copies of the files?

If I am reinstalling Ubuntu, I would have to backup to another drive, right? Could I then use my iPod or my Windows partition if my iPod does not have enough room? (Windows partition 35gb, iPod 30gb)

Would backing up my Home folder mean that my programs were backed up?

Thanks so much for your help.

---

### Post by Rinzwind on 2007-11-24
Inside your home folder are your settings. so do a 
cd
tar cvfz backup.tar /home/{username}/
inside a terminal and all your settings will be inside 'backup.tar'.
This will include your desktop and even your bookmarks, theme and backgrounds.

You can move this file onto an usb pendrive, cd, dvd of even your Ipod if you got enough room. Just do not use windows if it's on the same system: you might make a mistake formattting your discs and ending up without windows.

OH and DO check if you can copy your file back into your currrent Ubuntu and can reinstall this file! If it errors out cuz of something you mistyped you still fix that problem!


Wait for someone else to post too and then pick your option :) Mine might be wrong/not complete cuz I am not an exper :

---

### Post by kevindubrow on 2007-11-24
Ok, so how would all of that fit on a pendrive? Are the files compressed or is that just assuming that the pendrive is large enough to hold all of the files? Sorry if these are obvious questions, I am still confused about how a system can be backed up on zip drives and such when it would seem like they would not be large enough. Thanks for your help!

---

### Post by Rinzwind on 2007-11-24
The 'z' in the tar command means gzip it (so compress it).
All you need to do is copy the backup.tar to where you want to copy it.

---

### Post by kevindubrow on 2007-11-24
Ok, so...if I backed up my home folder and other files I would keep my programs and my settings, along with any specific files I requested to backup. Right? And also, will any of my files lose their quality when being compressed? Should I just copy and paste some files to another drive rather than backing them up to avoid this problem (if it even exists)? Thanks a lot for your help.

---

### Post by Rinzwind on 2007-11-24
A compressed file will never loose quality.
Programs are removed during an install with format so you will have to reinstall them.
Settings you have inside your backup will write over the newly created settings.
So all should be fine.

BTW I did it a bit different. I have a setup like this:

120 Gb disc in my laptop with: 
/  8.5 Gb 
swap 1.5 Gb 
/home 10 Gb
/files 100 Gb

"files" is a partition I never delete/format during a re-install. The rest gets wiped. I save all files I need to save that are inside /home to /files/backup.tar and just untar it when I am done. Up to now all I save are my .kq savegames (even my bookmarks get wiped cuz I know them from memory anyways :D )

"files" also includes a file with my WAP key. So I do not have to retype a 128 characters randomly created key ;) 
Plus it has an extra installation script (just a file with loads of 
apt-get remove
apt-get install
in it ;) Evolution Totem Ekiga Pidgin get removed. VLC streamtuner XMMS etc gets installed.

With this I can reinstall my system and have all I normally used installed with a few keystrokes.

---

### Post by kevindubrow on 2007-11-24
Wow, very cool....I would just worry about running out of room in a particular partition. What do you do then?

---

### Post by Rinzwind on 2007-11-24
100 Gb for a laptop is more than enough ;)
Swap more than 2 times your memory is useless I think.
Home dir: well if you use 'files' to store everything you'll not use your home for large files and all it will include are settings.

And all you need to make sure is that / (root) is large enough and 8.5 Gb has yet to be a problem for me (started with this about 1.5 years ago with a 40 Gb disc).

I think I have the setup that works best for me. Every other person might disagree ;) 
For instance: I like a clean desktop: no icons whatsoever. Others like their desktop messy and filled with icons.
I tend to use my gnome taskbar alot more than others and have that stuffed with applets.

---

### Post by kevindubrow on 2007-11-24
I agree with you on the desktop thing. This may be something I do in the future. This would solve all of my problems with reinstalling Ubuntu whenever an update comes around (I would like to reinstall over upgrade because I get so many glitches with upgrading). I'll do it when I fully understand it :)! Thanks do much for your help, I'll be backing up soon.

---

### Post by Rinzwind on 2007-11-24
Cool!

I never get upgrades to work so I always do a full reinstall about 2 weeks -after- the new release is out. That also solves alot of bugs from the install plus lots of people allready posted solutions on this forum 

>:)

---

### Post by websnail on 2007-11-24
I have another way to backup system to a directory or another (moveable) disk:
open a console, 
cd /
sudo mkdir temp_for_backup
sudo mount /dev/sdx  /temp_for_backup 
#/dev/sdx: which your system install on it , maybe not sdx ,instead  /dev/hdx
rsync -avH --delete /temp_for_backup /the_path_you_want_backup_to
...wait...
sudo umount /temp_for_backup
sudo rm -r /temp_for_backup
done

---

### Post by sailor2001 on 2007-11-24
for your programs, you could burn disk APTONCD  located in synaptics

---

### Post by kevindubrow on 2007-11-24
Thank you all, I'll work on this and tell you how it goes.

---


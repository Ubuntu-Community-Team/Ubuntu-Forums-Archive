---
title: "Only root? Owner? Read only?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by FatalTheGod on 2006-07-13
Well, after waiting for my discs, I finally recieved them and installed them. I tried doing the partition resizing thing to try and Dual Boot, but I ended up having to wipe my C drive, where Windows was installed.

However, all my data (95% of what I needed) is backed up on my D drive. I need to access it, but it's seeming to be somewhat hard. I've read several guides on Mounting/Unmounting, but all say different things, and none work in the long run!

First off, I've needed to mount it with some long string of commands everytime I boot up. I tried editing the fstab (I think that's the name) with a line that should automatically mount the drive everytime Ubuntu starts. However, it says the file is read-only! How can I get around this?

Also, I've been told several times I don't have the permissions to do certain things, and that only the 'Owner' can. However, how am I NOT the owner :P? Is there anyway to change it?

Lastly, why does the Terminal say 'only root can do that' sometimes? What does it mean?

I'm sorry to sound so desperate and like such a 'newbie' but I'm now stuck with just Ubuntu until I can buy another XP CD (long story) and I have a feeling this might be a little tough, so any help is appreciated! Thanks! :)

---

### Post by T700 on 2006-07-13
To do things as root in Ubuntu, preface the command with either "sudo" for non-graphical things or "gksudo" for graphical applications.  For example, to edit that file that says you don't have permissions:

```
gksudo gedit
``` 
and when the editor opens, navigate to the file and do your stuff.  It will now save it.

Linux isn't that tough, but it helps to always remember that it isn't Windows.  Sometimes you have to unlearn what you already know.

Paul

---

### Post by frodon on 2006-07-13
> **FatalTheGod said:**
> Lastly, why does the Terminal say 'only root can do that' sometimes? What does it mean?The terminal give you this message when you try to access something and don't have the needed rights to do it.
For infos, the whole ubuntu partition (except your home directory) need root rights to get a write access. To get root rights use sudo as the post above explain it.

Your problem here seems to be a wrong fstab line.

Please provide us the following information :
1- your fstab file content (sudo gedit /etc/fstab to open it)
2- the name of each partition you want tomount (should be /dev/....., use the sudo fdisk -l command to find the name ) and the file system use by the partitions.
3- where you want to mount the partition(s)

---

### Post by Paerez on 2006-07-13
> First off, I've needed to mount it with some long string of commands everytime I boot up. I tried editing the fstab (I think that's the name) with a line that should automatically mount the drive everytime Ubuntu starts. However, it says the file is read-only! How can I get around this?
Can you post the mount command? I can write the fstab entry for you.

> Also, I've been told several times I don't have the permissions to do certain things, and that only the 'Owner' can. However, how am I NOT the owner :P? Is there anyway to change it?
root (the admin account) is probably the owner, I will include a way to write to the drive in the fstab entry (if it is fat32, and not ntfs)

> Lastly, why does the Terminal say 'only root can do that' sometimes? What does it mean?
root is the admin account, so instead of running:
```
# mount blah blah
```you would have to run:
[coud]# sudo mount blah blah[/code]
sudo makes it run as root, but you need your own password for security.

> I'm sorry to sound so desperate and like such a 'newbie' but I'm now stuck with just Ubuntu until I can buy another XP CD (long story) and I have a feeling this might be a little tough, so any help is appreciated! Thanks! :)
I'll help you the best I can, just keep a positive attitude.

Worst case scenario: You have to move your data to another partition to write to it, which may be a pain, but if you have free space on the OS drive (your C drive) it shouldn't be a problem.

---

### Post by FatalTheGod on 2006-07-13
Thanks for the quick responce! The files saved, so I assume it will work next time I start it up.

A few more questions....

- I assume 'root' is the same as 'owner' ?

- Also, I installed WINE, and when I do 'locate wine' I see some of the files. However, there is no link in the 'Applications' area, nor is there a link on the desktop. Any idea where I can find it or maybe what I did wrong? I did it through the command line, and I get the update and then installed it, and it said it installed 100% with no errors.

Once again, thanks for your help. :)

---

### Post by Brunellus on 2006-07-13
the basics, systemmaticaly treated:

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

You have just encountered one of the great security differences between Windows and the Unix-like operating systems:  permissions.

"root" is the superuser--he can do anything, access anything, create anything, destroy anything.  Ubuntu disables the "root" account by default, because running as root all the time is extremely dangerous.  Think of it as tightrope walking without a net--you could do it, but it's not very safe.

If you need "superuser" privileges, ubuntu instead uses "sudo":  you preface the command with "sudo" in the terminal.  The shell will then prompt you for your password--that's your USER password, that is, the one you set up when you installed.  The program will then execute, using "superuser" priveleges.  When the program finishes, nothing else can run with those superuser privileges.

As a regular user, you can do almost anything, but you only have full permissions (read, write and execute) on your home directory.

---

### Post by FatalTheGod on 2006-07-13
You guys are replying so fast that I can't keep up! I think my question was answered with the first post, but I'm not sure. In a bit I'll restart the computer and see if it works.

However, if you still want to answer some questions, my second reply has more :D

And don't worry, in the next 5 minutes I'll probably have 20 more! ;)

---

### Post by x64Jimbo on 2006-07-13
> **FatalTheGod said:**
> Thanks for the quick responce! The files saved, so I assume it will work next time I start it up.

A few more questions....

- I assume 'root' is the same as 'owner' ?

- Also, I installed WINE, and when I do 'locate wine' I see some of the files. However, there is no link in the 'Applications' area, nor is there a link on the desktop. Any idea where I can find it or maybe what I did wrong? I did it through the command line, and I get the update and then installed it, and it said it installed 100% with no errors.

Once again, thanks for your help. :)
Wine is a program that lets you run other programs. It won't run without another program to run inside it. You need to run it like this:
wine windows_executable.exe
Give that a try.

---

### Post by FatalTheGod on 2006-07-13
Ah, that makes sense, however, what if there is a space in the folder? I copied a lot of files as backups from windows, and right now I'm trying to run:

/media/windows/PROGYY FILEZ/iTunes/iTunes.exe

However, I get 'wine: cannot find /media/windows/PROGGY'

Is there anyway to get around this?

---

### Post by Brunellus on 2006-07-13
either:

enclose the name in "double quotes":

/media/windows/"PROGYY FILEZ"/iTunes/iTunes.exe

or use a backslash before the space, and continue as usual

/media/windows/PROGYY\ FILEZ/iTunes/iTunes.exe

---

### Post by aysiu on 2006-07-13
I don't think iTunes will work in Wine.

---

### Post by T700 on 2006-07-13
> **aysiu said:**
> I don't think iTunes will work in Wine.

It did not for me, anyway.  I've settled on Amarok for now (I'm using Kubuntu).  Good interface, nice performance, and works well with my iPod.

Paul

---

### Post by FatalTheGod on 2006-07-13
I have a 100GB of music that was all organized....alot....:P I just don't want to lose all of the info attached to  the actual file. When I add it to RhytymBox, it isn't organized like it was in my iTunes =/

---

### Post by aysiu on 2006-07-13
There are two kinds of info--one is the kind that lives in the file itself (ID3 tags and the filename); the other is the kind that is kept track of by your music-playing program (where the files are located, what ratings you've given them, how often they've been played, etc.).

Rhythmbox should read things like the song title, artist, genre, album, etc.

Your ratings and playcounts all live in the iTunes database and are not attached to the songs themselves.

---

### Post by FatalTheGod on 2006-07-13
If I changed the artist/songname/album/genre etc in iTunes, would Rhythm still read it? Most of my songs are ripped from SHN and FLAC, and when they were converted to WAV (and some MP3) I would change the options in iTunes.

Right now when I add a song, it doesn't read anything and just leaves it at 'Unknown'.

---

### Post by FatalTheGod on 2006-07-14
Ok, I was able to figure out how to organize my music and now all the file types play! However, I now have a more serious problem...

I was installing Linux because Windows would freeze....alot. Now, if I turn on my computer, start Gaim, and walk away with the screen off, it seems fine. However, when I come back, one of two things happens:

a) If I leave for more than 10 minutes or so, I come back to a locked 'shot' of the screensaver, and I need to restart the computer

b) If it's less than 10 minutes, it's fine

I then went to change the screensaver, thinking there was a problem with it. However, when it started to 'preview' the 3D savers in the small preview box, my computer froze up again. This had NEVER happened in Linux before.

I shut the screensaver off, and made sure all my video card drivers were updated. I then turned on Gaim for the night, and when I come back, the computer is frozen and my monitor won't come back from 'Sleep' since it can't read the mouse! I rebooted the computer and now I'm here begging for help!

Any suggestions? I can post any/all file info needed as well as logs, but I need to goto work soon, so when I get back I'll post everything if I can't get to it now.

Thanks for all your help so far! :)

---

### Post by T700 on 2006-07-14
Regarding the freezing problem, I'd suggest starting another thread with a descriptive title.  That way, you're more likely to get the right eyeballs on it.

Paul

---


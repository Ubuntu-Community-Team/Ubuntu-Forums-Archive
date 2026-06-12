---
title: "Help needed for NTFS partions"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by ftnalex on 2006-05-12
Hello All,

Ok, I'm very very new to Linux. I am, however, quite familiar with Windows. I had heard about this distro so I thought I'd finally give it a whirl. I have installed ubuntu onto an older system using a hard drive that was basically for data storage. The hard drive has a ntfs partion and I'd like access to that for read and writing (so I can continue to store files there). So what do I do about this? Please bear in mind that I'm EXTREMELY new to this so baby steps would be much much appreciated.  For instance, what is sudo and how do I launch it?  How do I go about installing new programs (no more .exe files in Linux).  Thanks in advance for your help and assistance.

---

### Post by Iarwain ben-adar on 2006-05-12
Hi,
seeing as i am also fairly new to linux, i'll try to help you.

First off, sudo is used in your terminal (the dos-like thingy)
To use you ntfs drives, read [this](http://ubuntuforums.org/showthread.php?t=142481&highlight=mount+ntfs)

Installing programs is quite easy (as long as you don't have dependency issues)
you downloaded a program, so it is normally compressed.
If you downloaded it on your Desktop, right-click and select "unpack here"...

Now you would see a dir with the name of the program.
Fire up your terminal (don't know where it is in Gnome) and move to your newly unpacked dir. (cd commands)

Once you're there, type
>  ./configure
make
sudo make install

Hope this helped you a bit :-)


Iarwain

---

### Post by KillrBuckeye on 2006-05-12
I've been told that Linux has some trouble WRITING to NTFS partitions.  Your best bet for data storage that will be shared between Linux/Windows systems is a FAT32 partition.  That being said, you should have no problem *reading* data from NTFS partitions.

---

### Post by cgjones on 2006-05-12
Depending on what software you want to install, there is a much easier way then the 3 step ./configure, make, make install dance. Just type the following at the terminal.
```
sudo apt-get install *program name*
```

Let's say I want to install the Firestarter firewall program, for example.
```
sudo apt-get install firestarter
```

You can browse available software [here](http://packages.ubuntu.com/).

Or the even easier method of using Add/Remove Programs (I think thats what its called) or the Synaptic Package Manager.

---

### Post by KillrBuckeye on 2006-05-12
And some programs come with executables that work just like .exe files in Windows.  Like Wolfenstein: Enemy Territory game! (My favorite)

---

### Post by zerhacke on 2006-05-12
You should know two things:

First, you can't ./configure && make && make install untill you download the build-essential package.

```
sudo apt-get install build-essential
```

Second, you can't write to NTFS, not safely, and not by default.  You can look at files all day long but you can't save them, modify them, or delete them on an NTFS drive, not by default.  If you do turn on writing to NTFS, you're probably going to break the drive's filesystem.

---

### Post by gashcrumb on 2006-05-12
At one point when I got frustrated with gentoo and went back to Windows for awhile before moving to Ubuntu I used this [http://www.fs-driver.org/]("http://www.fs-driver.org/") on the drive I keep all my music and stuff on since I had no viable way of backing it up.  It worked perfectly for the entire time I was running Windows, then when I switched back...  Well, I didn't have to do anything special to the partition except mount it...  Maybe this would work for you.

---


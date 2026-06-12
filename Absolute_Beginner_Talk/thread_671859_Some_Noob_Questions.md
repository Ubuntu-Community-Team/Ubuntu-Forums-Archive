---
title: "Some Noob Questions"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Vapourstreak on 2008-01-19
hey.

Just switched to Ubuntu 7.10 Gutsy Gibbon i386 from Windows XP.

I've figured out almost everything in two days except:

1) How do you install Java 6?  I couldn't get it to install with Java.com's RPM file, so I don't know how to install it.  None of the other threads about installing it on this site helped me, so I figured it was time to post my own.

2) How do you get Ubuntu to read my secondary Drive?  It was in NTFS formatted drive before, but I couldn't get ntfs-3g working, so I used GParted (Installed form Synapic Package Manager after Add/Remove didn't work and I couldn't find it in Automatix)  to format it to ext3 (while losing all my data :( ).  It didn't appear in the 'Computer' file folder, so I tried every available format in GParted (ext2, ext3, fat16, fat32, linux-swap, and reiserfs), but none of them helped make my hard drive appear in 'Computer'.

3) How do you work Wine?  I've downloaded some '.exe' files from the internet.  When I double-clicked them, Ubuntu told me that it poses a security risk, so it wouldn't run them.  I tried right-clicking it, and running it with Wine, but neither Wine nor the Program ever started.

Thanks a lot,
Vapourstreak

---

### Post by iansane on 2008-01-19
jre 6 there's a couple of packages jre and jdk in synaptic. RPMs are for redhat distros. Ubuntu uses .deb packages or install from source but java runtime enviroment is in synaptic package manager

---

### Post by NullHead on 2008-01-19
OK for java 6 run this from a terminal ```
sudo apt-get install sun-jave6-bin sun-java-plugin
```

You need to open fstab and edit some lines(post results for further help) view the file by typing ```
sudo gedit /etc/fstab
```

To use wine you should consult the winehq websight for more info, but basically you can do this. ```
wine program.exe
```

---

### Post by asmoore82 on 2008-01-19
And if you have used Automatix I would recommend a BackUp and Re-Install
and _not_ using it the next go 'round

to make a long story short, it is an irresponsibly-developed App that makes your
Ubuntu a ticking time-bomb that _WILL_ fail future upgrades:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by NullHead on 2008-01-19
We need not start an automatrix rant here lest stay on topic.

---

### Post by asmoore82 on 2008-01-19
> **NullHead said:**
> We need not start an automatrix rant here lest stay on topic.

As soon as I become aware that a fellow human's Linux system is in a bad state,
it is my duty to let them know; I've seen too many "Ubuntu *crashed* after update" threads.

---

### Post by Vapourstreak on 2008-01-19
Thanks for the help, guys.  One more question, thought:

I'm sorry, but I don't understand the Run in terminal thing.  It just says Java is not found.  What is the filename for the Java 6 Runtime enviroment in the Synapic Package Manager?

I removed Automatix with synpatic.  thanks for the tip.

I tried to use wine again, and it worked :)!!!

---

### Post by jordanmthomas on 2008-01-19
> **NullHead said:**
>  ```
sudo gedit /etc/fstab
```

You should use gksudo instead of sudo when running programs that connect to your xserver.

> **Vapourstreak said:**
> Thanks for the help, guys.  One more question, thought:

I'm sorry, but I don't understand the Run in terminal thing.  It just says Java is not found.  What is the filename for the Java 6 Runtime enviroment in the Synapic Package Manager?

I removed Automatix with synpatic.  thanks for the tip.

I tried to use wine again, and it worked :)!!!

sun-java6-jre is the name of the package.
Make sure the multiverse repository is enabled.  (You can do this with Synaptic..look in the menus for it)

---

### Post by nkobel003 on 2008-01-19
> **Vapourstreak said:**
> I'm sorry, but I don't understand the Run in terminal thing.  It just says Java is not found.  What is the filename for the Java 6 Runtime enviroment in the Synapic Package Manager?

Select Menu>Accessories>Terminal and type in the commands:

```
gksudo apt-get install sun-jave6-bin sun-java-plugin
```

from there, you should be prompted to answer [y/n] and of course type 'y' for yes (and accept) or 'n' for no followed by the ENTER key.

Run in terminal simply means to enter code into a terminal.

---

### Post by jordanmthomas on 2008-01-19
> **nkobel003 said:**
> Select Menu>Accessories>Terminal and type in the commands:

```
gksudo apt-get install sun-jave6-bin sun-java-plugin
```

from there, you should be prompted to answer [y/n] and of course type 'y' for yes (and accept) or 'n' for no followed by the ENTER key.

Run in terminal simply means to enter code into a terminal.

heh, just sudo would have been fine in this one.  :lolflag:

---

### Post by Vapourstreak on 2008-01-19
o w8... the hard drive is still nto showing up.. help, anyone?

---


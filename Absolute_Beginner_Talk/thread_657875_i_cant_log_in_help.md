---
title: "i cant log in??? help??"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by the1nonlytk on 2008-01-04
i think i might have deleted some files how can i log in again?

---

### Post by The Tronyx on 2008-01-04
Is there any error message?  Is your caps lock key on?  Are you **sure** you are entering the password correctly?  Did you try logging in with the username root and your password?

---

### Post by the1nonlytk on 2008-01-04
theres a black screen an it says login and password i enter it and it tells me that last time i logged in and it says ubuntu is a freesoftware.... ect
and it says my user name@myusernames laptop:~$ and its blinking after that

---

### Post by The Tronyx on 2008-01-04
so there is no GUI?

---

### Post by PeterJS on 2008-01-04
Ah, you have logged in but just aren't getting a graphical interface. X breaks happen all the time. Once you get logged in run:
```

sudo dpkg-reconfigure xserver-xorg

```That should rebuild your x configuration after asking you a few questions. When that's done you should be able to reboot and login graphically.

EDIT:
I always get that package name wrong

---

### Post by ~LoKe on 2008-01-04
After you get to the black screen and log in, type this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then:
```
sudo /etc/init.d/gdm restart
```

---

### Post by the1nonlytk on 2008-01-04
wats that

---

### Post by the1nonlytk on 2008-01-04
> **~LoKe said:**
> After you get to the black screen and log in, type this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then:
```
sudo /etc/init.d/gdm restart
```

i put in the 1st code and it showed me the same thing and the second code wont work

---

### Post by The Tronyx on 2008-01-04
after you log in to the blinking cursor, try running 'startx' without the quotes.  What happens?

---

### Post by the1nonlytk on 2008-01-04
i typed in startx and i shows me a screen but thats all it shows

---

### Post by The Tronyx on 2008-01-04
> **the1nonlytk said:**
> i typed in startx and i shows me a screen but thats all it shows

And you tried "sudo dpkg-reconfigure -phigh xserver-xorg" right?

---

### Post by the1nonlytk on 2008-01-04
is there a command that allows me to delete everything or format it??
cuz i have a windows xp cd but i need space for it

---

### Post by PeterJS on 2008-01-04
> **the1nonlytk said:**
> i typed in startx and i shows me a screen but thats all it shows

With a "pretty" gray pattern and a big ugly X for a cursor?

---

### Post by the1nonlytk on 2008-01-04
lol yes

---

### Post by PeterJS on 2008-01-04
> **the1nonlytk said:**
> lol yes

Well that's a good sign, you graphics config is working, it's just not loading up the desktop. What happened when you ran:
```

sudo /etc/init.d/gdm restart

```

---

### Post by the1nonlytk on 2008-01-04
its telling me package 'cserver-xorg' is not installed

---

### Post by the1nonlytk on 2008-01-04
it says /ect/init.d/gdm command not found

---

### Post by the1nonlytk on 2008-01-04
it doesnt do anything

---

### Post by PeterJS on 2008-01-04
> **the1nonlytk said:**
> its telling me package 'cserver-xorg' is not installed

Huh, I wonder how you managed to get that un-installed, it's kinda important. Try:
```

sudo apt-get install ubuntu-desktop

```

Then try reloading gdm again.

---

### Post by the1nonlytk on 2008-01-04
i think its working cuz its loading a bunch of stuff

---

### Post by the1nonlytk on 2008-01-04
phew it worked now how do i delete everything and install windows xp cuz i have a cd

---

### Post by The Tronyx on 2008-01-04
> **the1nonlytk said:**
> phew it worked now how do i delete everything and install windows xp cuz i have a cd

lol...

Are you being serious right now?

---

### Post by the1nonlytk on 2008-01-04
lol umm i was can u help me get mplayer and update it to 7.1 or w/e the newest one is?

---

### Post by ajmorris on 2008-01-04
ok, so to format the HD, you did not need to fix ubuntu first, to re-install XP onto your HD, put in the cd, boot off it, then when the XP installer gets to choosing where to install to, just tell it to format the partition, that it will say is unknown, because it cant recognise linux partitions.

---

### Post by ajmorris on 2008-01-04
> **the1nonlytk said:**
> lol umm i was can u help me get mplayer and update it to 7.1 or w/e the newest one is?

ok, now im a little confused, do you wish to keep ubuntu, and dual boot it with XP, or do you want XP solely on your hard disk?

---

### Post by the1nonlytk on 2008-01-04
i jus want xp but when i tired to boots  it it told me i need space for it so i tired to remove ubuntu and it all got messed up i just want xp in there or a way to install mplayer and its nothing i need to upgrade it to ubuntu 7.1

---

### Post by PeterJS on 2008-01-04
> **the1nonlytk said:**
> i jus want xp but when i tired to boots  it it told me i need space for it so i tired to remove ubuntu and it all got messed up i just want xp in there or a way to install mplayer and its nothing i need to upgrade it to ubuntu 7.1

We're trying but can't make heads or tails of what you're asking. What I think the goal is to completely remove ubuntu and re-install windows, correct? How does mplayer relate to this?

---

### Post by ajmorris on 2008-01-04
ok, from booting the XP cd, before getting to the option where you try to install XP to the Hard Drive, there is an option to format the partitions, i dont remember exactly where, because it has been a long time since i used windows, if you really cant find it, you can also use the most unused page on the Microsoft website, this will tell you everything you need to remove ubuntu, and install XP: [http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

---

### Post by GSF1200S on 2008-01-04
> **the1nonlytk said:**
> i jus want xp but when i tired to boots  it it told me i need space for it so i tired to remove ubuntu and it all got messed up i just want xp in there or a way to install mplayer and its nothing i need to upgrade it to ubuntu 7.1

Ok... what exactly do you need? You have the following options:

1) Fix Ubuntu and use Add/Remove programs to install mplayer. If a newer version of mplayer is what you need, then well need to compile it from source.

2) Remove Ubuntu and install Windows in its place, hence having no mplayer at all and resolving that issue nicely.

3) Fix Ubuntu, resize the portion of your hard drive to give Windows more space, and continue to dual boot, giving you both Windows, a fixed Ubuntu and mplayer.

Since you have 7.04, you could upgrade to 7.10 on Ubuntu.

We dont know exactly what you need, so if you could be more clear, we could help you ;)

---

### Post by the1nonlytk on 2008-01-04
yes i want to remo ubuntu and get windows forget mplayer

---

### Post by the1nonlytk on 2008-01-04
i just want windows on my hard drive and remove ubuntu

---

### Post by The Tronyx on 2008-01-04
Insert an XP recovery disk and format the drive?

---

### Post by the1nonlytk on 2008-01-04
how do i format it

---

### Post by The Tronyx on 2008-01-04
Put the Windows recovery CD in your drive, restart the computer and watch the magic happen.

---

### Post by ajmorris on 2008-01-04
hi, you may wish to refer to my above post, that microsoft page will actually help you :) except, their first instruction is wrong, where it says to type fdisk and press enter
you must type fdisk /dev/blockdevice (either hda or sda, then change the a for the numbered HD if applicable, eg, hdb or sdb for the second hardisk) also, it must be run as root, and sudo fdisk -l will tell you whether your Hard disk is sda or hda
Hope it helps you :)

---

### Post by the1nonlytk on 2008-01-04
i have a windows cd now a recovery cd?

---

### Post by The Tronyx on 2008-01-04
> **the1nonlytk said:**
> i have a windows cd now a recovery cd?

Whatever it is you have, recovery CD, windows CD, put it in your drive and restart your computer.

---

### Post by the1nonlytk on 2008-01-04
so i should type  fdisk /dev/blockdevice(hda) in terminal?

---

### Post by ajmorris on 2008-01-04
> **the1nonlytk said:**
> so i should type  fdisk /dev/blockdevice(hda) in terminal?

no, if sudo fdisk -l, reveals that /dev/hda is your hardisk, on the ubuntu live cd, you type sudo fdisk /dev/hda

This is an example of how to tell the Hard Disk from sudo fdisk -l, mine outputs this at the top: 
"Disk /dev/sda: 80.0 GB, 80026361856 bytes"

so i would do sudo fdisk /dev/sda

but, make sure you follow the guide at: [http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

it walks you through using fdisk :)

---

### Post by the1nonlytk on 2008-01-04
okay i put sudo fdisk /dev/hda
it said 

the number of cylinders for this disk is set to 1467.
theres nothing wrong with that but this is later then 1024
and cuold in certail setups cuase problem with
1) software that runs at boot
2) boothing a partiioning software for OSs

---

### Post by the1nonlytk on 2008-01-04
oh 1 more thing im not trying to reinstall windows im doing it from sctatch

---


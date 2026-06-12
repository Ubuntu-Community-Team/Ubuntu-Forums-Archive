---
title: "Transfering files from a Windows based hdd to ubuntu?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-11
is it possible to pull media and other files from a NTFS to this file system? i did it with linux, ahh i forgot what version or the name of it,, but i tried the live CD and it worked fine,, except my audio drivers,, so,, is it possible while not formatting the drive and keeping windows intact to transfer files from my other hard drives onto this one?:confused:

---

### Post by bren on 2007-08-11
you need to install ntfs-3g

sudo apt-get install ntfs-3g

then configure it via

ntfs-config

you can then write to ntfs partitions (default is read only)
if you can't read then see other instructions on this forum about command chown and permissions

bren

---

### Post by jake16424 on 2007-08-11
> **bren said:**
> you need to install ntfs-3g

sudo apt-get install ntfs-3g

then configure it via

ntfs-config

you can then write to ntfs partitions (default is read only)
if you can't read then see other instructions on this forum about command chown and permissions

bren


E: Couldn't find package ntfs-3g

---

### Post by ron999 on 2007-08-11
...........

---

### Post by jake16424 on 2007-08-11
> **ron999 said:**
> ...........

:(

jacob@jacob-desktop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g
jacob@jacob-desktop:~$

---

### Post by starcraft.man on 2007-08-11
> **bren said:**
> you need to install ntfs-3g

sudo apt-get install ntfs-3g

then configure it via

ntfs-config

you can then write to ntfs partitions (default is read only)
if you can't read then see other instructions on this forum about command chown and permissions

bren

Just a note but if I get ya right OP you only want to move files Windows --> Ubuntu and that can be done without these drivers cuz Ubuntu has read drivers. If you installed Ubuntu and left your Windows partitions there they should be automatically mounted on your desktop.

As for the problem you had finding the package, I believe you don't have all the sources in your sources.list that are needed. Pleas read my blue guide to learn about that. Do install the drivers though, always a good thing for more support. Hope that helps.

---

### Post by jake16424 on 2007-08-11
> **starcraft.man said:**
> Just a note but if I get ya right OP you only want to move files Windows --> Ubuntu and that can be done without these drivers cuz Ubuntu has read drivers. If you installed Ubuntu and left your Windows partitions there they should be automatically mounted on your desktop.

As for the problem you had finding the package, I believe you don't have all the sources in your sources.list that are needed. Pleas read my blue guide to learn about that. Do install the drivers though, always a good thing for more support. Hope that helps.

nopers, ive tried to access them and it says, faild to mount drive, or media,, one of the two,,

---

### Post by splintercellguy on 2007-08-11
*sudo apt-get install ntfs-config

---

### Post by jake16424 on 2007-08-11
> **splintercellguy said:**
> *sudo apt-get install ntfs-config

jacob@jacob-desktop:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config
jacob@jacob-desktop:~$
:confused:

---

### Post by starcraft.man on 2007-08-11
> **jake16424 said:**
> jacob@jacob-desktop:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config
jacob@jacob-desktop:~$
:confused:

Like I said, please check my blue link in my sig for details on checking your sources list and editing. Once you enable the right ones I'm sure you will be able to install ntfs-3g. Doing the same command over and over won't work though.

As for the drive, I'm not sure the problem. If after installing ntfs-3g it doesn't work right, I assume it's a permissions issue and if that's the case please read through guides 1-4 of the orange link (far left) to give yourself permission. I know it's quite a bit of reading, but it's worth it and will answer questions.

---

### Post by jake16424 on 2007-08-11
thanx:)

---

### Post by starcraft.man on 2007-08-11
> **jake16424 said:**
> thanx:)

No problem. You got it working then? Oh and use the ubuntu guide sources.list (it's at the top), it has all the sources you need and combined with my explanation you can install almost anything. Best of luck.

---

### Post by jake16424 on 2007-08-11
no, didn't get it working,, read the index,, nothign seemed realivent, ^_^... ill mess with it some,, thank you for your time.

---

### Post by Frak on 2007-08-11
Run
```
sudo aptitude update
```
and post your output.

---

### Post by jake16424 on 2007-08-11
> **Frak said:**
> Run
```
sudo aptitude update
```
and post your output.

--------------------------------------------------------------
 for the record i like the texas warrenty, =)


jacob@jacob-desktop:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config
jacob@jacob-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Fetched 4B in 21s (0B/s)
Reading package lists... Done
jacob@jacob-desktop:~$

---

### Post by starcraft.man on 2007-08-11
> **jake16424 said:**
> no, didn't get it working,, read the index,, nothign seemed realivent, ^_^... ill mess with it some,, thank you for your time.

Uh, I told ya it was an issue with your sources list. From the index of my guide (in blue)...

>  Index
0) Introduction
1) Basics
2) Installing with CLI
[B]2a) Graphical Editors and the Sources List
2b) CLI Editors and the Sources List[/B]
2c) Authentication Keys
2d) Updating
2e) Installing Software
2f) Advanced Package Management
3) Installing with GUI
**3a) GUI and Sources List**
3b) Skip!
3c) Authentication Keys
3d) Updating
3e) Installing Software
4) Lexicon
4a) Lexicon of Terms
5) Extra sections
5a) Add/Remove GUI
5b) Differences Across Versions
5c) Extra Resources

I was implying you read those sections (and by extension the related ones depending on your preference of GUI or terminal (CLI) install). I've taken care to document it very well (I think at least) and IMO it's a good read front to back to know more about your OS and basic install functions. What you do is up to you, I just provide options.

---

### Post by jake16424 on 2007-08-11
> **starcraft.man said:**
> Uh, I told ya it was an issue with your sources list. From the index of my guide (in blue)...



I was implying you read those sections (and by extension the related ones depending on your preference of GUI or terminal (CLI) install). I've taken care to document it very well (I think at least) and IMO it's a good read front to back to know more about your OS and basic install functions. What you do is up to you, I just provide options.

hehe,, didnt see the gui then source list,, O_O ,, now i feel stupid,, :( haha,,

---

### Post by starcraft.man on 2007-08-11
> **jake16424 said:**
> hehe,, didnt see the gui then source list,, O_O ,, now i feel stupid,, :( haha,,

That's ok, just be patient and take it easy. It's good to read things and learn, going to Ubuntu isn't like just flipping a switch it requires patience and time. Have a nice read and any questions based on the guide feel free to ask. Best of luck.

---

### Post by jake16424 on 2007-08-11
i don't have a thing that says software sources,, i looked about 4 times,, O_o

---


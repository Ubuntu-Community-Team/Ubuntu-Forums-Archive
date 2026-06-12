---
title: "Browsing the folders"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by Eniac on 2006-03-09
Heya guys.

First, kudos for making such an easy linux distro, easy enough that windows retards like me can install it from the first try :)

A friend of mine had installed gentoo on my computer before but i found myself not using it because I couldnt handle it :)

So anyway, I installed ubuntu on my old P3 with the idea of transforming it into an autonomous PVR. Last night i was browsing the computer and it was cool but I was really confused about how the folders are set up.

Like I said, I've been using windows all my life and I see that linux doesn't quite work like windows (obviously :D)

For instance... last night, I downloaded mythtv and tried to put it somewhere on my hard disk, in windows, it would have been d:\downloads. but in ubuntu/linux I can't do that. is there a place on the hard drive where I'm supposed to be placing my downloads ? I like the idea of four desktops but there's no way I'm going to put everything on my desktops.

I'd just like someone to explain me how the folders works, what can users see and cannot see, can and cannot do. Why are there always a ton of folders no matter where I go in the folder tree ? tmp, bin, usr ... etc (i actually know what these are, but there are plenty others that i have no clue)

I'm not afraid of command lines, I was born in the DOS world and i kind of miss it too, dont be afraid to paste some if you think its useful.

..also...on a sideline...how do I install a program ? :) Like i said, i downloaded mythtv, I untar'ed it but i see no setup program. im sure thats a very noob question ha ha ha!

k, thanks.

Eniac

---

### Post by kaamos on 2006-03-09
The user is supposed to place files under his/hers home directory. So for example you might want to create a folder "downloads" in your home and it would be ~equivalent to d:\downloads. The when you download something, just navigate to /home/eniac/downloads.

And basicly you don't have to worry about the plentiness of folders in the drive root (/), because you are just about never supposed to be doing anything in there. :)

I've never installed or used MythTv, but it seems to be available in the repos. So the generic installation instructions should probably get you going. -> [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by trorion on 2006-03-09
Some quick notes:
If you cd to ~/ it takes you to home.
```
cd ~/
```=/home/*yourusername*
```
cd ~/Desktop
```=/home/*yourusername*/Desktop

You'll need to learn to use your sudo command to do things.  If you try to do something and it does..nothing; you may have to do sudo to get it running.  sudo gives you "administrator" privliges for that command.
```
sudo apt-get install mythtv
```
This means:
-sudo: do the following as root (aka SuperUser, SU, administrator)
-apt-get: This program installs packages in the .deb format that are pre-set and available (you'll learn this)
-install: an argument passed to apt-get program (this one means install it)
-mythtv: another argument for apt-get.  This means you want apt-get to find "mythtv"

If you have downloaded a package rather than getting it automatically (apt-get) you would use dpkg instead of apt-get.
```
man dpkg
```
will give you information on it.

Other option: go to System->Synaptic then find mythtv.  I think it's in the base repositories.  This is a graphical version (kind of) of apt-get.

---

### Post by meborc on 2006-03-09
for more on system tree (folders) [https://wiki.ubuntu.com/LinuxFilesystemTreeOverview](https://wiki.ubuntu.com/LinuxFilesystemTreeOverview)

---

### Post by Brunellus on 2006-03-09
[QUOTE=Eniac]Heya guys.

First, kudos for making such an easy linux distro, easy enough that windows retards like me can install it from the first try :)

A friend of mine had installed gentoo on my computer before but i found myself not using it because I couldnt handle it :)

So anyway, I installed ubuntu on my old P3 with the idea of transforming it into an autonomous PVR. Last night i was browsing the computer and it was cool but I was really confused about how the folders are set up.

Like I said, I've been using windows all my life and I see that linux doesn't quite work like windows (obviously :D)

For instance... last night, I downloaded mythtv and tried to put it somewhere on my hard disk, in windows, it would have been d:\downloads. but in ubuntu/linux I can't do that. is there a place on the hard drive where I'm supposed to be placing my downloads ? I like the idea of four desktops but there's no way I'm going to put everything on my desktops.

I'd just like someone to explain me how the folders works, what can users see and cannot see, can and cannot do. Why are there always a ton of folders no matter where I go in the folder tree ? tmp, bin, usr ... etc (i actually know what these are, but there are plenty others that i have no clue)

I'm not afraid of command lines, I was born in the DOS world and i kind of miss it too, dont be afraid to paste some if you think its useful.

..also...on a sideline...how do I install a program ? :) Like i said, i downloaded mythtv, I untar'ed it but i see no setup program. im sure thats a very noob question ha ha ha!

k, thanks.

Eniac[/QUOTE]
You can change the download destination of the files through the Options in Firefox

Tools-->Options--->Download

and you should see a download destination folder.

In general, on a Linux system, you will be expected to keep everything that is NOT system-critical in your home directory (/home/username).  The desktop you see in GNOME/KDE is actually a sub-directory of the home directory:

/home/username/Desktop

(note that these are case-sensitive).

If typing all these absolute directory paths gets tiresome, you can use the tilde key on your keyboard (~) which is shorthand for "this users' home dir".  so, for instance:

```
brunellus@funes$ cd ~/Desktop 
```

would bring me to /home/brunellus/Desktop

---


---
title: "how to install  --- complete Newbie!"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by sceon on 2006-12-20
I'd like to install software I have in cue/bin format. 
But I can't acces these files in linux, so I found a virtual cdrom program called cdemu with a so called simple install. Well, not for this newbie :)

[INDENT]installation step1:
you need the source of your current running kernel.
/lib/modules/$(shell uname -r)/build/include needs to point at it.[/INDENT]

This is completely chinese for me, I dont understand anything. Can someone explain this to me?

I also tried the "sudo aptitude install cdemu" command, but yet no new application appear in my menu (this is another newbie question: how do I start programs after I install the with Synaptic?)

Thanks for your help guys!

---

### Post by padre999 on 2006-12-20
Normally you install software using Synaptic. In Ubuntu most of the software you would need is stored as packages in online libraries, so called repositories or repos. With synaptic it is very easy to install a program. But you should enable some repositories like "universe" and "multiverse" first before using synaptic if you want the full resources.

To learn more about these things see [https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

---

### Post by bernied on 2006-12-20
Your chinese...
The kernel is the basis of your operating system. A kernel is a core if you like. This is the bit that was originally written by (and still developed by) Linus Torvalds. What actually runs is machine code, which is understood by the processor chip in your computer. But (almost) no-one writes machine code, so the source code is written in a programming language which is (almost) understandable by human beings, then compiled into machine code. So, you won't generally have the source code for your kernel, but you can get it through you package management system (aptitude, apt-get etc). 

That /lib/modules/... gubbins is a location on your filesystem, the bit in the middle is a clever way of inserting the version of your kernel (because they change all the time) into the location (path), and the phrase 'needs to point at it' means that the location itself is actually a link to another location - this is like a shortcut in windows, a file that points to another file (in this case the 'file' that is pointed to is a directory).

However, if your 'sudo aptitude install cdemu' command worked (did it? did you get any unfriendly error messages?), then you may not need to worry about the above, because it may sort that stuff out for you. Aptitude is a package manager, packages are an easy way of installing software (sudo, by the way, is used to run software with root - or administrative - privileges, which are not normally available to the regular user).

If the software is installed correctly, usually just typing its name is sufficient to make it run, but it may need some more instructions. Most software will tell you what it needs, you just need to learn to understand what it is telling you.

My I ask what software you are actually trying to install? What is the end point that you are trying to reach?

---

### Post by sceon on 2006-12-20
The "sudo aptitude install cdemu" command didn't work, it couldn't find the package.

In the end I'm trying to install Matlab, which installation cd I have in cue/bin format on my hard disk. 

I thought that I could simply make a virtual disk like with daemon tools in windows, and install from there. 
But I failed ](*,) 

So, how can I install this software I have in cue/bin format? 
If possible with CDemu, how do I get this program to install?

And furthermore, can I get the programs, that I install with Synaptic, in the upperleft menu?

Lots of newbie questions, I know :)
Thx!

---

### Post by bernied on 2006-12-20
To answer your second question first, you can add entries one by one, using the menu editor. I'm sorry I don't know the details, as I use Kubuntu (which uses a different window system - KDE), but if you google something like 'ubuntu menu add application' that should tell you.

Or, you could add the 'Debian Menu', which automatically lists (nearly) all applications on your machine. Again google 'ubuntu debian menu howto' or similar.

So this cd, you have this as a single file, yes? So, if this is a CD image then you can 'mount' it in order to access its contents. You don't need cdemu, this capability is built into linux.

To do this, open a terminal, then,
first create a mountpoint - a location on the filesystem where the cd will 'appear'
```
sudo mkdir /mnt/matlab-cd
```
then, mount the image at the location
```
sudo mount -o loop path/to/matlab.bin /mnt/matlab-cd
```
in this command you will have to replace 'path/to/' with the actual location of the file. If it is on your desktop, this would be '~/Desktop/' (the '~' is shorthand for your home directory)
then, go to the mountpoint and have a look at what's there
```
cd /mnt/matlab-cd
ls
```
Look for a file called README, to view it, use
```
less README
```

---

### Post by bernied on 2006-12-21
did it work?

---

### Post by jaybombalous on 2006-12-24
> mount: you must specify the filesystem type

I tried that and this is what I ended up with??? Complete new user to linux myself. :(

---

### Post by bernied on 2006-12-24
sorry, my mistake, the filesystem is probably iso9660, so
```
sudo mount -t iso9660 -o loop path/to/matlab.bin /mnt/matlab-cd
```
You could also burn the image to cd - in kde the program for this is k3b. Look in the multimedia part of the applications menu. But you want to burn a cd image, not burn the file.

---


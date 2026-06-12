---
title: "Using WINE for programs via Flash Drive"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by CD27 on 2008-01-07
Hi folks,

I've done some searches on this site, but so far nothing has helped me :(. I've done some google searches and stuff and i just can't figure it out. I got and installed Ubuntu Linux because i am absolutely sick and tired of Windows and i don't really want to go to mac. So i went with Linux, but my only problem was that i couldn't figure out how to run any programs in linux. It won't accept the .exe files. Okay, so i did some digging and heard about WINE. So i installed it and tried to get it to work, but i'm trying to run all my programs from my USB Flash Drive.

When i go into the terminal and type: "wine blender.exe" it tells me that it can't find blender.exe in "system32". Why is it looking in system32? I did a bit of extra work and found the exact file location and everything, typed it all up and then tried it and give kept giving me errors saying it can't find it. So i tried some other programs...why won't it work?

I thought WINE has some kind of GUI that i could see with, because when i try going to blender itself, right clicking it, and saying "open with" and searching for wine and using it, it does nothing. I want to use my version of Blender because i'm used to it and it's more familiar to me and easier to run. I also have other programs and scripts that run with blender that i can't exchange over. Is there not an easier way to install programs on Linux? If an alternative OS to windows is being created it could at least have the ability to run and use .exe files....:(

I have absolutely no idea what i'm doing. I barely know how to use linux, much less actually install files with it, even much lesser using wine. I'm good with Windows, i'm an IT, but i simply don't understand the transfer between windows and linux. Can anyone help me without requireing me to read a book?

God Bless and In Him,

Eric Wright

---

### Post by CD27 on 2008-01-07
anyone?

cd

---

### Post by doorknob60 on 2008-01-07
Are you sure wine is actually installed? If it is, the blender installer just might not work with wine, as not every program is compatible.

---

### Post by amingv on 2008-01-07
This is what you're looking for: press Alt+F2, and input 'winefile' (without the quotes). Navigate to your flash drive (usually /media/disk) and try to open the file from there (assuming wine is fully installed).

Also, if you're using Blender (the 3D modeler, I guess) you can install the Linux-compatible version by opening a terminal and typing

```
sudo apt-get install blender
```

The way you install programs in Linux is quite different from Windows (thank goodness). Linux does not run windows exe files natively.

In any case, this may be helpful too:

[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by CD27 on 2008-01-08
I've already got the windows version installed on the flash drive, i just want to run it now. When i go into synaptic it tells me it's already open and everything. Anyways, i'll try what you said there and take a look at this link. thanks guys!

cd

---

### Post by suber samurai on 2008-01-12
Wine works well for me to run applications from a flash drive.  I'm using the [Wine Desktop LivePC]("http://www.moka5.com/node/1620").  I just installed the Win32 version of Blender in ontop of it.  It didn't make a shortcut for me automatically which is obnoxious but it works fine.  

The problem I ran into for awhile was that I forgot to quote the path to blender.exe when I entered it at the command line.  

me@localhost / $ wine --version
wine-0.9.48

---

### Post by Paqman on 2008-01-12
Wine is very hit and miss. You're much better off avoiding the whole hassle of trying to get it to work by using native Linux applications.

---


---
title: "Having both Ubuntu and Edbuntu"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by lonoy on 2007-06-22
Hi,

I tried the Edubuntu live CD the other day and my 9 year fell in love with some of the programs on there. I am using Feisty at present and was wondering the following:

Can I set up Ubuntu and have my son change to Edubuntu via switch users or does it have to be installed as a completely separate system and accessed via boot options. I know Edubuntu shares the same repository as Ubuntu and I could load the programs onto my Ubuntu but I would prefer to have the complete Edubuntu "show" installed so I can try it out as his school is interested in it as well.

Second question: My sons childcare have a old computer (128meg ram and 10 gb HD) laying around which I was hoping to load a version of Ubuntu on. I tried loading Edubuntu but it asks for 256 ram so I had no success. I believe I should be able to load Xubuntu on it from what I have read. The thing is the computer will not have internet access so I am wondering is it possible to transfer some of the education programs from the Edubunu CD to a computer with a Xubuntu set up?

Thanks in advance.
Regards
Lonoy

---

### Post by diatribe on 2007-06-22
I doubt that even xubuntu would run well with 128mb of ram, maybe fluxbuntu.  in any case you would need the alternate install disk.  Also why would you want ubuntu and edubuntu, they are the same thing just different schemas I think

edit: yes you could have him log into his account and have it be the edubuntu theme and then have a seperate account for yourself that uses whichever theme/DE you want

---

### Post by master_kernel on 2007-06-22
Fortunately for you, the repositories provide an easy way to install Edubuntu on your current desktop.
This will build dependencies and install the Edubuntu meta package.
```
sudo apt-get build-dep edubuntu-desktop
```
```
sudo apt-get install edubuntu-desktop
```

After installation, this package may or may not change your desktop settings (wallpaper, icons, GDM theme, etc.) and the usplash (bootup screen). Your desktop icon theme can be edited through 'System > Preferences > Theme' in the top right corner of your screen. The GDM theme can be changed through 'System > Administration > Login Window'. The usplash screen can be changed using the following codes (entered through a terminal, of course):
```
sudo update-alternatives --config usplash-artwork.so
```
And after selection:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

As for your second question, the following link gives you step-by-step instructions on how to install Ubuntu (not Edubuntu) on low memory systems: [COLOR="Blue"][https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)[/COLOR]
However, in my opinion, this is NOT the most user-friendly or efficient way to install it. My recommendation is to download the [COLOR="Blue"][Ubuntu alternate CD]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso")[/COLOR], which gives support for low memory systems/older computers (32 MB of RAM) and just install the Edubuntu meta package using the code I gave you above. This process will be MUCH easier and will provide you with a full Edubuntu system quicker.

Good Luck!

---

### Post by lonoy on 2007-06-22
Fortunately for you, the repositories provide an easy way to install Edubuntu on your current desktop.
This will build dependencies and install the Edubuntu meta package.
Code:

sudo apt-get build-dep edubuntu-desktop

Code:

sudo apt-get install edubuntu-desktop



Thanks to all for your replies, much appreciated.

 I just need clarification though: by loading Edubuntu from the repos described above will that override my existing configuration or allow me to run both the standard Ubuntu that I have now then allow my son to login into Edubuntu as required?

Cheers
Lonoy

---

### Post by rocknrolf77 on 2007-06-22
Just make another unpriveliged user and set it up with some icons for the children apps on the desktop maybe. Like gcompris and other educational software and games. And the edubuntu artwork :)

Gnu/linux is made as a true multi user system

---

### Post by master_kernel on 2007-06-22
> **lonoy said:**
> Fortunately for you, the repositories provide an easy way to install Edubuntu on your current desktop.
This will build dependencies and install the Edubuntu meta package.
Code:

sudo apt-get build-dep edubuntu-desktop

Code:

sudo apt-get install edubuntu-desktop



Thanks to all for your replies, much appreciated.

 I just need clarification though: by loading Edubuntu from the repos described above will that override my existing configuration or allow me to run both the standard Ubuntu that I have now then allow my son to login into Edubuntu as required?

Cheers
Lonoy

It will allow you to run both Ubuntu and Edubuntu on your computer. edubuntu-desktop is a meta package that consists of all the programs needed to run Edubuntu. Installing it will allow all users to run the programs included in Edubuntu.

P.S.: I just followed my directions to make sure they work out OK for you. If you create a new user, it automatically uses the Edubuntu theme and icon set.
[COLOR="Red"]
EDIT: I'm not sure if I answered your question, but yes.[/COLOR]

---

### Post by lonoy on 2007-06-22
Thanks again.

I did as instructed above. I have created a new user for my son and the Edubuntu desktop appears while all my settings in my profile stay as they were:desktop etc included.

Only thing is that I still have to download contents of the Applications/Education folder when I am in my sons login. I was hoping the Edubuntu set up for him would appear exactly as the CD is. Reason being that he can quickly learn his way around a new setup and teach others at his school.

Cheers
Lonoy

---

### Post by lazyart on 2007-06-22
> **lonoy said:**
> Only thing is that I still have to download contents of the Applications/Education folder when I am in my sons login.

I don't follow you here.  What exactly do you mean by having to "download contents of the Applications/Education folder"?

---

### Post by lonoy on 2007-06-22
I have to open Applications then Add/Remove programs then select the individual programs within the Education folder as the Folder is showing empty. On the Edubuntu CD the folder had a dozen different programs  in it already loaded from the CD. I did not have to download them from the repository.

---

### Post by master_kernel on 2007-06-27
> **lonoy said:**
> I have to open Applications then Add/Remove programs then select the individual programs within the Education folder as the Folder is showing empty. On the Edubuntu CD the folder had a dozen different programs  in it already loaded from the CD. I did not have to download them from the repository.
That is very odd. The edubuntu-desktop package is supposed to include all of the programs. Maybe the developers left this out unknowingly.

---


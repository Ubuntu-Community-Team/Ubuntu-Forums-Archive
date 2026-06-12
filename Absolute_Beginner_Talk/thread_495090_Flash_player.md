---
title: "Flash player"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-07-07
I have installed the package swf-player which was described as flash player for Mozilla with apt-get, but I still can't play .swf files. Which packages do I need? I've also tried to install it manually by downloading both the tar.gz and.rpm file from their homepage, but the installation wouldn't work.

---

### Post by Malibu Illusion on 2007-07-07
Are you trying to play flash files in Firefox?  What architecture are you on?  AMD64?  x86?

---

### Post by kcirtap on 2007-07-07
Amd64

---

### Post by Malibu Illusion on 2007-07-07
Download the [Flash tarball](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash).

```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Extract it and move the necessary to the plugins directory:
```
tar -zxf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux/
mv *flashplayer* ~/.mozilla/plugins
```

Install nspluginwrapper:

```

sudo aptitude install nspluginwrapper

```

Install a wrapper version of the Flash plugin for your 64-bit browser:

```

nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so

```

Close and reopen Firefox.  Type this into the address bar:

```

about:plugins
```

You'll see Flash listed, and it should work.

Take care.

---

### Post by kcirtap on 2007-07-07
When I type the following line: mv *flashplayer* ~/.mozilla/plugins complains that it's not a category and when I tried to install the package it couldn't find nspluginwrapper.

**By the way:**
I get the following error message when I try ./flashplayer-installer: 
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

Still i'm always redirected to that page where you download that file.

---

### Post by Malibu Illusion on 2007-07-07
You need to install the enable the multiverse repositories in /etc/apt/sources.list in order to get nspluginwrapper from there, then perform a:

```
sudo apt-get update
```

Try this to move the files:

```

mv flashplayer.xpt ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
```

If that doesn't work for whatever reason, just copy/paste them into the /home/user/.mozilla/plugins directory graphically.

> **kcirtap said:**
> **By the way:**
I get the following error message when I try ./flashplayer-installer: 
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

Still i'm always redirected to that page where you download that file.

I didn't tell you to execute the installer for a reason. ;)  There is no native AMD64 flash player, hence the need for the plugin wrapper to use the 32-bit player within the 64-bit browser.

---

### Post by kcirtap on 2007-07-07
Sorry for being so slow on this. I have done the following things now:

* Moved the two files
* The multi repositories thing was already activated.
* Performed the sudo apt-get update (does this update the system?)
* and tried the line 'sudo aptitude install nspluginwrapper' again. I thought it worked this time because it came further than last time, but it still complains about not finding the package with that name in the end.

---

### Post by Malibu Illusion on 2007-07-07
Okay, seems as though it's only in the multiverse repos for Gutsy, my bad.

Get some dependancies:

```
sudo aptitude install ia32-libs-gtk ia32-libs linux32 lib32asound build-essential
```

Download the [tarball](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.4.tar.bz2)

```
wget http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.4.tar.bz2
```

Extract it:

```
tar -xf nspluginwrapper-0.9.91.4.tar.bz2
```

Go to the directory:

```
cd nspluginwrapper-0.9.91.4
```

Configure, make and install:

```

./configure
make
sudo make install
```

That will install nspluginwrapper properly.

---

### Post by kcirtap on 2007-07-07
Thank you for your help, one last thing though. When I try the line ./configure it says GLIB 2.0 environment not found. Which is the correct package to install?

---

### Post by Malibu Illusion on 2007-07-07
```
sudo aptitude install libglib2.0-dev
```

---

### Post by kcirtap on 2007-07-08
> **Malibu Illusion said:**
> ```
sudo aptitude install libglib2.0-dev
```

There seems to be a lot of packages I need, because after I installed the glib
, it complained about GTK+ 2.0. I managed to find out which package I needed for GTK+ though, but now it complains once again about: **X11 environment not found**. This time I don't know what to do.

---

### Post by Just_Bri_Thanks on 2007-07-08
I am having the same problems myself.  Still working on the gtk error.

---

### Post by Malibu Illusion on 2007-07-08
kcirtap,

Try using this as the configure line:

```
./configure --with-lib32=lib32
```

Also make sure these are installed:

```
sudo aptitude install libx11-dev libxt-dev x11proto-core-dev x11proto-xext-dev
```

then 

```
make
sudo make install
```

Just_Bri_Thanks,

```
sudo aptitude install libgtk2.0-dev
```

---

### Post by Just_Bri_Thanks on 2007-07-09
I'll try that when I get home today, thank you.

---

### Post by kcirtap on 2007-07-11
> **Malibu Illusion said:**
> kcirtap,

Try using this as the configure line:

```
./configure --with-lib32=lib32
```

Also make sure these are installed:

```
sudo aptitude install libx11-dev libxt-dev x11proto-core-dev x11proto-xext-dev
```

then 

```
make
sudo make install
```

Just_Bri_Thanks,

```
sudo aptitude install libgtk2.0-dev
```

Thanks, but it worked when I installed the dev package. nspluginwrapper certainly works now. Hopefully this is the last problem, when I type: nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so it says: **nspluginwrapper: ~/.mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin**

---

### Post by Just_Bri_Thanks on 2007-07-19
This has me so frustrated I am grinding my teeth.

---

### Post by jenniferwillow on 2007-07-19
I'm having the same problems that **kcirtap** is having.  I do small business gold tech support for Dell (no, I'm not a linux expert nor do I do linux tech support, but trying to learn the os, hence why I'm here), and I am certainly begining to understand how some people can feel frustrated when calling us.  I hate to say it, but I'm almost starting to miss that other OS!  All that aside, I'm fairly stubborn, and would like to get this done.  Ok, this is what I've done so far:

I am using an AMD64 system (home build, not OEM), feisty fawn os, fresh install, just completed all the initial updates.  I go to various sites that have video, and get a message that flash is not installed.  tried to install the .tar.gz file following the adobe instructions, and received an error stating "ERROR: Your architecture, \'x86_64\', is not supported by the
Adobe Flash Player installer"  I used that message to find this thread.  I then began to follow instructions in the thread.  I received some errors here and there, all listed in this thread by others.  So far, these are the commands entered (in italics):

(download flash tarball, command below)

[I]wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

tar -zxf install_flash_player_9_linux.tar.gz

cd install_flash_player_9_linux/

mv flashplayer.xpt ~/.mozilla/plugins

mv libflashplayer.so ~/.mozilla/plugins

sudo aptitude install ia32-libs-gtk ia32-libs linux32 lib32asound build-essential

(Download some tarball, command below)

wget [http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.4.tar.bz2](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.4.tar.bz2)

tar -xf nspluginwrapper-0.9.91.4.tar.bz2

cd nspluginwrapper-0.9.91.4

sudo aptitude install libgtk2.0-dev

sudo aptitude install libx11-dev libxt-dev x11proto-core-dev x11proto-xext-dev

./configure --with-lib32=lib32

make

[/I]
At this point, I get a message stating "/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [npviewer-npw-viewer.o] Error 1"

I figured what the heck, try the next command in the list, which appeared to be 
[I]
sudo make install[/I]

At this point, I again get a message stating "/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [npviewer-npw-viewer.o] Error 1"


**[SIZE="3"]So now what?[/SIZE]**

:confused:

---

### Post by pearlie on 2007-07-20
Thanks - this worked great on the 9-year old Thinkpad that I'm resurrecting from the trash.

---

### Post by nicandris on 2007-12-27
check if this library helps for the compilation:  sudo apt-get install libc6-dev-i386

---

### Post by peligro18 on 2008-01-04
i just cant get it right 
sorry

i try to do that but it said acces denied

roberto@roberto-temple:~/install_flash_player_9_linux$ mv *flashplayer* /usr/lib/mozilla/plugins
mv: cannot move `flashplayer-installer' to `/usr/lib/mozilla/plugins/flashplayer-installer': Permission denied
mv: cannot move `libflashplayer.so' to `/usr/lib/mozilla/plugins/libflashplayer.so': Permission denied

HELP!!!

---

### Post by Injoyy on 2008-01-30
peligro, you just need to add "sudo" to the beginning of the command line(in front of mv), it'll then ask you to enter the admin password.  Use the same pass you use to log in to Ubuntu

---


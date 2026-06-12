---
title: "Got myself into a total pickle with Tovid.."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by iamiso on 2007-06-27
Hi there, 

managed to convert and burn one DVD already but I know there is a patch for Tovid with regards the problem it has with moving on from converting to burning. 

I've downloaded the patch for it and I've absolutely no idea how to install. I've tried to follow their directions but each time I do this from the command line it tells me it can't find the folder it's in! 

I utterly appreciate this is SUCH A BEGINNER question but any advice much appreciated......

---

### Post by aeiah on 2007-06-27
i use tovid but i think ive got an old version, and never had any need to upgrade. could you post the instructions that came with the patch?

---

### Post by iamiso on 2007-06-27
Hi aeiah 

here are the instructions 

APPLICATION:

Since this patch is applied to five files simultaneously, you must apply it to the source and then re-install tovid. If you no longer have your source tarball or directory, grab one from SourceForge. Once you have the tovid-0.30 source directory (the installation instructions describe unzipping and untarring the tarball), apply the patch, and then re-install tovid.

Download the patch to your home directory (/home/$YOU) by right-clicking and saving as "tovid-0.30.2.patch.gz".

In a terminal, change directories into the top-level of the tovid source directory:
Code:
$ cd /path/to/tovid-0.30

To be sure that you're in the correct directory, an ls command should display:
Code:
$ ls
aclocal.m4  configure.ac  INSTALL      Makefile.in  README
AUTHORS     COPYING       install-sh   missing      src
ChangeLog   docs          libtovid     NEWS         todiscgui.desktop
configure   icons         Makefile.am  py-compile   tovidgui.desktop

Apply the patch:
Code:
$ zcat /home/$YOU/tovid-0.30.2.patch.gz | patch -Np1
patching file libtovid/gui/options.py
patching file src/makemenu
patching file src/postproc
patching file src/todisc
patching file src/tovid

With the patch applied, re-install tovid:
Code:
$ ./configure
$ su -c 'make install'

---

### Post by iamiso on 2007-06-27
having just read them again, how do I know I'm in the correct directory? The Tar ball for Tovid is currently in my "downloads" Folder which is contained in my stuff folder. Do I need to just be in the relevant folder when I open up the command line? 

if there was a foolish icon I'd be using it now   :D

---

### Post by aeiah on 2007-06-27
i always find this kinda thing is easier with everything on the desktop. so this is what id do:

-download the patch and drag it to the desktop

-download the tovid source and extract it to a folder on the desktop (it should extract to a folder named tovid-0.30 i guess)

-open a terminal and do ```
cd Desktop/tovid-0.30
``` to change your location to the tovid folder on your desktop

-apply the patch by typing this into the terminal
```
zcat /home/USERNAME/tovid-0.30.2.patch.gz | patch -Np1
```

being sure to replace USERNAME with your username

and then compile as you did previously or with

```

./configure
su -c 'make install'

```

---

### Post by aeiah on 2007-06-27
so yea i typed all that before reading your last post. when you open a terminal, it always opens in your home directory by default, and from there you have to navigate to whatever directory your file is in. i always put things on the desktop but if you have a folder called 'downloads' in your home folder then you can change to that directory by typing 

```
cd downloads
```

and if you type 'ls' (that's a lowercase L) it will list what is in that directory, so you can confirm its the right place

---

### Post by iamiso on 2007-06-27
Brilliant! I'll try that this evening.... 

Thanks for the help - much appreciated. From here on in everything gets downloaded to the desktop!

---

### Post by iamiso on 2007-06-30
hallelujah! With a combination of aeiahs advice and another thread somewhere in google land I finally managed to uninstall tovid, reinstall and patch and it now works like a dream! I feel like the dunce who just came good...... :-\":-\":-\":-\"

---


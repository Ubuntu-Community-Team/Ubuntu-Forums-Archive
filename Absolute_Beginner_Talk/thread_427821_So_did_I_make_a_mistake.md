---
title: "So did I make a mistake??"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-04-29
So last night was my first experience with Ubuntu or any other flavor of Linux for that matter.  The install itself was easier than XP and it detected all of my hardware - color me impressed.  So now here's my issue:  Because my system is an AMD64 system, Installed the AMD64 version of 7.04 - it seemed the logical thing to do.  Now I suspect that this may have been a mistake.

Shockwave and Flash do not appear to work on AMD64.  Quite a few of the websites that I frequent make heavy use of them.

And my biggest problem, :  I can't seem to get any of the virtualization software working under the AMD version.  I tried to install VMware Server following the instructions [here]("https://help.ubuntu.com/community/VMware/Server?highlight=%28vmware%29"), but I must be missing something because it doesn't work.  I really need to have access to a copy of XP for awhile because all our our bills are using MS-Money right now, and until I find something that can import everything, and sync with my banks, I need to continue using it.

So does anyone have any suggestions other than reloading with the i386 version?  I really don't want to go through the hassle again if there's an easy fix.

Thanks

Dave

---

### Post by octoberdan on 2007-04-29
There are ways of getting those things running, but where this is your first experience with linux, I'd install the 32bit version to ensure that it is a hassle free one. Macromedia (Flash), Sun (Java), and others have been a bit slow in developing working 64bit plugins. The mistake wasn't yours. Enjoy!

---

### Post by supersonicdarky on 2007-04-29
get flash working: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)
virtualization: qemu (sudo apt-get install qemu) - info: [http://en.wikipedia.org/wiki/QEMU](http://en.wikipedia.org/wiki/QEMU)
will run faster when compiled with kqemu

i have feisty amd64 and both work fine

---

### Post by bodam on 2007-04-29
Well, let me ask you, can I install the i386 version over the top of this one and keep my look/feel/settings?  I'm kinda happy with the config I now have other than the technical issues I mentioned.

---

### Post by octoberdan on 2007-04-29
> **bodam said:**
> Well, let me ask you, can I install the i386 version over the top of this one and keep my look/feel/settings?  I'm kinda happy with the config I now have other than the technical issues I mentioned.

There probably is a way to export/import the settings, but nothing simple comes to mind right off the bad. As far as sticking it out with 64bit while waiting for the rest of the industry to get into gear, I'd suggest following this [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435) to get firefox up and running. There's evening a script you can download to your Desktop and run to do everything for you. Kilz, the poster, is awesome.

---

### Post by bodam on 2007-04-29
> **supersonicdarky said:**
> get flash working: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)
virtualization: qemu (sudo apt-get install qemu) - info: [http://en.wikipedia.org/wiki/QEMU](http://en.wikipedia.org/wiki/QEMU)
will run faster when compiled with kqemu

i have feisty amd64 and both work fine

So, I'm following the directions just fine for flash up to this part:

Let’s go into the folder with the downloaded file and untar it
the “install_flash_player_9_linux” folder has been created 
move the 2 files “libflashplayer.so” and “flashplayer.xpt” from that folder into the /usr/lib/mozilla/plugins folder 
at last give the command 
Code:
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
if it is all right, it would have to return to the prompt without no messages


So how do I copy the files to the /usr/lib/mozilla/plugins folder?  The GUI says I don't have rights and I don't know how to do it from the command line.

---

### Post by bobplano on 2007-04-29
```
sudo cp *file* /usr/lib/mozilla/plugins
```
sorry for not reading the whole post but that is how you copy whatever file you want. if that doesn't work though just add a -t like:
```
sudo cp *file* -t /usr/lib/mozilla/plugins
```

---

### Post by bodam on 2007-04-30
> **bobplano said:**
> ```
sudo cp *file* /usr/lib/mozilla/plugins
```
sorry for not reading the whole post but that is how you copy whatever file you want. if that doesn't work though just add a -t like:
```
sudo cp *file* -t /usr/lib/mozilla/plugins
```

Thanks for your help.  I do have a weird problem though, after running through the process, Flash only works the first time i run Firefox.  If I completely exit it, Flash does not work when I restart the browser.  If I then run through the process, it works, for the first time again.   Any ideas?

Thanks

Dave

---


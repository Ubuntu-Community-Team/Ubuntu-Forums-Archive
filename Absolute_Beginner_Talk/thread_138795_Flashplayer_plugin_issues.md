---
title: "Flashplayer plugin issues"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-02
I just loaded up ubuntu 5.10 an I really think I love it, but I am having a nightmare of a time with installing the flashplayer plugin.  I am copying the entire terminal session below.
I get the same error everytime I try to install no matter what I try.  Can anyone look this over and tell me what I am doing wrong?  

Thanks


woody@ubuntu:~$ sudo sh flashplayer-installer

Copyright(C) 2002-2003 Macromedia, Inc.  All rights reserved.

Macromedia Flash Player 7 for Linux

Macromedia Flash Player 7 will be installed on this machine.

You are running the Macromedia Flash Player installer as the "root" user.
Macromedia Flash Player 7 will be installed system-wide.

Support is available at [http://www.macromedia.com/support/flashplayer/](http://www.macromedia.com/support/flashplayer/)

To install Macromedia Flash Player 7 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Macromedia Flash Player requires two font packages
      to be installed, gsfonts and gsfonts-x11.

Press ENTER to continue...



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla-firefox


----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Browser installation directory = /usr/lib/mozilla-firefox

Proceed with the installation? (y/n/q): y
cp: cannot stat `./libflashplayer.so': No such file or directory
cp: cannot stat `./flashplayer.xpt': No such file or directory
chmod: cannot access `/usr/lib/mozilla-firefox/plugins/libflashplayer.so': No such file or directory
chmod: cannot access `/usr/lib/mozilla-firefox/plugins/flashplayer.xpt': No such file or directory

Installation complete.

---

### Post by jrib on 2006-03-02
Instead of using that install, you can install flashplugin-nonfree from [multiverse]("http://wiki.ubuntu.com/AddingRepositoriesHowto") using system > administration > synaptic

---

### Post by WoodyMahan on 2006-03-03
Excellent.  Thanks for the assistance.  That worked perfectly.

---

### Post by Simian on 2006-03-03
I don't understand. I've done this downlowd a few times before but now it's not working.

This is what happens:

ben@sunshine:~$   sudo apt-get install flashplayer-mozilla
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
ben@sunshine:~$

I have the multivers repos enabled

---

### Post by Perfect Storm on 2006-03-03
Try update your list

```
sudo apt-get update
```

---

### Post by takayuki on 2006-03-03
hi all,

i just got ubuntu going.  whoooo hoooo!

but i can't find "flashplugin-nonfree" in synaptic.  I've reloaded the package information, and searched for "flash" and "plugin," but can't find it.  any help greatly appreciated.

thanks,

takayuki

---

### Post by takayuki on 2006-03-03
oops.  the answer was in Jason's post above.  go here [URL="https://wiki.ubuntu.com/AddingRepositoriesHowto"]
https://wiki.ubuntu.com/AddingRepositoriesHowto[/URL]

for an excellent howto on showing "disabled software sources", great after you've installed ubuntu and can't find that little package you need.

thanks!

takayuki

---


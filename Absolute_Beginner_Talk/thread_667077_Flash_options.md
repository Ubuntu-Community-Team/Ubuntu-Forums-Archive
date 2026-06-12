---
title: "Flash options"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-01-14
hi all

Using an Acer Travelmate 2420 notebook, with a gig of RAM, running 7.10 and Firefox, and having a lot of swf issues.

For some reason the Adobe Flash player is just a no-go for me.  I have already installed the restricted packages thing, so that isnt the issue, but with Adobe Flash, the site just comes up 'needs to install plugin' - if I install from there, it fails.

If I look in Synaptic - it lists it as installed. 

From Synaptic, I have tried uninstalling/reinstalling/complete removal, etc.  Still nothing.

Switched and installed Gnash.  This works on small basic flash, like splash screns with scrolling text or similar, but slows the system down incredibly, and doesnt seem to be able to handle Youtube at all - just crashes Firefox.

Are there any other options I should test out?

Thanks

Matt

---

### Post by RomeReactor on 2008-01-14
Hi. The flashplugin-nonfree package is broken at the moment; close Firefox, open a terminal and run:
```
sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash
```
Then take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=636397") to see what the problem with the Flash package is. In short, download [this fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), double-click on it to install it, then start Firefox again.

---

### Post by -grubby on 2008-01-14
Yah currently the Flash packages are broken. Use [this]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") package (if you have a 32-bit CPU)

---

### Post by nikoPSK on 2008-01-14
> **RomeReactor said:**
> Hi. The flashplugin-nonfree package is broken at the moment; close Firefox, open a terminal and run:
```
sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash
```Then take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=636397") to see what the problem with the Flash package is. In short, download [this fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), double-click on it to install it, then start Firefox again.

Your assistance is always appreciated.

---

### Post by System6 on 2008-01-14
I am running the 64bit version and of course get the "wrong architecture" message. (Man, I butchered that!)


Is there another package or flash plug in that will work?

---

### Post by tqprvn on 2008-01-14
well this just got a whole lot more interesting.

I saw downthread slightly another similar post (sorry!) and tried to install the package as suggested there.

Midway through that, Firefox went crazy on the confirmation screen of a flight booking.  Went ballistic.  Restarting the machine was the only way out of that one....but the install wasnt finished.

Opened Firefox (hoping for the best really) and went to a page with a splash screen.  Flash not installed.

Went to Synaptic to see if I could see anything there, and it wont start..telling me that:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So went to Terminal, pasted in the dpgk part - superuser priveleges required.

This is my eighth day on Linux, so now we are well into territory above my head....any advice greatly appreciated!

---

### Post by Semong on 2008-01-14
> **nathangrubb said:**
> Yah currently the Flash packages are broken. Use [this]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") package (if you have a 32-bit CPU)

Hello. This guys suggestion should work for you. I did this very same thing with good results. G-debi will do all the work for you and then simply restart firefox, If that doesn't work for you though, try going to this thread and follow instructions: [Absolute Beginner Guide: Install Flash in Firefox Ubuntu 64 (Firefox32)]("http://ubuntuforums.org/showthread.php?t=663871&highlight=flash")

By the way you should consider putting your distros system monitor in your panels (its like the task manager for windows). Anytime a program stops responding or goes haywire, find it in the processes and destroy it.

---

### Post by tqprvn on 2008-01-14
hi there

At the moment I cant install anything, as it keeps telling me that I have another installer open (I dont) from the earlier crash.

See my last post for the error I get in Synaptic.  The default deb installer wont start, telling me to close any other installations I have running.

I have restarted twice to try to kill it, but seems that something is stuck in the pipes somewhere.

M

---

### Post by RomeReactor on 2008-01-14
> **System6 said:**
> I am running the 64bit version and of course get the "wrong architecture" message. (Man, I butchered that!)


Is there another package or flash plug in that will work?

Hi. Yes, get the [64-bit package here]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466").

> **tqprvn said:**
> Went to Synaptic to see if I could see anything there, and it wont start..telling me that:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So went to Terminal, pasted in the dpgk part - superuser priveleges required.

This is my eighth day on Linux, so now we are well into territory above my head....any advice greatly appreciated!

Run the command by prefacing it with **sudo**:
```
sudo dpkg --configure -a
```
If you get an error message saying that you have another package manager open and you don't, that's probably Update Manager working in the background fetching updates for your system; just wait a couple of minutes and then try again.

---

### Post by tqprvn on 2008-01-14
that got it - tks!

---

### Post by vitalstatistix on 2008-01-14
From what I understand you just need the flash plugin for your browser. Goto [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
and download the tarball. Double clicking should open the tarball in fileroller and choose to extract it. Next
n terminal, navigate to this directory and type 
```
 sudo ./flashplayer-installer 
``` and enter ur password                   to run the installer. Click Enter. The installer will instruct                   you to shut down your browser(s). Next provide the path of ur browser usually ```
 /usr/lib/mozilla-firefox
``` and choose to install. You should be done!

---

### Post by n_murthy on 2008-01-14
I downloaded and extracted the flash plug-in, ran the installer program after navigating to the directory containing the program. After being prompted to enter the location of my firefox folder, I got the following response:

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

As you can see below I entered the proper path:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=56496&d=1200362157[/IMG]

How can I get around this problem??

---

### Post by RomeReactor on 2008-01-14
Hi. Did you run the installer with administrator privileges by using **sudo**?
```
sudo ./flashplayer-installer
```
Or try using **/usr/lib/firefox**.

Otherwise it won't let you install to that directory. For an easier way to install Flash, download [this .deb package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466") and double click on it to install.

---

### Post by n_murthy on 2008-01-14
**/usr/lib/firefox** was the appropriate directory. thanks

---

### Post by nikoPSK on 2008-01-14
> **n_murthy said:**
> **/usr/lib/firefox** was the appropriate directory. thanks

Please mark this thread as "SOLVED" :)

Best,
nikoPSK

---

### Post by bosstweed on 2008-01-15
Just wanted to thank you all for a great thread. This worked perfect for me.

---

### Post by nikoPSK on 2008-01-15
> **bosstweed said:**
> Just wanted to thank you all for a great thread. This worked perfect for me.
 
No problem. :)

---


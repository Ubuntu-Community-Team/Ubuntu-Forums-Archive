---
title: "[SOLVED] Package installs &amp;quot;failing&amp;quot;"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Michael Young on 2007-08-21
I just installed Ubuntu 7,04 desktop on my PC this past weekend.  While doing that, I had a little trouble getting my Motorola WN825G Wireless PCMCIA card working - but, after a little sleuthing, I got it working.  In this process, I had executed "sudo apt-get install bcm43xx-fwcutter" - it installed some items, but it failed when attempting to retrieve / install other parts (the actual firmware, I think).  I found other apt commands to get the firmware and proceeded to install the necessary files to get the card to work.  

However, I now get the following error anytime I run apt-get or synaptic for any new package :

E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1

The details indicate that a "404 Not Found" error is being encountered.

Apparently, the package manager is keeping track of the fact that I had a failed download/install of the bcm43xx-fwcutter, and reattempts this install every time I install any package (as if the bcm43xx-fwcutter is in some sort of "pending" install state).  I don't want to uninstall the entire package, since I may be using pieces of it, but I would like to get rid of the spurious error messages.  BTW - I don't want to simply use a "backup" of an old version of the package database, either, because I've successfully installed several other packages since the original errored installation attempt (simply ignoring the error each time), so "rolling back" the database file is really not viable.

How can I "clear" this error?

Many thanks,
   Michael

Update - this problem is now preventing me from installing some packages (g++, in particular), as they error out on the subprocess for bcm43xx.

---

### Post by FakeOutdoorsman on 2007-08-22
Did you try the following?
```

sudo dpkg --configure -a

```

You may have to remove bcm43xx-fwcutter:
```

sudo apt-get remove bcm43xx-fwcutter

```

Then install it:
```

sudo aptitude update
sudo aptitude install bcm43xx-fwcutter

```

I used aptitude in that example because it may do a better job than apt-get of finding any dependencies for that package.

---

### Post by Michael Young on 2007-08-22
Thanks for the reply.

I tried the "dpkg --configure -a" and got the same errors I have been getting...
****
sudo dpkg --configure -a
Password:
Setting up bcm43xx-fwcutter (006-1) ...
--02:02:12--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
02:02:12 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
****

So I proceeded with an attempt to remove the offending package, using your code, but I get an error, as shown below :

sudo apt-get purge bcm43xx-fwcutter

E: Invalid operation purge

So, unfortunately, I'm still stuck....

---

### Post by FakeOutdoorsman on 2007-08-22
Curses!  I'm up too late and mixed apt-get with aptitude. Try:

sudo apt-get remove bcm43xx-fwcutter

Then try installing using the code from above.

---

### Post by FakeOutdoorsman on 2007-08-22
Ok, now I doubt my above recommendations will work too because there is a problem with the package you are installing:

[Bug #124304 in restricted-manager (Ubuntu): bcm43xx-fwcutter required by restricted-manager, but isn't included]("https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/124304")

and
[URL="http://ubuntuforums.org/showthread.php?p=3214872"]
Wireless using bcm43xx-fwcutter for Acer Aspire 5100[/URL]

---

### Post by Michael Young on 2007-08-22
It seems to have worked!
All I did was the "sudo apt-get remove ..." and reboot (I know, I know, probably not necessary, but I wanted to make certain nothing was cached.)
I didn't have to reinstall anything, my wireless card is still working, and subsequent installs do not give me the error - wonderful!
Thank you for your help!

---


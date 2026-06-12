---
title: "Lucid Macbook No Internet, wired or wireless"
date: 2010-05-25
forum: Apple Hardware Users
---

### Post by rat6fink on 2010-05-25
Hey All,
I'm a certified Ubuntu noob, and I'm at a spot that has me thoroughly aggravated.  I can't get a wireless connection at all.  This wouldn't be a problem, except that I can't get a wired connection using ethernet either.  And when I switch over to OS X, everything is fine.  Wireless is ok, and ethernet is ok.   I've searched and searched and haven't found an answer.  Please help!!!!!!

I'm running a Macbook 3,1, running Lucid 10.04, as a dual-boot with OS X Leopard. I checked, and it looks as if I have a Broadcom airport card.  Also, if it helps, my internet is thru AT&T, using a 2wire broadband modem/router combo.  If ya need more info, I'll be happy to provide it.  Again, please help if possible, and thank you all in advance!

---

### Post by sha.goyjo on 2010-05-25
Weird. Did your ethernet work when you booted the livecd? 

My advice would normally be to try and install ifplugd, but you don't have internet access, so that would be diffult. The only way to do it without access to the internet ubuntu-side is to download it onto a flash drive in OSX, then use
```

sudo dpkg -i <path to the file>

```
in order to install from the file on your flash drive.

you can get the file here
[http://packages.ubuntu.com/lucid/ifplugd]("http://packages.ubuntu.com/lucid/ifplugd")

Maybe that will help with your wired connection. Then again, maybe it won't. I hope you get some other, more certain suggestions. It definitely wont' make anything worse. :)

---

### Post by rat6fink on 2010-05-25
I just tried booting from the CD, and I could get everything up.  Wired network came up with no problem, downloaded the hardware drivers ok, found my wireless network.  Now when I shut down, and start the comp again, it's back to square one.

Now I have nothing, just as before.

---

### Post by rat6fink on 2010-05-25
Alright.  It's been 4 hours trying to figure this one out.  LOL.  I'll return tomorrow for another installment.  Probably just delete Ubuntu, and start from the beginning.  If anyone has anymore advice or help, I will return tomorrow.  Thanks for the help so far.

---

### Post by sha.goyjo on 2010-05-26
That's just damn weird. Either some installer script didn't go off, or there is something not in a script that should be. Or, god forbid, there is an actual bug, but you think we would have heard more of it.

---

### Post by rat6fink on 2010-05-26
I know.  I'm stuck at work now, but when I get home, just to make sure, I'm going to wipe the Macbook, reinstall everything, and start over.  I've done it so many times now, that it's not that big of a deal. LOL

---

### Post by rat6fink on 2010-05-26
RAWR!!!   I had to do the re-installation of Mac OS first.  Then, installed Lucid using these instructions from Jamesixgun:


[http://ubuntuforums.org/showthread.php?t=1466252&page=3](http://ubuntuforums.org/showthread.php?t=1466252&page=3)

when finished installing Lucid, had my Macbook hardwired through ethernet.  Went to terminal, typed:

sudo apt-get update
sudo apt-get upgrade

downloaded and installed everything in update manager.

down'ed and installed the device drivers for the Airport card.


VOILA!  success!

Thanks for all your help!!!

---

### Post by sha.goyjo on 2010-05-27
Glad you got that taken care of. That particular slew of broadcom cards is a pain in the butt. I think I've typed
```

sudo apt-get install b43-fwcutter

```
a few more times than I'd like to count.

Best of luck with Ubuntu :)

---


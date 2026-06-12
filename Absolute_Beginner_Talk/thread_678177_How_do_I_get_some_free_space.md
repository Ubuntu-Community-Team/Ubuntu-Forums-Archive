---
title: "How do I get some free space?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Sadbird on 2008-01-25
Hi there, I'm a newbie with Ubuntu, and I am wondering how to clear some files I don't need, or the temporary files or something, because Ubuntu is growing everytime I update, but I'm running out of space, and I don't know what to do.
I was reading stuff and it said to type sudo apt-get clean, but then, it asks for my password, where I type it I can see it but nothing happens, and when I type sudo apt-get autoclean it does something but I only get like 1 MB of free space.
Is this ok?
Sorry, I really am trying to get used to Ubuntu, Im using Gutsy.
Thanx.

---

### Post by wolfen69 on 2008-01-25
try doing sudo apt-get autoremove

other than that, there is not much else you can do, other than manually removing personal files or uninstall apps you dont use.

---

### Post by Hightide on 2008-01-25
Hi what size of a Hard Disk have you got? are you dual boot?

:(

---

### Post by skymera on 2008-01-25
try

Applications -> Accessories -> Disk Usage Analyzer

then that will show what dirs are the biggest, i dont reccomend modifying other than your homw.

have you checked the .wine folder?
usually i forget to get rid of the files i install in there and GB's fill up fast

---

### Post by Sadbird on 2008-01-25
:) Thanks, it freed like 50 MB, but I tried removing some apps and it says I should do it from Synaptic package manager, and there are all sorts of things, all separated. Can I remove something there that can kill my OS??
:confused:
I have dual boot, linux drive is 20 GB, where is the wine folder? (Sorry)
Thanx again.

---

### Post by skymera on 2008-01-25
yes.

certain things will defo break your system.

check them out before you remove them.

---

### Post by ugm6hr on 2008-01-25
apt-get clean should free up space.  Not sure why it doesn't for you (unless it has already been cleaned, and you are still low on space).

To check, post the output from:
```
ls /var/cache/apt/archives
```

---

### Post by Jelmoh on 2008-01-25
Take a look at the applications tab.. Probably there are a lot of programs you don't use!
In games for example.. Or in internet...
Removing these applications via Synaptic is quite safe.. :)
If you're not sure if it's safe to remove an application, come back to the forum and ask! :)
There's always someone willing to help you here! ;)
Good luck!

---

### Post by Sadbird on 2008-01-25
its says lock: partial
nothing more.
I will check on synaptic and ask :)
Thank u

---

### Post by mandrill on 2008-01-25
Three things you can do - first go to Synaptic, at the bottom left choose the bar that says "Status", choose that - you will see four sections under "All" (installed, installled/local or obsolete. not installed and the fourth one ( whose exact wording I can't remember right now - something like "installed not used" - anyway, its the bottom one. Choose that and all the packages that are not doing anything will appear in the main window. Mark all of them for uninstallation, then uninstall them.

Then, while still in synaptic install deborphan, or the one right below it called gtkorphan, which has a gui....once installed, you may safely delete orphaned deb packages.

Finally, instead of just deleting files through the trash, you can shred them or wipe them  . I don't know if this really makes a difference, but it makes *me* feel better. Install shred and/or wipe, and you can run them on individual files from either the terminal, or configure them into your Nautilus context menu, so you can just do it with a click. There is a tutorial  here : [http://library-cafe.com/article/securely-wipeerase-files-in-ubuntu-gutsy-via-right-click-menu-in-nautilus-1390-1.html](http://library-cafe.com/article/securely-wipeerase-files-in-ubuntu-gutsy-via-right-click-menu-in-nautilus-1390-1.html)  

Anyway, Good Luck!

---

### Post by ugm6hr on 2008-01-25
> **Sadbird said:**
> its says lock: partial
nothing more.


Which means you have removed all the archives.

If you've filled 20GB, you must have a lot of personal files or apps installed.  There should not be any "unnecessary" Ubuntu system files elsewhere.

---

### Post by rosegarden78 on 2008-01-25
> **Sadbird said:**
> Hi there, I'm a newbie with Ubuntu, and I am wondering how to clear some files I don't need, or the temporary files or something, because Ubuntu is growing everytime I update, but I'm running out of space, and I don't know what to do ... 

A fresh install of Ubuntu GG as described [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981") does the trick for me.  But I suggest you consider using your internal hard disk mostly for programs and system files?  If you have at least 5GB you can burn a dvd and free that space.  If you only have 700 MB free you can burn one CD-ROM at a time.

Other than that consider investing in external hard drive / USB storage for data storage or use the CD/DVD discs.  The computer needs the hard drive for all that system file stuff.  I think my Ubuntu with programs uses 2-4GB of space on a 30GB partition but your results may vary.  EDIT:  It looks like a fresh install as above without extra programs is 6.2 GB but that includes home folder, Opera 9.5 beta, swap file, temp folders and trash can. (both I haven't checked lately)

---

### Post by Sadbird on 2008-01-25
Thank you for all the help you've given me.
I did not have personal stuff on the linux partition, it was just a bunch of programs I never used, now I have 11.5 GB free.
:)
Problem solved.

---


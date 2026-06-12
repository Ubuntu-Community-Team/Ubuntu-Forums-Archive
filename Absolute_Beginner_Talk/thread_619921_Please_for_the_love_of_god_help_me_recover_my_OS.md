---
title: "Please for the love of god help me recover my OS"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-11-22
Hey ive ran into a BIG problem trying to install a bloody usb wireless adapter the post is here:

[http://ubuntuforums.org/showthread.php?t=619887](http://ubuntuforums.org/showthread.php?t=619887)


now everytime i try boot it says "kernel pannick" even in recovery mode

is there anyway at all possible that i can get back my settings from my drive?

the conky, the themes the godam everything

EVERYTHING

i really dont want to reinstall everything, i have no CD/DVD burner, no Flash drive, no nothing to back up anything on to, i cant believe this, i just tried install a godam usb wireless adapter and i kill the whole bloody OS...

---

### Post by MegaJim on 2007-11-22
When you boot up, tap the "i" key to trigger interactive mode, when it gets to ndiswrapper module, deny it permission to load.

edit: nvm, it appears ubuntu doesn't have an interactive start script :(

---

### Post by elctb on 2007-11-22
Yes, it should be possible to recover everything. However, to be able to help better we need to know the reason for the kernel panic. Could you post the last several lines leading to the panic ? You might need to click on "view details" or something like that as the computer boots up.

---

### Post by dynamethod on 2007-11-22
Well, at the part where it says "kernel panick" it says its because "cant sync kernel" and a whole load of hex before that, i dont have time to muck around unfortunatly ive gone ahead and formated the drive and reinstalled, i need to study, i need to study hard, and i need to do it now, but i mean, this is crazy, all i was trying to do in the first place is get my wireless usb adapter to work and its cost me my study material and everything, not a good experience at all

---

### Post by Bartender on 2007-12-10
dynamethod -
You have got to build yourself a separate "/home" partition.  aysiu's website has a guide for building a /home partition after you've already installed Ubuntu in case you didn't do it when installing.

A separate /home is the only way to fly.  I recently screwed things up and got a Kernel Panic Error.  Had no idea what to do so just re-installed Ubuntu 7.10 to the "/" partition.  When finished, everything was there like before; the desktop wallpaper, all documents, music files, etc.  Even the upper panel with quick-start icons re-appeared as before. 

I found just one thing that was out of whack - the GnomePPP applet in the upper panel had changed to a generic icon, but it was simple to set the dialer up again.

---

### Post by AlanRogers on 2007-12-10
Separate /home +1 but it's not fixing the OP's problem. Sorry for the hijack but hopefully following this advice will mean that you never have the same problem again. Having learned the hard way myself, I now always create a separate /home, advise converts to do the same and never will do different.
 
FWIW, the standard Debian installation does just this and I'm not really sure why Ubuntu has chosen to do it differently, unless it's a recent change in Debian that hasn't been caught up yet; I've only ever installed 4.0 Etch.

---

### Post by rockinlinux on 2007-12-10
> A separate /home is the only way to fly

+1

---

### Post by viking777 on 2007-12-10
> **rockinlinux said:**
> +1

Seperate /home BS!. Had one, got rid of it, much better off for it.

---

### Post by AlanRogers on 2007-12-10
> **viking777 said:**
> Seperate /home BS!. Had one, got rid of it, much better off for it.Please qualify; I've explained why a separate /home is benefical and you disagree, which is your right. It doesn't help the OP one jot though if you don't explain why. Keep them informed, let them make their own decisions.

---

### Post by candtalan on 2007-12-10
My sympathies for the loss of data in a difficult real life situation - however - it seems to be a good time, if there ever is a good time after the event, to remind all new users of computers that a backup of data is a *really good* idea. 

Even without problems after using the powerful sudo command, all sorts of hardware failures can hose data, or make life very inconvenient when - say - study deadlines loom.

Backups with usb sticks are very easy with ubuntu.

---

### Post by viking777 on 2007-12-10
> **AlanRogers said:**
> Please qualify; I've explained why a separate /home is benefical and you disagree, which is your right. It doesn't help the OP one jot though if you don't explain why. Keep them informed, let them make their own decisions.

S'easy. A seperate /home partition has two effects.

1) It takes up extra space on your hard drive. I have 10 partitions on a 100Gb hard drive - I cant afford the space.

2) It makes reinstalling or upgrading *twice* as difficult as just copying your data and reconfiguring your OS because hardly any of the settings on the separate drive ever work again and sorting out those that dont from those that do is vastly more difficult than reconfiguring from scratch. I have proved this to myself over and over again whilst I had a seperate /home partition.

---

### Post by Myglaren on 2007-12-10
> **viking777 said:**
> S'easy. A seperate /home partition has two effects.

1) It takes up extra space on your hard drive. I have 10 partitions on a 100Gb hard drive - I cant afford the space.

2) It makes reinstalling or upgrading *twice* as difficult as just copying your data and reconfiguring your OS because hardly any of the settings on the separate drive ever work again and sorting out those that dont from those that do is vastly more difficult than reconfiguring from scratch. I have proved this to myself over and over again whilst I had a seperate /home partition.


I have to disagree with you here.

I took the advice of creating a seperate /home partition and have nothing but positive experiences.  Saved hours of tweaking to get everything back the way I wanted it after a new install/upgrade.  This machine has never been better.

As for taking up more space - you are still limited to the total space on your hard drive with or without  a home partition.  Having the data in a home folder just means having to back it all up then reinstate it after a new install. - or not, of course, in the event it didn't get backed up.

---

### Post by maybeway36 on 2007-12-10
I have a /home on my main machine with all my files, but on fooling around machines I don't. It's really depending on the situation for me.

---

### Post by viking777 on 2007-12-10
> **Myglaren said:**
> I have to disagree with you here.

I took the advice of creating a seperate /home partition and have nothing but positive experiences.  Saved hours of tweaking to get everything back the way I wanted it after a new install/upgrade.  This machine has never been better.

As for taking up more space - you are still limited to the total space on your hard drive with or without  a home partition.  Having the data in a home folder just means having to back it all up then reinstate it after a new install. - or not, of course, in the event it didn't get backed up.

In answer to your first point I can only say you have been exceptionally lucky - I haven't.

In answer to your second point you are simply wrong. Unless that is you have some kind of divine knowledge of how your partitions are going to grow over time. If you have a separate /home and / partition you have to have space on each of them to allow for them to grow over time. This always takes up more space overall.

Anyway none of this is really relevant to our friend who started the thread is it.

---

### Post by Teknyk on 2007-12-10
I think that is where the difference lies. Viking777 I notice is using Hardy already and states he has 10 partitions. Based on that one would assume that he is not dependent on that OS for his day to day work and could feasibly move "must have" files to another partition if needed. As the OP states, he IS dependent on his OS and has no way to back up any of his important files although a cheap USB mem stick would be a great investment if he can swing it.

In the OP's case I would have to agree, a dedicated /home partition is the only way to go.
I just moved mine to its own partition even though I do have a way to back up my important stuff.

Anyways since the OP has already done a nuke and pave it pretty much makes it a moot point. Hopefully though he has created a separate /home this time or picked up a USB stick so he doesn't find himself in this position again.

Just my .02

---

### Post by az on 2007-12-10
> **AlanRogers said:**
> I'm not really sure why Ubuntu has chosen to do it differently

Ubuntu has a streamlined installation.  The fewest steps is best.

A separate home is mostly a false sense of security at best.  It also unnecessarily complicates the installation process.  You limit your use of free space by creating partitions.  By putting everything on one partition, you don't run the risk of running out of space on one of your partitions and bringing your whole system down - one partition for everything shares all your available space at all times.

It is far less complicated to perform a conventional backup than to create a separate partition.  This case in point, the data was still there, the problem was either a kernel misconfiguration (I'm not clear as to whether the OP swapped out his/her kernel or not) or a kernel module misconfiguration (ndiswrapper tends to make a system unstable) 

The OP should not have had to wipe the entire drive to reinstall.  Simply shrinking the existing Ubuntu partition and installing again besides it would have worked just fine, preserving the data.  If the OP did not have sufficient disk space to do that, I would think further limiting disk space by creating another partition for home would make matters worse.

A separate home partition was a nice idea years ago, when Linux was just for geeks.  Disks are cheaper and less reliable these days.

Not to mention that a desktop configuration problem can bring down your desktop.  The solution for which is to create another user and log in.  If you were to copy your home partition, you would reinstall with the same issues on your fresh-install.

---

### Post by v.alari on 2007-12-10
I have a sticky space bar so please excuse Errors. I have a 160GB HDD with a 40GB secondary. The 40 is all one partition but one my primary I have a 25GB partition for windows in case I Need it, a 6GB linux windows installation partition to go with that, a 4GB swap partition and the rest for ubuntu. How can I shrink the Ubuntu partition without damaging the data and create a data partition in the free space?

---

### Post by viking777 on 2007-12-11
Just use Gparted, if you haven't got it already it is in the repositories, and is very easy to use with a proper gui!!  Just remember that in order to do anything on a partition it must be unmounted so in your case you would have to use a live cd like this:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

or a small distro that contians it like this:

[http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)

---


---
title: "is there a deep freeze-like software for ubuntu?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-01-26
In Windows xp, I use deep freeze, a very useful software, and I wonder if there is any equivelant tool for ubuntu available, that does the same?

Deep freeze restores the computer, back to how it was, everytime you reboot. This means that any virus, trojan and stuff cannot do anything, I even don't need to use any antivirus. When I want to install a new sotware, I first install it with deep freeze on, try the software, and if satisfied and decided to perminantly install it, I ask deep freeze to be disabled in the next reboot, to install the new software perminantly. I can also setup one or more partitions that is perminantly open (not locked by deep freeze) to save my downloads and other files that needs to be saved regularly.

---

### Post by steve.horsley on 2006-01-26
Ah. I just saw a post from you complining that you don't automatically have access rights to your whole filesystem. Put the two together. I haven't heard of anything like deepfreeze, but it's probably not so badly needed on *nix. You don't get viruses so many times a day, partly because it's not so easy for them to gain enough rights to corrupt the system files.

You may be able to do something with rsync in a startup script.

---

### Post by bulldogzerofive on 2006-01-26
For a variety of reasons, viruses and trojans are not currently a concern for linux in general and ubuntu in particular.  As such, programs like that do not tend to exist for linux (although there might be one I don't know).  I really do not think you need to worry about this.

However, there are a couple ways to get what you want:

**1.  LiveCD**  A liveCD is a complete operating system that runs entirely from your CDROM.  You will never ever catch a virus with a liveCD because the operating system is on a non-writable media.  The disadvantage of this is that it runs slow and you cannot install anything.

**2.  Custom LiveCD**  You can create a custom liveCD with all the software you desire on it and burn it to CD.  This will still run slow and it requires a certain level of research (certainly more than I can help you with).

**3.  Partimage and tripwire.**

All the executable files on your Ubuntu box (installed, not LiveCD) are kept in the partition called "/".  The other partitions are just for information storage (it is more complicated than that but in a nutshell...).  So, the first thing you do is set up your Ubuntu box the way you like it and make sure you have all the patches and updates installed.  Then, download a live CD (such as knoppix) with partimage on it and use it to make a mirror of "/" and store it somewhere safe (like on a CD-R or two). This will be the backup.  Then, you use tripwire.   Tripwire monitors the size of all the binary executables on "/".  If any of them changes, you have a problem and can simply install "/" again from your backup.  Simply repeat this process each time you install programs or update your box.


**4.  Learn to trust the wonderful and secure world of *nix:**

Seriously, viruses, trojans, and spyware are *not* an issue on Unix-like systems.  Simply follow these security practices and you are safe:
a.  Be aware of what services you are running for the outside world and make sure they are secure.  Learn how to use tool netstat.
b.  Only install software from the ubuntu repositories.  Although Ubuntu only certifies main and security as secure, universe and multiverse are perfectly safe, as are PLF, the Wine repository, and the Open Office repository.  Just don't install software you find floating on the net.
c.  Run as a normal user.  Do not run as the superuser ("root") and only use the first "administrator" account to do administrator things.  When surfing the net or opening questionable media be really, really sure that you are a normal user.

Then you will be safe.

Let us know if you need any more advice!

---

### Post by sallam on 2006-01-26
Thanks so much for your wonderful help. I now understand a lot better.
I've selected to be loggen in automatically at boot, to avoid typing my username/password each time I boot. Does that put my box in risk for viruses or tojans?

---

### Post by Jucato on 2006-01-26
Not really, because no matter who you are at login, as long as you do not login as root, you will still be prompted for root privileges everytime you try to do something that only a root could/should do.

It won't protect your system, however, from other users who might use your PC (relatives, friends) since they will automatically be logged in to your user and your settings.

---


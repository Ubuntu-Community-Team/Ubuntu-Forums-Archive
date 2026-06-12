---
title: "Repairing Ubuntu system files"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Michaelg14 on 2007-05-07
Is it possible to repair an installation of Ubuntu keeping updates but reinstalling the file system?  Doing a re-install from CD requires the ext3 partition to be reformatted losing all my changes and added software.  Obviously, I have trashed the system more that once and had to re-install from scratch, is there an easier way to recover from my mistakes.

---

### Post by Tundro Walker on 2007-05-07
*"Holy f'ed up Ubuntu's, Batman!"*

As far as I know, there isn't a "restore base system" feature on the cd, letting you, you know, restore the base system without touching other things you've set up (like your config files for other applications).

But, if it's simply hosed up but still bootable, you might be able to command-line the apt-get utility, and tell it to reinstall whatever you feel you've pooched up.  

**EG:** let's say I pooch up the "ubuntu-desktop" (like, for instance, I uninstall the meta package so I can uninstall a whole lot more stuff, which I do something to totally hose up the desktop.)  I can just boot in safe-mode to command-line, and "apt-get install ubuntu-desktop", which will reinstall the meta package, which forces reinstallation of all the stuff I may have pulled out and hosed up.

If your system isn't even bootable (EG: you pooched the /boot/grub/menu.lst file...which I've done once...LOL!), you can boot from the Ubuntu LiveCD, mount your hard drive, then dig for the file that's hosed up.  Open it in a text editor as super-user, and you can correct what's hosed up.  Then, presto, just reboot back on your hard-drive.  The liveCD can really get you out of a bind at times by letting you boot from it to correct problems with your Linux (or Windows!) install.

Ok, if worse comes to worse, you may need to totally re-install Ubuntu.  To keep your personal settings, or avoid having to re-download all your porn...uh *cough* mp3's (yeah, mp3's), you can use a LiveCD to boot from, so you can mount your drive and copy all your stuff you want to save onto some kind of removable media (EG: flash stick).

When re-installing, a lot of folks recommend making your /home directory use its own partition.  This has multiple advantages:

1) lets you use that /home directory partition with multiple Linux OS' installed on the same machine (EG: if you had Ubuntu and Xandros on the same machine, they could both use your /home partition for the that, letting you preserve your personal settings between the two).

2) If your OS partition bites the big one, you can just reformat it without losing your /home partition.  When you re-install, you just hook back into your /home partition to use it as your /home directory for the new install.

I personally don't do this (I don't keep much stuff on my computer I don't mind re-installing).  So, I'm not to familiar with how to do this.  I assume it just involves making a partition, tossing a /home directory on it, and using a symbolic link on the OS partition to point it to your /home directory partition.  But, I may be wrong.  You can search for "partition drive" and should hit quite a few posts that recommend how to do this.

The answer I've given is pretty generalized, because your question was pretty general.  If you provide more detail, like what exactly you feel is messed up, or perhaps a snippet from an error log (or if you need help figuring out how to view an error log), I'm sure some folks on here will be able to give better help. I've found that it's pretty hard to hose up Ubuntu in such a way that it can't be fixed, especially if you can still boot from a LiveCD and have the help of a knowledgeable Linux forum member.

---

### Post by Michaelg14 on 2007-05-07
Thank you that was very helpful.  I will save that post if I ever need it, right now everything is cooking along just fine, but I haven't tried to do anything weird lately.  I'm sure it's only a matter of time before I try to do something I shouldn't.  I do have all my por...mp3s, I mean, backed up elsewhere.

---

### Post by ron999 on 2007-07-17
Wow Tundro Walker
You've got me out of a mess.
I had been trying to 'strip down' my Ubuntu installation by removing orphan apps using gtkorphan program.
I must have chucked out too many apps and Ubuntu refused to re-boot.:sad::sad:
So I searched through the threads while booted into another OS and found this one.
The instruction 'apt-get install ubuntu-desktop' did the trick.
It took a long while for it to reinstall everything, but I'm up and running again now.:D:D
That gtkorphan program is dangerous in the hands of an amateur like me.
Thanks very much.
8)

---


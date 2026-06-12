---
title: "Home Folder Problems"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-07-25
I just changed the motherboard on this computer and managed to mess up something with the Ubuntu Feisty install that was on it.  So I tried to reinstall without formatting the /home partition I had set up.

That didn't work, I posted asking for directions, and the solutions I got didn't work either.

All through this I would (seemingly) randomly get error messages when I tried to log in saying that the /home folder for the user account I was trying to access wasn't there and that I could try to log in as root even though that wasn't going to work (and predictably when I hit OK it didn't work).


So I decided I'd had enough of that crap and reinstalled completely from scratch - formatting both the root and the home partitions.  Every time I run the Live CD to install and set the partitions manually I have to delete and recreate them, since if I simply try to assign the existing partitions to root or home they resize them so I end up with a few megabytes of free space.  Annoying.


Anyway, I get it completely reinstalled and I get 100 things that need updated.  I do that and it says it needs a restart.  So I restart only to be greeted with a forced check of the hard drive because it says it hasn't been checked in 465 days or something like that. (which isn't true)  Only this time it doesn't actually do anything, it just sits there looking at me.  I try CTRL-ALT-DEL and it boots up, and then throws the "no home folder" crap at me for every user account.

Full text of the error: "Your home directory is listed as: '/home/chris' but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory?  It is unlikely anything will work unless you use a failsafe session."  Interesting that they'd essentially say "go ahead and hit Yes if you want.  It works the same as hitting No."  Why not simply just say there's an error and you're completely screwed?


I'm now reinstalling AGAIN.  What in the heck is going on with this machine?

Update: I've now reinstalled.  Immediately upon reboot it informed me that the drive hadn't been checked for 460 days and froze up.  I used CTRL-ALT-DEL again and got the same result - the non-existant /home directory error.  Incidentally, the directory does in fact exist if you boot via Live and look in the partition.


I really need some help on this.  It's the wife's computer, she's really ticked off, and I don't know enough about Ubuntu to even guess what to do next.  I searched for similar problems on the forums and 90% of the posts on those topics just look like gobbledeegook to me.  Stuff about fstab and failsafe and whatnot, I have no clue where to begin.

---

### Post by e_james on 2007-07-25
I have installed 7.04 on 3 different computers using the alternate CD. Two of them worked fine, no problems. The third, over several attempts, consistently gets the location of the boot partition wrong. I can get ubuntu to start by editing the grub menu before booting and then editing menu.lst to keep it that way, but if a new kernel is installed I have to do it all again. It seems to me that it is possible that you may have a variation of the same problem. If you can understand it, check that the grub menu refers to the correct locations. This link might help.

[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

---

### Post by Spektyr on 2007-07-25
After unplugging the second hard drive (used just for storage and backups) it has installed and *seems* to be running okay.

Whether it will continue to do so after that drive is reinstalled is unknown...

---

### Post by Spektyr on 2007-07-29
Just a quick update if anyone is interested (you Ubuntu gurus can file this away for future newbie problems).

It seems that the trouble was caused by some of the folders on the second (storage) hard drive being limited to certain users.  When those users weren't present (since you only make one during install) there was some kind of freak-out and things started going haywire.

I appear to have worked around this by disconnecting that drive, installing, setting up the users as before, then hooking it back up.

Everything seems to be working properly now.

---


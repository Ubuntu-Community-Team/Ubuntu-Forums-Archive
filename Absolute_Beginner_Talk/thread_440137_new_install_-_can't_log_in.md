---
title: "new install - can't log in"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by raequin on 2007-05-11
Hi,

I just installed 7.04 using the resize partition option for the windows partition that was previously there (probably inconsequential information, but it was the first time I used software that did that).  I imported a user account from windows.  Upon starting the new install, I can't log in.  I tried both the account name that I gave the windows import, and the name and pwd that ubuntu asked me to create.  Neither is working.

I read this thread: [http://ubuntuforums.org/showthread.php?t=140852](http://ubuntuforums.org/showthread.php?t=140852), but when I press Enter like it says, nothing different happens on startup.

I am excited to use Ubuntu on this computer; I'm really looking forward to it.  Please help me.

---

### Post by Hendrixski on 2007-05-11
hhhmmm, did you perhaps have you caps locks on when you typed the password? or is the username different?

I mean, the username and password are what you set it to when you installed.

If you can't log in to the graphical window, try logging in using safe mode, where there is no graphics.  Then you can try to log in as root and use the same password???

Worse comes to worse, you can just reinstall.

---

### Post by raequin on 2007-05-11
So I can get it to start in safe mode, where I can, apparently, issue commands as root - without ever being prompted for a password (which helps in this situation).  So is there any way that I can see a list of user names and passwords from there?  If not, I guess I will reinstall.  Thanks.

---

### Post by raequin on 2007-05-11
Well, due to the apparent lack of options, I started to reinstall.

I can't get past the partitioning step.

As I mentioned before, I left my old windows install on the hd.  Now I want to use the remaining space for the new install, but it appears that this windows partition is under the root file system (forgive my unknowlegeable use of these terms) so I don't know what to do.  The options provided to me are to a) resize /dev/hda2/ (where the current install of ubuntu is) and use the free space (an option that would lose 1.5 gig to the old install), b) use the entire hd (losing my windows data), c) manual (but I have tried deleting the two partitions made by the old install, hda2 and swap, but I can't procede because installer says I haven't specified a root filesystem).

Help would be appreciated; greatly.

---

### Post by Terl on 2007-05-11
When you installed there was a screen where you were asked to type your full name, then pick a user name and then you had to enter a password two times.  It also asked for the name of the computer.

This is the username and password you need to use.  Did you do this part on the first install?

---

### Post by raequin on 2007-05-11
Yes, I did that part.  Plus, before that, it asked me about importing windows profiles (or accounts?).  So I had to set up a name and password for that account too.  None of the names and passwords have worked (I even checked caps lock).  Thanks.

---


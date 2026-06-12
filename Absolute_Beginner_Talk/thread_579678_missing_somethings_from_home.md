---
title: "missing somethings from home"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-10-18
I just recently installed kubuntu 7.10 and before that I was using linux mint.  I had home on another partition, but I wasn't sure that the files that were there would work with kubuntu, so during installation I deleted all the files that I didn't think I needed to save.  I thought that if kubuntu didn't see certain files in the home directory it would place the files there.

Well .bashrc wasn't there and I'm not sure what else is missing. Anything I can do for the missing files that weren't installed?

---

### Post by introp on 2007-10-18
For .bashrc, that isn't really installed by the OS, but rather copied to your home directory when you make a new user.  I'm guessing that since the home directory was already there, it didn't make a new one and therefore didn't have a reason to copy the skeleton files from "/etc/skel/".  You can look at the files there (such as "/etc/skel/.bashrc") and see if you can copy them to your home directory.  As always, back up any files before replacing them.

Hope this helps.

---

### Post by bone2006 on 2007-10-18
thanks
I see three files
.profile
.bashrc
.bash_logout

None of these files are in my home directory.  Should I copy all three and are there any other files I should be worried about that might be missing?

I basically went through and deleted everything in the directory that was hidden except for .filezilla and .mozilla and I thought I backed up .bashrc, but I can see that I didn't know.

I'm wondering if I'm just better off backing up my files from home onto another spare HD, then reinstalling and reformating everything and copying my important files back over to home?

Now when I open dolphin and close it down I get a warning as well

Error - Dolpin
Unable to save bookmarks
in /home/bone2006/.kde/share/apps/d3lphin/bookmarks.xml.  Reported error was: Permission denied.  This error message will only be shown once.  The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

I get this error each time I navigate anywhere and close it. So I'm thinking maybe it might be better for me to install a fresh copy and just back everything up to another disk and then put it back on?

---

### Post by anjilslaire on 2007-10-21
the bookmarks.xml file has ownership set to root. I ran across this also when I used my old /home directory from Feisty.

Change ownership of all the files in that d3lphin directory to your use/group. That should fix it.

---


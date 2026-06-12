---
title: "More information about Software Updates"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2007-05-12
This weekend there's an update for SNMP.  I don't know what it is or even which app's use it.  
Is there a place where I can go to read about software updates before I download and install them?  
I'd like to know what it is, and how it's being improved.  
Just curious, that's all.

---

### Post by Najand on 2007-05-12
If you click on the "Description of package" in update manager you can get some details about them.

---

### Post by Gyrotwister on 2007-05-12
Yes but I'm interested in more detail about what changes have been made.  Has a vulnerability been patched, a bug fixed, an algorithm streamlined to speed a process up?  

Often I get no information at all when I click the "Changes" tab.

---

### Post by Gyrotwister on 2007-05-12
Bump, does anybody know?

---

### Post by jtraub on 2007-05-12
Other way is to visit software homepage and to read changelogs here.

---

### Post by tgalati4 on 2007-05-13
I think what you really want to know is: "If I update this package, is it going to trash my system?  Again?"

---

### Post by Gyrotwister on 2007-05-13
Well, no.  That's not what I'm talking about.  I'd like to know what the intention is (in simple terms) for each Software Update.  Whether it trashes my system or not is another issue altogether.  

These updates have been created, reviewed and then released to us.  What's being fixed or improved?  

I just assumed this information would be published here somewhere.  
It seems it isn't.  
If it is, I can't find it.

---

### Post by tgalati4 on 2007-05-13
I think you can find the information in the bug tracking system used for each package under development.  Since you need to log into the tracker and search the package and follow the patches that are being applied to  the specific version--it's tedious to find the info.  

Someone would need to go through and summarize all of the patches.  Normally this is done in CHANGELOG.txt or release notes, but you would have to check out the current source code to find that info.

In synaptic, there is a dialog window that shows brief package information, but rarely is there any changelog information.

Perhaps the changelog function needs to be picked up by someone with an interest in developing in this area.  That person could be you.

Personally, I am interested in an update that breaks a production machine running a stable version of Ubuntu (say Dapper).  There's really no way to know ahead of time when an upgrade will cause problems.  

I had a server that ran 165 days straight.  When I brought it down for maintenance (dust cleaning, and UPS battery replacement), I had ~100 Dapper patches to apply.  I did them a few at a time to make sure the system came up after each update.  I didn't have any problems, so this demonstrates that the Ubuntu community is hard at work.  If there were problems with a patch, it would show up quickly in the forums.

I don't know of a master changelog database of Ubuntu packages.  Perhaps someone could write a utility to go through subversion for each upgrade candidate and capture the changelog to put it somewhere useful.

Because of the large package count (21K?) and the simultaneous development taking place, that's a lot of changes to keep track of.  Because of the technical detail of the changes, you might as well be reading the source code.

And maybe that is the answer.  If you really need to know what has changed in a given package, compare the source.  

I realize that this is not helpful.

The bottom line:  all of the upgrades are trying to fix Bug #1.  Maybe that is what should be displayed in the synaptic dialog!

---

### Post by Gyrotwister on 2007-05-13
Thanks for explaining.

---


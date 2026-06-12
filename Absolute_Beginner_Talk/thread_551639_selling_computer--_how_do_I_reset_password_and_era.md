---
title: "selling computer-- how do I reset password and erase info?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by neatokino on 2007-09-15
I am selling an imac G4 which I set up to dual boot Tiger and Feisty.  I want to get rid of all my personal info before selling it, but I don't want to have to completely reload the software.  I know how to clear out my OSX info,  but am not sure what to do with Ubuntu.

Is there a way to change (reset) the password and login name on Feisty and a way to securely erase the small amount of personal information I put in (I really only set up personal info in Thunderbird and on a few Firefox webpages that had login info)?    Is there a way to return Feisty to its original state without reinstalling?

TIA

Michael

---

### Post by styphon on 2007-09-15
You should just be able to create a new user account and then delete your old ones. Any personal information setup just for your account would then be wiped.

---

### Post by Majorix on 2007-09-15
Yeah just delete the home folder of your user.

---

### Post by neatokino on 2007-09-15
So, if I set up a new user account and delete the old one, there isn't a 'root' user account that will have any of that info?  (sorry I'm so lame about this, but I never quite understood if the user account that I created when I first set up the OS is the permanent, 'root' account.

TIA

---

### Post by ryanVickers on 2007-09-15
just wondering, why would you keep the OS's in stalled (specifically ubuntu) if you were selling it?  I mean, unless it's to a friend or something, but...

---

### Post by styphon on 2007-09-15
> **neatokino said:**
> So, if I set up a new user account and delete the old one, there isn't a 'root' user account that will have any of that info?  (sorry I'm so lame about this, but I never quite understood if the user account that I created when I first set up the OS is the permanent, 'root' account.

TIA

The root account would still exist but only contain personal information on you if you have used the root account for such things. You can easily change the root account password to hand over when selling it. Go into System -> Manage Users/Groups and change the root account password in there.

---

### Post by cubeist on 2007-09-15
don't forget the very useful shred command to securely remove any sensitive date.  type "man shred" in the terminal for more info...

---

### Post by Mud.Knee.Havoc on 2007-09-15
Call me paranoid, but I would never just delete personal stuff off a drive and then sell it to somebody else.  If somebody wants to retrieve your info, it's possible to do so.

What I'd do - again, I'm paranoid - is download and burn [DBAN]("http://dban.sourceforge.net/"), which will completely wipe your data.  

Then I'd sell the computer with a clean, wiped drive and whatever OSX/linux discs you want to give the guy.  Let him install the OS.

---

### Post by ryanVickers on 2007-09-15
yes, and in the mac os x install disk, isn't there a feature in the "Disk Utility" to like wipe the disk with zeros 36 times or something?! :)

---

### Post by Tecguy2 on 2007-09-15
the safest way would to reinstall ubuntu what kind of passwords user accounts internet accounts etc

---

### Post by ubuntu27 on 2007-09-15
Well, as for Ubuntu, you can do a reinstall. This time install Ubuntu as OEM. You have the opction to install as OEM with the ALTERNATE CD.

Y you don't want to reinstall. Then just do what other has said:

*Eliminate you Firefox cache and others  [ OPen Firefox, and Ctrl + Shift + Del ]
* Create a new User Account and give sudo provilates [System/Administration/users and Groups]
*Eliminate your User Account

That should be it.

---

### Post by aysiu on 2007-09-15
> **cubeist said:**
> don't forget the very useful shred command to securely remove any sensitive date.  type "man shred" in the terminal for more info...
I'm not too good at understanding *man* pages. Would it go something like this (after creating the new user and deleting the old user)? ```
sudo shred -u -v -z /home/*oldusername*
```

---

### Post by nonewmsgs on 2007-09-15
> **Mud.Knee.Havoc said:**
> Call me paranoid, but I would never just delete personal stuff off a drive and then sell it to somebody else.  If somebody wants to retrieve your info, it's possible to do so.

What I'd do - again, I'm paranoid - is download and burn [DBAN]("http://dban.sourceforge.net/"), which will completely wipe your data.  

Then I'd sell the computer with a clean, wiped drive and whatever OSX/linux discs you want to give the guy.  Let him install the OS.

i would use that program first like mud knee said

---


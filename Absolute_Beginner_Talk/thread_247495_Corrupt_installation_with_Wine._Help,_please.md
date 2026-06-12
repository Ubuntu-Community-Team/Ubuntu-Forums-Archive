---
title: "Corrupt installation with Wine. Help, please?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Catewilliams on 2006-08-30
I've been trying to install Ventrilo for some time, but it hasn't been working. After getting some help on my previous thread, I uninstalled Wine, and tried to reinstall (you can see the thread [here]("http://www.ubuntuforums.org/showthread.php?t=246051")).

Now, when I try to run the ventrilo install exe, it keeps telling me it was a corrupt installation. So I uninstall and re-install, only to have it tell me the same thing. 

Also, when I try to run winecfg, I get this error message:

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

It will open the configuration controls, but when I click on the drivers tab, it comes up with this message:

> 
You don't have a C Drive. Not so great.
Remember to click 'add' in the drivers tab to create one!

After that, if I try to specify where I want my C drive, if I click 'Apply' and 'Ok' and then the window closes, I can open up winecfg again, only the C drive *still* isn't there and the process happens all over again. 

Any help with this? If so, Thanks!

---

### Post by Kilz on 2006-08-30
> **Catewilliams said:**
> I've been trying to install Ventrilo for some time, but it hasn't been working. After getting some help on my previous thread, I uninstalled Wine, and tried to reinstall (you can see the thread [here]("http://www.ubuntuforums.org/showthread.php?t=246051")).

Now, when I try to run the ventrilo install exe, it keeps telling me it was a corrupt installation. So I uninstall and re-install, only to have it tell me the same thing. 

Also, when I try to run winecfg, I get this error message:

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

It will open the configuration controls, but when I click on the drivers tab, it comes up with this message:



After that, if I try to specify where I want my C drive, if I click 'Apply' and 'Ok' and then the window closes, I can open up winecfg again, only the C drive *still* isn't there and the process happens all over again. 

Any help with this? If so, Thanks!
I have had similar problems with wine on the 64bit version of Ubuntu. You arnt running the 64bit version are you?

---

### Post by Catewilliams on 2006-08-30
> I have had similar problems with wine on the 64bit version of Ubuntu. You arnt running the 64bit version are you?



Mmm.. No, I don't think so. :/
But do you know how to fix it for that? And if so, would that work for my problem..? Sorry, slight incompentence. :-#

---

### Post by Kilz on 2006-08-30
> **Catewilliams said:**
> Mmm.. No, I don't think so. :/
But do you know how to fix it for that? And if so, would that work for my problem..? Sorry, slight incompentence. :-#

I used [sidenet]("http://sidenet.ddo.jp/winetips/config.html") to setup wine. It sets up a virtual c drive and all the disks. It should work for the 32bit version.

---

### Post by Catewilliams on 2006-08-30
> **Kilz said:**
> I used [sidenet]("http://sidenet.ddo.jp/winetips/config.html") to setup wine. It sets up a virtual c drive and all the disks. It should work for the 32bit version.



That seemed to work, except I don't see any icons for Ventrilo. How can I run it without a clickable icon? x_x

---

### Post by Kilz on 2006-08-31
> **Catewilliams said:**
> That seemed to work, except I don't see any icons for Ventrilo. How can I run it without a clickable icon? x_x

You probably have to install or have installed the program after you installed sidenet. Sidenet will put a c folder in your home folder. This is a virtual c drive, navigate to the programs folder and click on the exe. You might have to use the open with another application if it dosent open, and click custom command at the bottom of the applications list. Type in wine and click ok.

---

### Post by Catewilliams on 2006-08-31
> **Kilz said:**
> You probably have to install or have installed the program after you installed sidenet. Sidenet will put a c folder in your home folder. This is a virtual c drive, navigate to the programs folder and click on the exe. You might have to use the open with another application if it dosent open, and click custom command at the bottom of the applications list. Type in wine and click ok.



Okay, so I did that, except all that happens is the Ventrilo Setup window flashes and then disappears.  Whats happening there?

Sorry, I'm really new to this. x_x

---

### Post by DougieFresh4U on 2006-08-31
I installed game house games with wine and when I click icon for gamehouse the game screen also flashes and while installing it  I was given message -16 bit sound card is required. I have sound card and all sounds work.

---

### Post by Kilz on 2006-08-31
> **Catewilliams said:**
> Okay, so I did that, except all that happens is the Ventrilo Setup window flashes and then disappears.  Whats happening there?

Sorry, I'm really new to this. x_x

[Go here ]("http://appdb.winehq.org/appview.php?iVersionId=3936")and do all the setup if you havent.

---

### Post by Catewilliams on 2006-09-01
> **Kilz said:**
> [Go here ]("http://appdb.winehq.org/appview.php?iVersionId=3936")and do all the setup if you havent.


:/ It was still doing that. It would quickly flash a bar, then disappear after half a second. I can't install Ventrilo for this reason.

---

### Post by bluntu on 2006-09-10
How do I completely UNINSTALL wine? I messed up the drive_c thing via '$ winecfg' and don't know how to bring it back. I feel that by uninstalling it completely I can reinstall it and it would be normal.

---

### Post by bluntu on 2006-09-13
Ok I found the solution while playing around with Ubuntu.

If you accidently messed up the c: drive via '$ winecfg' what you can do to restore it is to create a LINK inside ~/.wine/dosdevices. That's where it keeps drives info.

```

$ cd ~/.wine/dosdevices
$ ln -s ~/.wine/drive_c c:

```

That should restore the C: thing if you get:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

---


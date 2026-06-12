---
title: "Uninstall itunes and quicktime?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-16
How do you do this, I installed both itunes and quicktime and don't know how to uninstall. 

Thanks

---

### Post by Lord_Dicranius on 2007-11-16
On Ubuntu?  Wasn't aware that iTunes had a Linux-based installer.  Are you using them through Wine, maybe?

I see from your profile that you marked as being a Windows user also.  Maybe this question is about uninstalling from your Windows desktop?  If so, go to the start menu>settings>control panel (depending on the version, you may not require the 'settings' step there).  Then open up "add/remove programs", find the application, click "remove".

---

### Post by GeorgiaBoot on 2007-11-16
Sorry for not being clear. I have itunes installed on Ubuntu with Wine. I have gone to add/remove but it is not there. I have also gone to Synaptic Package Manager and I can't find iTunes or Quicktime. I know it is installed cause I can go to Applications>Wine>Programs>iTunes or Quicktime. Thanks for any help.

---

### Post by LowSky on 2007-11-16
> **GeorgiaBoot said:**
> How do you do this, I installed both itunes and quicktime and don't know how to uninstall. 

Thanks

didn't I warn you about this in another thread?  :lolflag:


Wine has its own uninstaller. 
You can also delete the iTunes/Quicktime files by hand. This isn't windows so it wont screw up your registry.

---

### Post by por100pre1 on 2007-11-16
Did you tried the Wine uninstaller:

```
uninstaller
```

---

### Post by Lord_Dicranius on 2007-11-16
> You can also delete the iTunes/Quicktime files by hand.
This is what I've done to get rid of apps in Wine *shrug*

---

### Post by GeorgiaBoot on 2007-11-16
Ha, yes lowsky you did, and I am paying for it! I did the Wine uninstaller and clicked Uninstall and guess what it said? Installing itunes :(, it installed it again! 

Well I went into wine virtual Drive C. and manually deleted the files. It still shows up Quicktime and itunes in Wine>Programs but Owell.

Thanks for the help

---

### Post by Inxsible on 2007-11-16
I stay away from using windows apps in linux !!!

so no wine for me :)

drinking and driving is not good for health

---

### Post by GeorgiaBoot on 2007-11-16
I know, my first sip and I have already crashed! :)

Thanks for the Help Guys, very much appreciated.

---

### Post by Lord_Dicranius on 2007-11-18
> **GeorgiaBoot said:**
> It still shows up Quicktime and itunes in Wine>Programs but Owell.
You mean in the Applications menu?  If this is the the case, right click on "Applications", then select "Edit Menus".  From there you can remove them from the Wine folder :-)

---

### Post by muzosa on 2008-06-11
> **Lord_Dicranius said:**
> If this is the the case, right click on "Applications", then select "Edit Menus".  From there you can remove them from the Wine folder :-)

After numerous failed attempts to get rid of itunes and quicktime using wine's uninstaller, deleting the folders was the only solution that worked. Thanks for the help getting the detritus out of the wine folder.

I'm giving virtualbox a try instead. So far, so good.

---

### Post by elord on 2008-06-12
is this case solve already? maybe try this Applications>wine>Uninstall wine software if you install itunes in wine.. :)

---

### Post by yragrelluf on 2008-06-12
I had similar wine problems but with different windows apps. The way i solved it was to remove wine completely from my system using synaptic. Wine is a horrible program, and windows apps are juvenile. There is a free alternatives to anything, so why use the bloatware?

---


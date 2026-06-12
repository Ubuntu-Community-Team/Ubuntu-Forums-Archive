---
title: "How to &quot;completely&quot; uninstall stuff."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-01-06
I saw a post a few days ago about how to uninstall all the unused dependencies an app used.

Someone said that using add/remove and synaptic will install necessary dependencies, but will only uninstall the app itself.

How do you uninstall all the extra crap that isn't being used after the program is gone?

I'm not short on space, I'm just an anal minimalist.

---

### Post by thelatinist on 2008-01-06
Using Synaptic, right click on the package and choose "Mark for complete removal."

---

### Post by Pogeymanz on 2008-01-06
Oh, that's what I've been doing. Cool
And that gets rid of all the extra stuff that came with the app?

Just to make sure:
If I install Kubuntu-desktop and the pages of ugly KDE libs and files with it. Then I go and click complete removal, it will delete all those extra KDE files and libraries?

---

### Post by cartisdm on 2008-01-06
> **EmosSuck777 said:**
> Oh, that's what I've been doing. Cool
And that gets rid of all the extra stuff that came with the app?

Yeah that should do the trick, it'll give you a warning if anything else is using those packages for anything

---

### Post by mcduck on 2008-01-06
That gets rid of all the setting files as well as the app itself, but doesn't uninstall packages that were installed as dependencies.

To get rid of all the packages that were installed as dependencies, but are not needed any more as the original program has been removed, just go to Synaptic, click the 'Status'-button in lower left corner, then select the 'Autoremovable' and uninstall everything that it shows. Or just run "sudo apt-get autoremove" from a terminal..

---

### Post by Pogeymanz on 2008-01-06
That's what I was looking for! Thanks

---

### Post by thelatinist on 2008-01-06
> **EmosSuck777 said:**
> Oh, that's what I've been doing. Cool
And that gets rid of all the extra stuff that came with the app?

Oh, wait...I'm sorry.  I misunderstood. But mcduck beat me to it.

---

### Post by houstonbofh on 2008-01-06
You can also look at the "History" function under "File" and see what you installed.  Remove those components.  Autoremove will not catch everything.  You might want to look at gtkorphan as well.

---

### Post by mcduck on 2008-01-06
> **houstonbofh said:**
> You can also look at the "History" function under "File" and see what you installed.  Remove those components.  Autoremove will not catch everything.  You might want to look at gtkorphan as well.
True, autoremove doesn't detect everything, only almost everything ;)

The way to find the rest is to install deborphan, and then either add a new filter in Synaptic to show only orphaned packages, or install gtkorphan to get a separate GUI for uninstalling orphaned packages. I prefer the Synaptic way, as it's easier to do all the package management in the same program.

But be careful when removing orphaned packages; just because something is listed as orphaned doesn't mean that it's not used by anything. It only means that all your programs are able to run without that package, but it still might be that the package provides additional functionality for some program you are using.

For example many audio/video codecs I have installed show as orphaned packages. That means that all my audio/video players will work without those codec packages, they just won't play some files without them ;) So be careful, and make sure you know what the packages do before removing them as orphaned packages..

---

### Post by Odd-rationale on 2008-01-06
See this forum post:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Also, you can delete some of the hidden folders in your home directory.

---

### Post by tirzahsdad on 2008-02-03
Problems uninstalling vdrift.

I am a newbie.  I am new to posting and have been working with gutsy for only a few weeks now. Recently, I was able to get vdrift to run-although it didn't look pretty or run correctly.   Then Ubuntu locked up while I was trying it out and the whole system would not respond to any combination of keystrokes.  I had to restart.
  When ubuntu booted up again I tried "sudo dpkg --configure -a" and "sudo apt-get -f install." I assumed vdrift didn't install correctly  The next step I thought should be to remove it and reinstall it since neither one of these terminal commands pointed to the problem  But now I have been unable to find vdrift anywhere in add/remove (under games) nor in the synaptic package manager.  I don't understand, if nothing was broken in the installation or download, why wasn't it recognized system-wide; why isn't it listed in add/ remove?

Thanks and Best Regards,

Shawn

system:

p4-2.26Gz
768mb ram
radeon 9700 pro

OS: gutsy gibbon 7.10 (updated as of today 2/3/2008)

---


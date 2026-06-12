---
title: "Synaptic and APT-GET don't cleanly remove packages"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by CSMatt on 2007-01-30
While Ubuntu is much "cleaner" than Windows when it comes to left over fragments from removed programs, it still has issues.  For example, user application data is left in the /home/user folder after removal.  This is noticeable when you completely remove a package and them reinstall it.  It is even noticeable with similar packages.  For example, if I install xchat-gnome and xchat-gnome-common, use them, completely remove them, and install xchat and xchat-common, I find that the X-Chat settings are still there.  Just deleting the folder left over doesn't work either.  For example, if I install WINE, use it, completely remove it, delete .wine, and reinstall WINE, WINE complains of the missing .wine folder, even though it should have created a new one by thinking this is the first time it was installed.  Is this done on purpose, or is this a flaw?  Am I misunderstanding the meaning of "Completely remove package (including configuration files)"?  Is there a third-party uninstaller I can use if I need to?

PS: this might be in the wrong forum.  If it is, I apologize.

---

### Post by taurus on 2007-01-30
Yes, this one is definitely in the wrong forum.  

Move to Beginner Talk.

---

### Post by jvc26 on 2007-01-30
To remove config files as well you need to do a sudo apt-get --purge remove *** where *** is the app name. This is quite a helpful post for cleaning up ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)
Il

---

### Post by CSMatt on 2007-01-31
That still doesn't explain why when I removed WINE's config files and then reinstalled it it refused to re-create them.

---

### Post by macogw on 2007-01-31
I think it knows what files have been installed before.  VRMS complains (it tells you what on your comp isnt free software) about things you've uninstalled.  I guess it looks at the record and sees "oh, you had me before. where's my files?"

---

### Post by dcstar on 2007-01-31
> **CSMatt said:**
> That still doesn't explain why when I removed WINE's config files and then reinstalled it it refused to re-create them.

Running wine for the first time creates a (hidden) .wine directory with configuration data in a user's home directory.

Since this sort of this occurs after package installation, the uninstallation process has no control of these files and therefore will not touch them.

If you want to "reset" a wine installation, you simply delete (or rename) this directory.

---

### Post by Sef on 2007-01-31
If you use aptitude instead of apt-get,  then you can remove everything upon removal.

```
sudo aptitude install name_of _application
```

---

### Post by meng on 2007-01-31
> **CSMatt said:**
> That still doesn't explain why when I removed WINE's config files and then reinstalled it it refused to re-create them.
It shouldn't refuse to recreate them, it just complains that ~/.wine is not present the first time you run it, and it SHOULD then go ahead and create it for you.

---

### Post by CSMatt on 2007-02-02
> **macogw said:**
> I think it knows what files have been installed before.  VRMS complains (it tells you what on your comp isnt free software) about things you've uninstalled.  I guess it looks at the record and sees "oh, you had me before. where's my files?"

Then why aren't uninstallers written so that they remove all traces of a program, so that it appears from all cases like the program was never there in the first place?  There are supposedly third-party uninstallers for Windows that track all files installed or changed by a program so that they can all be purged or revoked upon uninstallation.  Although the sloppiness of built-in Windows uninstallers is mostly the fault of IstallShield or VISE or whatever proprietary software was used to install the product in the first place, and thus cannot be fixed by anyone who didn't make the installer, the ability to fix APT-GET or Synaptic so that it exhibits these monitoring behaviors (which should probably be optional for privacy reasons) should in theory be available to everyone who knows how to patch said installer, given that both are free software.  The same goes for NSIS.

---

### Post by dr_d on 2007-02-02
I agree this is a problem.

I think that there are too many different ways of installing packages in Ubuntu. I.e. Add/remove, apt-get, aptitude, Synaptic

Personally, I use *only* synaptic.. because it keeps a log of every change that was made.. so if I want to get rid of a package later I can get rid of it and all the dependencies I dont need.

As for hidden folders in the home directory yeah. I guess just dont install a whole lot of junk that you're just going to end up removing anyways and you should be right :)

And yes even though it's not ideal in Ubuntu it's a hellova lot worse in that disaster from Redmond.

---

### Post by macogw on 2007-02-02
> **CSMatt said:**
> Then why aren't uninstallers written so that they remove all traces of a program, so that it appears from all cases like the program was never there in the first place?  There are supposedly third-party uninstallers for Windows that track all files installed or changed by a program so that they can all be purged or revoked upon uninstallation.  Although the sloppiness of built-in Windows uninstallers is mostly the fault of IstallShield or VISE or whatever proprietary software was used to install the product in the first place, and thus cannot be fixed by anyone who didn't make the installer, the ability to fix APT-GET or Synaptic so that it exhibits these monitoring behaviors (which should probably be optional for privacy reasons) should in theory be available to everyone who knows how to patch said installer, given that both are free software.  The same goes for NSIS.

Use aptitude when you install, and then if you use aptitude to remove, it'll do it cleanly.  Aptitude, pulls in "recommended" not just "required" when it installs, and it removes all unused dependencies when it uninstalls.  It is superior to apt-get.  Synaptic is just a front-end for apt-get.  The settings in it can be changed so it behaves like aptitude though.  There is deb orphan to remove leftover debs from using apt-get, by the way.  If you use aptitude, you shouldn't ever have to worry about it though.

---

### Post by macogw on 2007-02-02
> **dr_d said:**
> I agree this is a problem.

I think that there are too many different ways of installing packages in Ubuntu. I.e. Add/remove, apt-get, aptitude, Synaptic

Personally, I use *only* synaptic.. because it keeps a log of every change that was made.. so if I want to get rid of a package later I can get rid of it and all the dependencies I dont need.

As for hidden folders in the home directory yeah. I guess just dont install a whole lot of junk that you're just going to end up removing anyways and you should be right :)

And yes even though it's not ideal in Ubuntu it's a hellova lot worse in that disaster from Redmond.

You're a bit confused.  There is apt-get, that is it.  Aptitude is a terminal-style GUI (try just typing "sudo aptitude" with nothing else) for apt-get that automatically does "recommended" along with "required" dependencies on both install and uninstall.  Add/Remove and Synaptic are two views of the same thing.  They function the same way, and are just laid out differently (I think they're really the same program, and Synaptic is "advanced view").  They by default use apt-get.  When you hit apply, it sends "apt-get install *whatever*" and then when you hit the yes-i'm-sure button it says "yes" to that little prompt.  If you change the settings, it'll use aptitude's behavior, but it's still the same program.  All 4 are apt.  They are just different interfaces.  By the way, even if you install through the CLI, Synaptic sees it.  Synaptic knows what I've installed from 3rd party sites using the double-click-on-a-deb method, even if it's nowhere to be found in the repos.

---

### Post by CSMatt on 2007-02-02
In that case, is there any way to configure synaptic to use aptitude instead of apt-get?

> **dr_d said:**
> Personally, I use *only* synaptic.. because it keeps a log of every change that was made.. so if I want to get rid of a package later I can get rid of it and all the dependencies I dont need.
Exactly where is this log?

---

### Post by dr_d on 2007-02-21
Hmm... I see. How do you change the settings in synaptic so that it behaves like aptitude... and would these settings work for the Update-manager also?

CSMatt, the log can be viewed from inside synaptic, File | History... or something like that. I just realized that the changed made using the Update-manager also get saved in this log so I'm pretty happy about that.

---

### Post by CSMatt on 2007-02-22
It's a shame that aptitude and apt-get installations and removals aren't recorded in this log.  Needless to say, I am quite pleased with aptitude.  I would very much like a GUI version of aptitude to be made in the near future.

---

### Post by dr_d on 2007-02-23
> It's a shame that aptitude and apt-get installations and removals aren't recorded in this log.

agreed.

i'm currently using synaptic+updatemanager and deborphan to handle all my package needs. it works quite well if you're looking for a GUI solution.

imo, the key advantage of aptitude is that it removes orphans, so deborphan places synaptic on equal footing w/ aptitude.

---

### Post by Kenneth Cochran on 2007-03-07
Back to the original question... had the same problem. Uninstalling a package doesn't uninstall its dependencies (there can be multiple packages with the same dependency). The .wine folder is created by the **libwine** package installation not the **wine** package. Reinstalling libwine should fix the missing .wine folder problem...at least it did for me.

---

### Post by CSMatt on 2007-03-15
After playing with gtkdeborphan a little, I've found that it really only does libraries.  If you tell it to look for orphaned packages of everything else, EVERY package that depends on another package shows up, even if that package is present.  I've found that Synaptic has an option to throw in recommended packages as well, but I don't see an option for removing packages that were thrown in with another package.  I also don't see an option for Synaptic to completely remove by default instead of remove (a non-issue anly if the packages removed aren't depended on by other packages).

Is there any hope that this will be added in 7.04?

---


---
title: "Removing Gnome"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by Hobbsee on 2005-09-15
Hey all...

I have both gnome and kde installed, and want to delete gnome, and all the programs.  How do I do this?  I've already tried the "sudo apt-get remove gnome-desktop", and it couldnt find the package...

If I cant do that, i might just dist-upgrade to breezy, and try that out...

---

### Post by SilentCacophony on 2005-09-15
The gnome-desktop seems to be in the universe repository on my setup, so you'd have to add extra repositories as outlined [here](http://ubuntuguide.org/index.html#extrarepositories), and update the package list.

I don't know if that'd work to remove it, though. Personally, I re-installed ubuntu with the 'server' install (minimal system,) and use aptitude to install X, window-manager, and such.

---

### Post by Hobbsee on 2005-09-15
[QUOTE=SilentCacophony]The gnome-desktop seems to be in the universe repository on my setup, so you'd have to add extra repositories as outlined [here](http://ubuntuguide.org/index.html#extrarepositories), and update the package list.

I don't know if that'd work to remove it, though. Personally, I re-installed ubuntu with the 'server' install (minimal system,) and use aptitude to install X, window-manager, and such.[/QUOTE]
 sorry, I meant that it wasnt installed, not that it couldnt be found...

Got the extra repositories, and synaptic confirms that gnome-desktop isnt installed.  I know that if you want to remove kde, you completely uninstall kde-libs and the rest uninstalls as well, as it depends on kde-libs, but I couldnt seem to find the gnome equivalent of that when i looked.

If all else fails, i may backup, upgrade to breezy (and hope like crazy that it doesnt wipe out my dual boot!  I dont want to reinstall windows again!), check it out, and if there's problems, use my kubuntu CD to have a clean install of kubuntu...

---


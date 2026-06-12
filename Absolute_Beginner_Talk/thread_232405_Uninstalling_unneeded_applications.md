---
title: "Uninstalling unneeded applications?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Fraoch on 2006-08-08
Hello:

My Ubuntu installation went very well and all my devices were properly detected and configured.

Perhaps I still have the Windows mindset here, but the first thing I did was look in the Synaptic Package Manager for unneeded items in order to remove them.

There were a lot of things I'd never need: Bluetooth, wireless, Swahili language localizations for Firefox, etc.  When I selected some of these items for removal, I noticed other packages got selected too, due to module dependencies I guess.  The text was a little alarming: it indicated, for example, that ubuntu-desktop would be uninstalled along with it.  I didn't think that's what would really happen, that only certain components would be removed or that the package would be reconfigured, but that's exactly what happened.  As soon as I applied the changes most of the icons disappeared and on reboot I went to the shell.

So is there any way to remove certain components without having to remove items like the desktop?  Are these components inseperable from other components?  It doesn't make sense that in order to remove the Bluetooth stack I have to remove the desktop, i.e. that the two are totally inseperable, but that appears to be the case...

Any advice?  Ubuntu is nice and snappy for me but I'd like to make it as snappy as possible by removing unneeded services.  Is this still Windows thinking?  Will these services and components slow down the machine?

Thanks.

---

### Post by jordilin on 2006-08-08
In Linux all is about dependencies. So, if you uninstall a software package may be another one will be removed. If you for instance remove the Mono platform, F-Spot, Tomboy and Beagle will be removed since they depend strongly on Mono. Welcome to the world of choices and dependencies :D

---

### Post by Fraoch on 2006-08-08
OK, thanks for the response.  That's that I guess.

It's still much faster than even Windows 98 on this machine, so I don't have too much to complain about.  I can't say there's any lag with just about anything I'm doing.

Thanks again.

---

### Post by hw-tph on 2006-08-08
I highly recommend aptitude for installing and removing applications. It may "only" be a console application but it is very powerful and helpful. If you use aptitude to install an application that pulls in several dependancies those will be installed - just like you would expect. But if you later uninstall that application (still using aptitude) it will also remove the dependancies unless they are needed by some other package. Very neat feature.

If you're looking to disable services, look into bum, the BootUp Manager. It will allow you to select what services to run in a pretty graphical user interface. If you're a console enthusiast just use sysv-rc-conf instead (it usually does the job faster too). Or, just do it the traditional Debian way, by using update-rc.d. Works wonders too.

Håkan

---

### Post by Delkster on 2006-08-08
> **Fraoch said:**
> There were a lot of things I'd never need: Bluetooth, wireless, Swahili language localizations for Firefox, etc.  When I selected some of these items for removal, I noticed other packages got selected too, due to module dependencies I guess.  The text was a little alarming: it indicated, for example, that ubuntu-desktop would be uninstalled along with it. 
Actually, ubuntu-desktop is merely a so-called metapackage. It contains no software itself, but it has been set to depend, directly or indirectly, on (at least almost) all other packages that comprise the default Ubuntu desktop. Thus, by installing it (or by having it installed) you are guaranteed to have everything belonging to the default setup. By removing it you don't automatically lose the actual software (unless your package manager of choice is keen to automatically remove so-called orphaned packages, i.e. those ones which are no longer depended on by any package). Thus, if you remove a package that belongs to the default setup (for example gaim), the package manager also wants to remove the ubuntu-desktop package, you no longer have the metapackage but you should still have everything else with the exception of gaim.

Removing the metapackage isn't dangerous but having it installed is useful in certain situations, for example in upgrades from one release to another.

Since I don't know what else was removed in your case apart from ubuntu-desktop, it's hard to say what happened.

> Any advice?  Ubuntu is nice and snappy for me but I'd like to make it as snappy as possible by removing unneeded services.  Is this still Windows thinking?  Will these services and components slow down the machine?
They probably won't slow it down directly but of course they consume memory, which may affect the performance of the system (although, if the services are never used, I suppose they get paged out of physical RAM over time if the memory is needed for other purposes).

I have disabled unnecessary services (generally called daemons in the unix world) just because I don't keep my computer running continuously and the system starts up a bit quicker with less things set to launch at boot. The `Services' configuration item that can be found in [System > Services] won't allow you to disable many of them, but the Boot-up Manager (found in the `bum' package in the universe repository) will provide more flexibility, although you'd better be careful about what you disable.

---

### Post by Fraoch on 2006-08-08
> **Delkster said:**
> Since I don't know what else was removed in your case apart from ubuntu-desktop, it's hard to say what happened.

Yeah, I kind of went overboard, removing many items.  One of them must've taken out GNOME.

I'll try stopping a few services.

Thanks for the responses.

---

### Post by Christmas on 2006-08-08
Yes, Delkster here explained it very well. Don't worry if Synaptic will automatically uninstall ubuntu-desktop, it won't harm Ubuntu.

---

### Post by jrjr on 2006-08-08
.

---


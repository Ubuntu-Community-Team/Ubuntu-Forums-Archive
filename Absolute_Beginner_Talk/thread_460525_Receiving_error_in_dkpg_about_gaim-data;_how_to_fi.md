---
title: "Receiving error in dkpg about gaim-data; how to fix?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by teknosexual on 2007-05-31
When I install/remove packages with aptitude, I receive the following error:

**dpkg: serious warning: files list file for package `gaim-data' missing, assuming package has no files currently installed.**

Generally, the package will go ahead and install or remove itself. However, I want to install w32codecs from mediubuntu, and dpkg stops after this error. 

I checked in Synaptic and the latest version of gaim-data is installed. So I'm confused as to what the issue is. I have removed Gaim, previously. I have also removed ubuntu-desktop, of course, since I removed Gaim. I have Pidgin installed currently. Everything is running smooth in those regards.

Would uninstalling gaim-data, then reinstalling it help? Would that conflict with my Pidgin installation? Do I even need gaim-data for anything? I understand it's some architecture for instant messaging, but if I'm not using Gaim (but I am using Pidgin), do I still need it?

Thanks in advance for the help!

Edit: Well, FWIW, I got DVD playback going by installed VLC player. *shrug* So, I guess I don't need the codecs from mediubuntu, but I'm still curious about the gaim-data dpkg error if anyone knows what's going on there.

---

### Post by stimpyaw on 2007-06-16
I'm getting a similar type of error:

[B]dpkg: serious warning: files list file for package 'gaim' missing, assuming package has no files currently installed.

[/B]I just now, removed 'gaim' and all its dependencies and all add-ons.  Did not restart system, but wait a few minutes and then reinstalled 'gaim' and add-ons I had installed before.

Now when I install or remove a package with Synaptic Package Manager, I do not receive the error message in the terminal screen.

---


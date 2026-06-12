---
title: "Nautilus &amp; GNOME error - New install. Help?"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by jmeccia on 2008-08-11
I'm completely new to Ubuntu and Linux.  I've been a Mac user for 10 years now and am very happy with OSX, I'm just looking to broaden my horizons and felt like trying to install Ubuntu on my PowerBook G4.

From what I can tell, Ubuntu 6.06 is the last version capable of running on a PowerPC mac, right?

So I downloaded and installed 6.06.  I can't get it to install.  When I boot from the CD it loads a scrambled video screen after the white screen.  It looks like the desktop background, but I cant make anything out.  I do hear the "startup chimes," but that's it.

So, I downloaded the Alternate Install (6.01, i think) and got it to work.  I installed Ubuntu, but when it ejects the cd and attempts to boot off the HD, it gives me the following errors upon loading the desktop:

"There was an error starting the GNOME Setting Daemon."

"There was a problem registering the panel with the bonobo-activation server.  The error code is 3.  The panel will now exit."

"Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.  Killing bonobo-activation server and restarting may help fix the problem."

Any advice?

Thanks, and I'm looking forward to getting this installed properly!

-J

---

### Post by vegenalle on 2008-08-11
> **jmeccia said:**
> I'm completely new to Ubuntu and Linux.  I've been a Mac user for 10 years now and am very happy with OSX, I'm just looking to broaden my horizons and felt like trying to install Ubuntu on my PowerBook G4.

From what I can tell, Ubuntu 6.06 is the last version capable of running on a PowerPC mac, right?

-J

Hello, there is a sticky thread where you can find an answer:

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

---

### Post by cyberdork33 on 2008-08-11
also check here:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by stream303 on 2008-08-11
> **jmeccia said:**
> I'm just looking to broaden my horizons and felt like trying to install Ubuntu on my PowerBook G4.

Welcome aboard!
Your horizons will probably be broadened at the outset, since sometimes ppc installs aren't a walk in the park.  Just being honest so you don't throw your powerbook through the window. :)

> From what I can tell, Ubuntu 6.06 is the last version capable of running on a PowerPC mac, right?

That is a common misconception since the "official" download links only to the older version from which you could get commercial support contracts for.  Nowadays, the ppc releases are "ports", meaning that they are supported by the user and dev community solely, and therefore no commercial support is available.  You have to come here and read the faqs / wikis and so forth to find the download location for the new good-stuff such as Hardy and Intrepid-Alpha for ppc!

Here's the download link for the latest:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Normally I recommend the "alternate" installer, but you may have to manually edit your /etc/X11/xorg.conf file, and perhaps your /etc/yaboot.conf file as well, since the ppc hardware doesn't always respond properly to Linux probing.

Check out the powerbook threads for ppc both here and in the read-only archives.

It may be a bit daunting for someone new to Linux, so that's why I want to put this out there right up front so you don't get frustrated at Ubuntu - we PPC users *wish* that our hardware responded properly during install, but in many cases it doesn't, so manual intervention is called for.  Not the fault of Ubuntu, or any other ppc distro for that matter.

Just take it slow, and most importantly, keep it fun.

---

### Post by jmeccia on 2008-08-12
stream303 --

you're info has been most helpful, and it appears I'm having similar problems to the bug mentioned in this 
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

However, I followed the author's directions, and I can't change my computer's clock.  It either tells me I don't have permission, or it says the timestamp is too far into the future.

Any advice?

I'm downloading Xubuntu and will see where that takes me.  Thanks, and despite the complication and confusion, I am actually enjoying the learning experience.

-J

---

### Post by stream303 on 2008-08-12
As for the permission problem, are you sure you are prefacing the date commands with sudo ?

If not, we might be able to do it using the rescue-mode, or in the single-user mode, but let's see if you are using sudo.

Told ya! :)  Anyway, sounds like you are keeping it fun rather than frustrating.  When you overcome a problem in ppc, it is like the clouds opening...

And which version of xubuntu are you downloading?

---

### Post by jmeccia on 2008-08-12
I'm typing:

sudo date -s "date"

and it will either reply date is too far in the future, or invalid command ??

I downloaded xubuntu 7.(10)?

---


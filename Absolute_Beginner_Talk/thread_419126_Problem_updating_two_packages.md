---
title: "Problem updating two packages"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-22
There are two update packaged waiting in Update Manager that I can't get installed: alsa-base and alsa-utils. 

I've cleared the cache and downloaded a second time with the same results. Here is the error message. > E: /var/cache/apt/archives/alsa-base_1.0.13-3ubuntu1_all.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/alsa-utils_1.0.13-1ubuntu5_i386.deb: subprocess pre-installation script returned error exit status 1

I don't know what error status 1 means nor how to fix this. Any thoughts?

---

### Post by mabelrxu on 2007-04-22
exit status 0 usually means no problems, completed successfully, and 1 usually means has a problem of some sort, although some programs return different numbers based on the problem ...

you can try sudo apt-get --fix-missing, then sudo apt-get --fix-broken, and then there should be no problems ... or at least, that's how it was with me ...

---

### Post by Patrick K on 2007-04-23
Thanks for the reply. I tried the code you suggested but got an error on --fix-missing. The -h file was shown. I looked in the man page but was unsccessful in getting the command to work. How do you run this command?

---

### Post by Sef on 2007-04-23
Try System > Administration > Synaptic Package Manger > Edit > Fix Broken Packages.

---

### Post by Patrick K on 2007-04-23
That didn't do it. Got the same error.

---

### Post by Patrick K on 2007-04-23
Bump. I hope someone has a solution to this as playback in Audacity is having problems. I need to get these updates before trying to troubleshoot the issue.

---

### Post by Patrick K on 2007-04-23
bump

---

### Post by mabelrxu on 2007-04-24
this probably isn't what you want to hear ...

when I was running ubuntu (edgy), I would have all kinds of problems, with video, sound, mouse, etc.
after switching to xubuntu (and upgrading while I was at it), no problems at all ... or at least, less problems

I have no idea why ...

---

### Post by Patrick K on 2007-04-24
Once I got it sorted out, Edgy was very solid for me. The sound worked fine. I'm not into desktop effects at all (recently took KDE off) so maybe xubuntu would be a good choice. 

I've wonder if the repositories have a corrupt copy of these files but I suspect not or others would have this issue. 

Thanks for the bump. 
apt-get moo

---

### Post by hanzomon4 on 2007-04-24
Try running this in a terminal ```
sudo apt-get upgrade 
``` Post the output

---

### Post by Nythain on 2007-04-24
not sure if you have fixed your problem yet, but you could try this...

first change the country code for your repositories in your /etc/apt/sources.list (in case the repo you got them from contained a corrupt copy or something)

then i would sudo aptitude clean (to remove the old packages from apt cache)

sudo apt-get update (for a new, complete, up to date list of packages available, maybe the ones you grabbed were bugged and its fixed now, who knows)

finally sudo apt-get upgrade (to re-download and install the packages again)

---

### Post by Patrick K on 2007-04-24
I ran the list of commands and still got the error. Four new upgrades installed fine. The same two didn't. Here is the output:> Errors were encountered while processing:
 /var/cache/apt/archives/alsa-base_1.0.13-3ubuntu1_all.deb
 /var/cache/apt/archives/alsa-utils_1.0.13-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Here is the specific output:> Preparing to replace alsa-base 1.0.11-5ubuntu1 (using .../alsa-base_1.0.13-3ubuntu1_all.deb) ...
rm: cannot remove `/etc/alsa/dev.d/alsa-base': Not a directory
dpkg: error processing /var/cache/apt/archives/alsa-base_1.0.13-3ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace alsa-utils 1.0.11-6ubuntu2 (using .../alsa-utils_1.0.13-1ubuntu5_i386.deb) ...
rm: cannot remove `/etc/alsa/dev.d/alsa-base': Not a directory
dpkg: error processing /var/cache/apt/archives/alsa-utils_1.0.13-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1


It seems the files aren't located where the script is expecting them. Alsa-base is in the modprobe.d directory. Alsa-utils is in the /etc/init.d directory. I can't create an /etc/alsa directory since there is already a file named alsa there. 

I suspect that either the original install put these files in the wrong location (although the sound system worked fine) or the upgrade script is incorrect. I can't see any other reasons for this problem. Thoughts?

---

### Post by hanzomon4 on 2007-04-25
Uninstall and then reinstall the two packages

---

### Post by Patrick K on 2007-04-25
I thought about that but it took many hours over several days to get alsa working properly. I'd rather not if I can avoid it and there is no assurances that that will fix the problem.  I posted a bug report and they are trying to recreate the problem. I'm going to wait to hear more from them.

---


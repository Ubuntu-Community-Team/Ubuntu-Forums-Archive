---
title: "[SOLVED] New at linux"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by DGGARCIA on 2007-12-30
Hi all,

I was really piss off of windows vista in particular and windows and Mr. Gates in general and i decided to change to Ubuntu.This was 3 days ago.Now I'm trying to understand how to use it.I'm installing some programs from the package gestor but this morning i got an error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I was checking the forum for any ideas to fix it. I found one talking about delete the contents of the folder /var/lib/dpkg/updates using the terminal window and writing: sudo rm /var/lib/dpkg/updates/*

I did it but is asking me for a password that i don't know so i used the same i have when i start the laptop but is not this one..And i don't really have a clue of what password i have to use.

Thanks in advance for your help and sorry for my English. I'm a spanish working in Ireland and i'm still improving.

Diego.

---

### Post by Perfect Storm on 2007-12-30
The password should be the same as the password you installed Ubuntu. Remember that linux is case-sensitive and make sure you spelled it right.

To fix the problem do;
```
sudo dpkg --configure -a
```

---

### Post by Samhain13 on 2007-12-30
> /var/lib/dpkg/updates/

Try removing the trailing backslash (/) that so that it says: /var/lib/dpkg/updates
I can't help you with your real problem though, sorry.

---

### Post by x1a4 on 2007-12-30
The sudo password is the one you used to login.

---

### Post by DGGARCIA on 2007-12-30
Thanks a million..

Now is working..

One last thing..which package u recommend me to watch the flash videos from youtube?

I was trying to download adobe flash and this cause the problem.

Thanks again

Diego

---

### Post by overdrank on 2007-12-30
> **DGGARCIA said:**
> Thanks a million..

Now is working..

One last thing..which package u recommend me to watch the flash videos from youtube?

I was trying to download adobe flash and this cause the problem.

Thanks again

Diego

Hi and these links should help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by Fixman on 2007-12-30
> **DGGARCIA said:**
> Thanks a million..

Now is working..

One last thing..which package u recommend me to watch the flash videos from youtube?

I was trying to download adobe flash and this cause the problem.

Thanks again

Diego

If you aren't using Ubuntu 64-bit edition, I reccommend you ```
 sudo aptitude install flashplugin-nonfree 
```

---

### Post by SOULRiDER on 2007-12-30
From IRC:
**The Flash plugin installation is currently broken. This is due to Adobe changing the tar file that the package downloads. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) if you need to fix this immediately, but it's recommended to wait for an official fix.**

Ceck out that thread or [http://ubuntu-tutorials.com/2007/12/26/manually-install-adobe-flash-temporary-flashplugin-nonfree-fix/](http://ubuntu-tutorials.com/2007/12/26/manually-install-adobe-flash-temporary-flashplugin-nonfree-fix/) so you can see how to install flash. If you got any questions just ask.

---

### Post by DGGARCIA on 2007-12-30
Thanks everybody for the help.

After check in some links i found the solution to my problem.

Now i can watch all the videos.

The link with the last version of the wright Adobe Flashplayer is:

[http://fr.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb) 

Thanks again.it has been a great help

Diego:)

---

### Post by SOULRiDER on 2007-12-30
Cool, im glad you got it working :)

---


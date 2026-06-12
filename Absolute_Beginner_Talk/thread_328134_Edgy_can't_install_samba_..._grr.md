---
title: "Edgy: can't install samba ... grr"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by negativ on 2006-12-30
](*,) 

$sudo aptitude install samba


Setting up samba (3.0.22-1ubuntu4) ...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libcrypt-smbhash-perl (0.12-1) ...
Setting up smbldap-tools (0.9.2-3) ...

Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu4) ...
 * Starting Samba daemons...                                             [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba


no clue whatsoever what to try,

---

### Post by UltraMathMan on 2007-01-07
Same problem, any help would be appreciated. In the meantime I guess I'll keep searching

giving [this]("http://www.ubuntuforums.org/showthread.php?t=240699&highlight=install+samba+error") a go...

---

### Post by Jagermaster on 2007-01-07
I believe Samba should already be installed?

I had a hard time figuring it out too because I tried KDE before Gnome.
Gnome doesnt have it up front and easy...like KDE did.

Try this:
Go to **Places - Home Folder** then click the icon next to the location bar switch into text mode.
Next enter > smb:///
Hopefully your windows network will show right up.

After you find the networked computers, dont forget to bookmark them.

---

### Post by UltraMathMan on 2007-01-07
that thread, above post, fixed it - hooray for shared printing :)

---


---
title: "Samba files don't show up in windows!"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-08-08
I cant find my ubuntu PC in My network places > view workgroup computers > workgroup.  The other windows PC is here, as well as the one I'm using.

I setup for sda5 aka "DISK" to be shared on the workgroup/domain 10.0.0.2.

The two windows PCs are connected via wireless, and the ubuntu PC is connected with a cat5 cable to the router.

Any help please?

EDIT: Found it it wasnt in workgroup! Was in "10.0.0.1"

I feel stupid

---

### Post by ukripper on 2007-08-08
open you smb.conf:

```
sudo gedit /etc/samba/smb.conf
```

and find 
**; browseable = no **

and change it to** browseable = yes**   (don't forget to remove semicolon from front)

and do same with **writable**

then 
 save and restart your samba daemon with follwoing command

```
sudo /etc/init.d/samba restart
```

---

### Post by Hendrixski on 2007-08-08
> **ukripper said:**
> open you smb.conf:

```
sudo gedit /etc/samba/smb.conf
```

and find 
**; browseable = no **

and change it to** browseable = yes**   (don't forget to remove semicolon from front)

and do same with **writable**

then 
 save and restart your samba daemon with follwoing command

```
sudo /etc/init.d/samba restart
```

wow, that's good to know!  I've had problems up the wazoo with Samba.  It works perfectly when you're sharing with other UNIXen like Mac OS X or Linux, even OpenSolaris.  But with windows sometimes it's like "hah hah, I'm going to hide from that f*cker, hah hah hah".  Maybe this will help me in the future.

---

### Post by ukripper on 2007-08-09
> **Hendrixski said:**
> wow, that's good to know!  I've had problems up the wazoo with Samba.  It works perfectly when you're sharing with other UNIXen like Mac OS X or Linux, even OpenSolaris.  But with windows sometimes it's like "hah hah, I'm going to hide from that f*cker, hah hah hah".  Maybe this will help me in the future.

Windows can be pain when it comes down to detecting  other machines and smb protocol for windows is just like giving the gun to a donkey. Unix and Linux like OS never would have that problem because they are developed keeping networking in mind.

---


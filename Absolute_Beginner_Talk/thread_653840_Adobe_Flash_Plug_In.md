---
title: "Adobe Flash Plug In"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2007-12-30
Get notification to upgrade Adobe Flash Plug-in installer.  Click on install and get following error message:   " E: tzdata: subprocess post-installation script returned error exit status 1".  What does this mean?  Is it important?  If so, how do I correct the error.
CB

---

### Post by Desolator on 2007-12-30
The installation of the Adobe Flash plug-in is currently broken. If you have it installed, good, else go to Gnash.

---

### Post by hyper_ch on 2007-12-30
you can manually install it:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

--> the tar.gz one.

---

### Post by Covalent Bond on 2007-12-30
Desolator:

Thanks for the Info.  Will ignore.
CB

---

### Post by shuttleworthwannabe on 2007-12-30
I used [these instructions]("http://ubuntuforums.org/showthread.php?t=642816") as a workaround. Hope you find them useful.

---

### Post by flamelab on 2007-12-30
Uninstall first everything regarding flash and then download the tar.gz file from Adobe .

Untar it somewhere , for example /Desktop and then 

```
sudo -s H
```

```
cd /home/yourname/Desktop/flash-player <-- that's an example
```

```
chmod +x flashplayer-installer.sh
```

```
./flashplayer-installer
```

and do what it says.

---


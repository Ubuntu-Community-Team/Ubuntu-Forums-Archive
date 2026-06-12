---
title: "WineHQ Repositories"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by jsimmons on 2005-06-24
I tried to add the wineHQ repositories, but synaptic gave me errors about the entry.  Could someone please describe to me how to add them?  I tried within Synaptic itself, but they never  showed up in the list, and if I tried to manually edit the list in a text editor, Synaptic produced the errors I mentioned earlier.

BTW, how long does it typically take for new versions of programs to be added to the Ubuntu repositories?

---

### Post by N'Jal on 2005-06-24
I have had this problem myself in the past, and today it works, and i don't know why. Here is my /etc/apt/sources.list for to look at. To be honest i don't really know why that happens, but sometimes in Linux it's like that. Forgive my simplfiying the comments, it's the only way i knew what was going on.

#Has all main repo's
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

# Wine repo's
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

# ubuntu backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by jdong on 2005-06-24
Make sure you try to use Reload at least twice with Synaptic; sf.net is pretty flaky when it comes to APT... I speak from experience ;)

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=jsimmons]
BTW, how long does it typically take for new versions of programs to be added to the Ubuntu repositories?[/QUOTE]

The official Ubuntu repositories never have updated pacakges (beyond security updates).

If you want new stuff, requesting backports is the way:

[http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)

---


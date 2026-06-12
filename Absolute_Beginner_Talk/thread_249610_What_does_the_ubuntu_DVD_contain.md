---
title: "What does the ubuntu DVD contain?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-09-02
i noticed on [www.ubuntu.com/download](www.ubuntu.com/download) there's a dvd downloads section.  i wanted to know what is the dvd actually made of, as in what extra packages, is it the alternate and the live cd at the same time, does it have all three desktop environments available to install, and if there are extra packages, are you forced to install them if you choose the default installation method?

---

### Post by meng on 2006-09-02
I think it's just extra packages, as there are separate Ubuntu and Kubuntu Live CDs. The downloads page has a file/package manifest that you can peruse.  In other words, not really useful unless you need to install lots of stuff and don't have a working internet connection.

---

### Post by aysiu on 2006-09-02
I believe it has the entire Main and Restricted repositories. I don't know if it allows you the Alternate installation, though.

---

### Post by user1397 on 2006-09-04
> **aysiu said:**
> I believe it has the entire Main and Restricted repositories. I don't know if it allows you the Alternate installation, though.well I finally got the scoop on the ubuntu dvd.  i downloaded it from the 'Europe' link in [www.ubuntu.com/download](www.ubuntu.com/download), and even though it was ftp and im living in the US, the d/l speed was 405-430 kbps!

Anyways, it is a combination of the desktop/alternate/server cd's, because the options available at boot are:
"Start or Install Ubuntu
Install in Text Mode
Install in OEM Mode
Install in Server Mode
Check for Defects"
and maybe a few other ones I can't remember.

And yea you were right aysiu, it contains the entire main/restricted repositories.  after I added the cd-rom as one of my repositories, I looked at my sources.list and at the top it said:
> ## Uncomment the following two lines to fetch updated software from the network
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

One question however, if the dvd has the entire main/restricted repos, what do the regular desktop cd or the alternate cd have in respect to repos?

---

### Post by aysiu on 2006-09-04
The Deskop CD has *ndiswrapper* and *build-essential*. That's it.

The Alternate CD has whatever desktop environment it's for--like *kubuntu-desktop* for Kubuntu or *xubuntu-desktop* for Xubuntu.

---

### Post by user1397 on 2006-09-04
> **aysiu said:**
> The Deskop CD has *ndiswrapper* and *build-essential*. That's it.

The Alternate CD has whatever desktop environment it's for--like *kubuntu-desktop* for Kubuntu or *xubuntu-desktop* for Xubuntu.wow, i didnt know that.  so if you install ubuntu with the desktop cd, you would get the ubuntu-desktop, ndiswrapper, and build-essential packages only, but if you installed ubuntu with the alternate cd you would have ubuntu-desktop and that's it?

---

### Post by aysiu on 2006-09-04
No, sorry--the Alternate CD also has *ndiswrapper* and *build-essential*.

The Desktop CD does **not** have *ubuntu-desktop*.

---

### Post by user1397 on 2006-09-09
> **aysiu said:**
> No, sorry--the Alternate CD also has *ndiswrapper* and *build-essential*.

The Desktop CD does **not** have *ubuntu-desktop*.okay, if i'm getting this right then, if you added the alternate cd as a repository, you would be able to install ubuntu-desktop, ndiswrapper, and build-essential from it.  But if you added the desktop cd as a repo, you would not be able to install anything but the ubuntu-core package?

---

### Post by aysiu on 2006-09-10
> **erik1397 said:**
> okay, if i'm getting this right then, if you added the alternate cd as a repository, you would be able to install ubuntu-desktop, ndiswrapper, and build-essential from it.  But if you added the desktop cd as a repo, you would not be able to install anything but the ubuntu-core package?
If you add the Desktop CD as a repository, you will be able to install only *ndiswrapper* and *build-essential*. That's it. No *ubuntu-core*. Nothing else.

---

### Post by user1397 on 2006-09-10
> **aysiu said:**
> If you add the Desktop CD as a repository, you will be able to install only *ndiswrapper* and *build-essential*. That's it. No *ubuntu-core*. Nothing else.wow, that sucks.  good thing i have all of main and restricted on my dvd.  

i went to synaptic package manager, and in settings > repos, i unticked everything except my dvd repo, and was able to see after i reloaded, that there were over 3,000 packages available to install (the main & restricted repos).  not too shabby.

---


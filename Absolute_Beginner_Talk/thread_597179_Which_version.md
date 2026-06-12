---
title: "Which version?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by olwe on 2007-10-30
I'm new to U-land and I see many different versions, but not really much detail about them. I'm used to Fedora where they say in the install "Desktop," "Developer," "Server," "Everything." I'd like everything. I'd like KDE, all developer tools and the full LAMP setup too. How do I get all that now that I've chosen Ubuntu 7.10?

---

### Post by ShogunMaster06 on 2007-10-30
You'll want to install Kubuntu 7.10.  Once installed, fire up the Synaptic package manager and all the packages are categorized.  You can choose the packages you want from the Developer section (as well as any others).  I think this is similar to YUM in Fedora.  It's just not set up to install while installing the distro.

---

### Post by bubbalouie on 2007-10-30
Use Kubuntu if you like KDE, to get LAMP you may need to install the components you need.

The following site has some great howtos: [http://ubuntuguide.org/](http://ubuntuguide.org/)

This covers installing LAMP: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by olwe on 2007-10-30
So I'll need to reinstall completely with the KUbuntu? There's no way to apt it over on Ubuntu 7.10?

---

### Post by rbprogrammer on 2007-10-30
if you want developer tools, after you install kubuntu, do a 
```
$ sudo apt-get install build-essential
```

many people forget to install that then try to write some programs.

---

### Post by AndyCooll on 2007-10-30
The versions on the whole refer to the desktop environment e.g. Ubuntu for GNOME, Kubuntu for KDE, Xubuntu for Xfce etc. And although not numbered there is a clear progression since the numbering refers to the release date, e.g. 7.10 refers to October 2007. The Gutsy Gibbon is just a development referral name, which IIRC Fedora also has even if its not so well known.

Although Ubuntu doesn't have collections in quite the same way as Fedora does, both Synaptic and  Add/Remove have sections where you can browse by type of app.

:cool:

---

### Post by AndyCooll on 2007-10-30
> **olwe said:**
> So I'll need to reinstall completely with the KUbuntu? There's no way to apt it over on Ubuntu 7.10?

```
sudo apt-get install kubuntu-desktop
```

That will do the trick. Once installed, logout and then before logging in choose the KDE session.

:cool:

---

### Post by LowSky on 2007-10-30
go into synaptic and look for KDE its ther

---

### Post by LowSky on 2007-10-30
go into synaptic and look for KDE its there

---

### Post by jaybombalous on 2007-10-30
> **AndyCooll said:**
> ```
**sudo apt-get install kubuntu-desktop**
```

That will do the trick. Once installed, logout and then before logging in choose the KDE session.

:cool:

then make sure its set as default.

---

### Post by Cochise on 2007-10-30
open a terminal and type sudo apt-get install kubuntu-desktop

this will download and install kde for you. to remove gnome etc open a terminal again and type sudo apt-get remove ubuntu-desktop

---


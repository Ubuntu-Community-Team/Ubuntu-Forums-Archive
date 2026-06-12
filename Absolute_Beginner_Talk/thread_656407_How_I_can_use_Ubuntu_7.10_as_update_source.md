---
title: "How I can use Ubuntu 7.10 as update source?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-02
Hi
Thank you for reading my post
I have a 7.10 DVD and I installed the ubuntu from it, but it does not asks me to choose packages that I want to be installed.
Is there any way that I can use it as update source to install more packages using add /remove program feature?
I dont like to use bandweidth for downloading things that I already have.

Thanks.

---

### Post by llamakc on 2008-01-02
Sure, if the packages are on the DVD.

Put the disc in the drive, and in a terminal type:

```

sudo apt-cdrom add

```

Now you can install packages from it with Add/Remove, Synaptic, or apt-get.

I also checked the menu SYSTEM | ADMINISTRATION | SOFTWARE SOURCES and at the bottom there is a blurb about how you just insert the cd/dvd to add packages from it, so the method I described above may now be integrated into Gutsy.

---

### Post by logos34 on 2008-01-02
insert dvd
system>admin>synaptic>settings>repos>ubuntu software tab>check cdrom/dvd box bottom

---


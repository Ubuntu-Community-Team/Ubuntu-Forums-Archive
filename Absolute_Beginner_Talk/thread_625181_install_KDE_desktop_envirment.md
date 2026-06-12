---
title: "install KDE desktop envirment"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-11-27
is there anyway that i can install kde desktop envirment without all the goofy apps that come with the kde envirment

---

### Post by rsambuca on 2007-11-27
sudo apt-get install kde-core

will install just the minimum required for the kde desktop and a few apps.

---

### Post by fedex1993 on 2007-11-27
or can can i build it from source

---

### Post by rsambuca on 2007-11-27
Of course, but why?

---

### Post by vikram on 2007-11-27
multiple options are listed in the doc.


[https://help.ubuntu.com/community/InstallingKDE?highlight=%28kde%29](https://help.ubuntu.com/community/InstallingKDE?highlight=%28kde%29)


if you arent short of disk space why not install the kubuntu-desktop and try some of the 'goofy' apps ? if you remove what you dont like later.

you may find yourself loving the 'goofy' apps as I have :)

---

### Post by aysiu on 2007-11-27
If you you don't want any of the "silly" apps that come with KDE, I would advise installing *kdebase* instead of *kde-core* or *kubuntu-desktop*: ```
sudo aptitude update
sudo aptitude install kdebase
```

---

### Post by rsambuca on 2007-11-27
The only difference between the kdebase and kdecore is the kdelibs, which you will likely need anyways, and the arts sound system.  Not a big deal either way.

---

### Post by aysiu on 2007-11-27
> **rsambuca said:**
> The only difference between the kdebase and kdecore is the kdelibs, which you will likely need anyways, and the arts sound system.  Not a big deal either way.
That's weird. I thought it was more than that.

You're right, it's mainly libs... and the arts sound system.

---

### Post by fedex1993 on 2007-11-27
heres another good question can i install kde4 with kde

---

### Post by jpittack on 2007-11-27
I am interested in trying out KDE, of course coming from Gnome.  Is it possible to switch between the two with ease?  I am assuming that I choose to install kde-desktop and then install gnome-desktop to get back to where I was.

---

### Post by -grubby on 2007-11-27
yes, you can switch between them at will on the login manager under "session"

---

### Post by fedex1993 on 2007-11-28
so does anyone know i i can install kde4

---

### Post by Incense on 2007-11-28
> **fedex1993 said:**
> so does anyone know i i can install kde4

Yes

[http://http://kubuntu.org/announcements/kde4-rc1.php]("http://http://kubuntu.org/announcements/kde4-rc1.php")

---

### Post by fedex1993 on 2007-11-28
> **Incense said:**
> Yes

[http://http://kubuntu.org/announcements/kde4-rc1.php]("http://http://kubuntu.org/announcements/kde4-rc1.php")

ty very much i love kde4 for somereason i wish gnome going to come out with something new

---

### Post by EtniesBMX on 2007-11-29
> **jpittack said:**
> I am interested in trying out KDE, of course coming from Gnome.  Is it possible to switch between the two with ease?  I am assuming that I choose to install kde-desktop and then install gnome-desktop to get back to where I was.

its actually easier than re-installing/un-installing between the two. it's explained in detail here: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

all you're really doing is this:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

then go back to the login screen and choose **kde** from the sessions menu.

---


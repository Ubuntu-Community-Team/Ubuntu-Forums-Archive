---
title: "KDE desktop"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by skizz on 2006-07-09
Okay, this is my first post on this amazing forum. First of all, I want to say 'Hello' to all of you. And I thank you all... The outstanding How-To's made my (Ubuntu) Linux axperience much easier.
So, let's get to the real business. As shown, I operate the Ubuntu Dapper 6.06 LTS. The Gnome desktop is very friendly, easy-to-use. But, one day, someone told me that Kubuntu uses the KDE desktop which is a good experience. Well, I wanted KDE on my Ubuntu, with dual desktop-interface (gdm and kdm). Okay, I googled it a little. Helping myself with [this]("http://www.psychocats.net/ubuntu/kde.html"), I used: 

```
sudo aptitude update
```

Then:

```
sudo aptitude install kubuntu-desktop
```

It downloads and installs like a charm. I log out from Gnome panel, select the KDE session but not as default. Well, it's working. I played a little with the new applications, then logged back in Gnome. There, a little surprise. My internet connection wasn't working. Okay, I reboot... Same problem. KDE is the problem, I thought. I used:

```
sudo aptitude remove kubuntu-desktop
```

It uninstalls correctly. I reboot again, but I couldn't run any administrative applications in Gnome. No Synaptic, no Terminal. 

As a conclusion of all this stuff, I barely realised that kubuntu-desktop isn't compatible with ubuntu-desktop, on the same machine.

But I still want that KDE on my Ubuntu machine... I don't want all Kubuntu applications, nor Kubuntu settings. I only want KDE itself. Can you guys help me out?

Cheers,
A.

---

### Post by user1397 on 2006-07-09
> **skizz said:**
> Okay, this is my first post on this amazing forum. First of all, I want to say 'Hello' to all of you. And I thank you all... The outstanding How-To's made my (Ubuntu) Linux axperience much easier.
So, let's get to the real business. As shown, I operate the Ubuntu Dapper 6.06 LTS. The Gnome desktop is very friendly, easy-to-use. But, one day, someone told me that Kubuntu uses the KDE desktop which is a good experience. Well, I wanted KDE on my Ubuntu, with dual desktop-interface (gdm and kdm). Okay, I googled it a little. Helping myself with [this]("http://www.psychocats.net/ubuntu/kde.html"), I used: 

```
sudo aptitude update
``` 
Then:

```
sudo aptitude install kubuntu-desktop
``` 
It downloads and installs like a charm. I log out from Gnome panel, select the KDE session but not as default. Well, it's working. I played a little with the new applications, then logged back in Gnome. There, a little surprise. My internet connection wasn't working. Okay, I reboot... Same problem. KDE is the problem, I thought. I used:

```
sudo aptitude remove kubuntu-desktop
``` 
It uninstalls correctly. I reboot again, but I couldn't run any administrative applications in Gnome. No Synaptic, no Terminal. 

As a conclusion of all this stuff, I barely realised that kubuntu-desktop isn't compatible with ubuntu-desktop, on the same machine.

But I still want that KDE on my Ubuntu machine... I don't want all Kubuntu applications, nor Kubuntu settings. I only want KDE itself. Can you guys help me out?

Cheers,
A.so you want to only have the kubuntu-desktop, as in not having the ubuntu-desktop?

---

### Post by woedend on 2006-07-09
you could just try installing the package kde
sudo aptitude install kde

may or may not work i am not there to try it out.

---

### Post by skizz on 2006-07-09
> so you want to only have the kubuntu-desktop, as in not having the ubuntu-desktop?

No. I still want my ubuntu-desktop. I don't want the kubuntu-desktop. I only want Kubuntu's graphical interface, KDE.

Cheers,

A.

---

### Post by skizz on 2006-07-09
> **woedend said:**
> you could just try installing the package kde
sudo aptitude install kde

may or may not work i am not there to try it out.

Nice tip. I will try that. I will keep you up-to-date with the progress.

Cheers,

A.

---

### Post by cyberlite on 2006-07-09
Just installed kubuntu, very very cool, for more info go here---> [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by kinematic on 2006-07-09
> **skizz said:**
> No. I still want my ubuntu-desktop. I don't want the kubuntu-desktop. I only want Kubuntu's graphical interface, KDE.

Cheers,

A.

i think you're confusing things.
ubuntu uses the gnome gui(ubuntu-desktop)and kubuntu the kde gui(kubuntu-desktop)and you can't run kde on top of gnome.
if you want kde you have to run kubuntu or install kde-base and expand on that.
that  gives you the ubuntu base with a fully configured kde(kubuntu)or you can install kde-base wich you can build upon yourself and customize from scratch(could also be kde-core...i'm not sure).

---

### Post by aysiu on 2006-07-09
Considering this is the first time I've ever seen a new desktop environment killing someone's internet connection, I'm going to assume this is a freak accident (I have seen a **lot** of posts, my friend).

It's also entirely possible that this has nothing to do with the addition of KDE and is merely a coincidence. It's hard to diagnose without any error messages.

---

### Post by skizz on 2006-07-09
> **aysiu said:**
> Considering this is the first time I've ever seen a new desktop environment killing someone's internet connection, I'm going to assume this is a freak accident (I have seen a **lot** of posts, my friend).

It's also entirely possible that this has nothing to do with the addition of KDE and is merely a coincidence. It's hard to diagnose without any error messages.

Hmm. The internet connection was working on the KDE session, but not on the Gnome one. The kubuntu network settings are a little bit different from the ubuntu ones. I think that the settings were overexposed and conflicting.

---

### Post by cyberlite on 2006-07-09
Hey I just install kde and all whent good. \\:D/  I,m using it now, so at the start of the OS when it asks me for the password I can loggon in kde or gnome.

Personely I like kde better but hey that is just me. 
I just cant ajust the refresh rate from 75 to 100 hz like I can in gnome but I will figer it out.

---


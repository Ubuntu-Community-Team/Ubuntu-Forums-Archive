---
title: "Error with SU?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Tixer on 2006-02-13
I recently installed Kubuntu (as in 5 mins ago) and when I got to my desktop, I couldnt get on the net. I have used SuSE before, but my main reason for moving to Ubuntu would be automatix.

I went into Settings, then Network settings, and I click Admin mode, or whatever. When I hit this, I get an error saying SU Commited suicide, and I cannot access it. I cant go into terminal and hit "su root", because it asks me for a pword I do not know.

Why can I not do this, and how can I fix it. Keep in mind that I have the Linux experience of a door (without knob!) and know nothing, but I am competent with Windows. Please help soon, MCE is pissing me off

---

### Post by Robgould on 2006-02-13
Your root account is not enabled by default in Ubuntu. The last time I tried Kubuntu, one of the reasons I left it is that the administrator mode is broken. There are (were) several threads about this in the kubuntu forums. There are workarounds.  IMHO kubuntu is very rough.
 
[http://www.kubuntuforums.net/]("http://www.kubuntuforums.net/")

---

### Post by Tixer on 2006-02-13
Is there any way to run Ubuntu with KDE? I am more familiar with KDE than with GNOME, so I dont wanna switch

---

### Post by Adrian on 2006-02-13
[QUOTE=Tixer]Is there any way to run Ubuntu with KDE? I am more familiar with KDE than with GNOME, so I dont wanna switch[/QUOTE]

Kubuntu **IS** just Ubuntu with KDE.

Read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

...and enjoy Kubuntu. It's very nice :)

---

### Post by Tixer on 2006-02-13
He was saying though that Kubuntu is rough, and I want stable. Is there any way to run Normal Ubuntu with KDE

Keep in mind my Linux knowledge, so the n00bish questions.

---

### Post by Adrian on 2006-02-13
[QUOTE=Tixer]He was saying though that Kubuntu is rough, and I want stable. Is there any way to run Normal Ubuntu with KDE

Keep in mind my Linux knowledge, so the n00bish questions.[/QUOTE]

Well, I would say that Kubuntu is quite stable. And in fact, it IS "normal Ubuntu with KDE".

You can have both Gnome and KDE desktops installed at the same time. If you for instance install Ubuntu (with Gnome) and later decides to install the **kubuntu-desktop** package (containing KDE), you will have both "Kubuntu" and "Ubuntu" installed and will be able to switch between them from the login screen. Similary, you can install "Ubuntu" from Kubuntu by just installing Gnome. The only difference really is the desktop environment.

And for most people, Kubuntu Breezy works just fine. The previous version was somewhat buggy, but that was because it was the first Kubuntu release ever. The current version is very good and stable. Highly recommended!

---

### Post by Robgould on 2006-02-13
Here is a more specific post about administrator mode in kubuntu. If you go there and search the forum for "administrator mode" you will find several pages of posts. I am not saying Kubuntu is not stable. It is ubuntu underneath. Ubuntu comes with gnome as a front end (what you see). Kubuntu is the same system underneath, but has KDE as front end. I just found it a bit aggravating when I used it. I think that something as fundamental as the KDE administrator mode should work.
 
[http://kubuntuforums.net/forums/index.php?topic=579.0]("http://kubuntuforums.net/forums/index.php?topic=579.0")

---

### Post by Tixer on 2006-02-13
Enabling the root account

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root 

I just tried that, and I got a message saying, from what I remember, "Cannot Look up Ubuntu ()0" or something. Did I do something wrong, and what is the point of Kubuntu if you can just get normal Ubuntu with the KDE package?

---

### Post by newuser111 on 2006-02-13
whats wrong with sudo -i

---

### Post by Robgould on 2006-02-13
kubuntu is "just ubuntu with the KDE package".  That is what it is and that is the whole point.  A large group of linux users prefer KDE to Gnme (ununtu default).

---

### Post by Adrian on 2006-02-13
I don't know why you couldn't set the root password. However, you don't have to do that. Try **sudo -s** instead of **su**.

[QUOTE=Tixer]...and what is the point of Kubuntu if you can just get normal Ubuntu with the KDE package?[/QUOTE]

This is because Ubuntu and Kubuntu are distributions supposed to fit on one CD. It's difficult to have both desktop environments on the same CD.

Next version of Ubuntu will probably include the KDE desktop (i.e. Kubuntu), because they will radically change the installer (and combine it with the live CD).

---

### Post by Tixer on 2006-02-13
I tried everything, and I cant get it to work. I tried the thingy in the thread, and that didnt work, so should I just abandon hope and use normal GNOME, or will I have this problem with Ubuntu again.

Never tried GNOME, KDE just appealed to me because of the eye candy.

---

### Post by Adrian on 2006-02-13
[QUOTE=Tixer]I tried everything, and I cant get it to work. I tried the thingy in the thread, and that didnt work, so should I just abandon hope and use normal GNOME, or will I have this problem with Ubuntu again.

Never tried GNOME, KDE just appealed to me because of the eye candy.[/QUOTE]

Try upgrading to KDE 3.5.1. Here is a thread about that:
[http://www.ubuntuforums.org/showthread.php?t=126113](http://www.ubuntuforums.org/showthread.php?t=126113)

---

### Post by Tixer on 2006-02-13
I dont have internet on the build with Ubuntu on it.

---

### Post by Adrian on 2006-02-13
[QUOTE=Tixer]I dont have internet on the build with Ubuntu on it.[/QUOTE]

Apparently admin mode is buggy in Kubuntu Breezy. However, there must be simple workarounds for your problem. Are you trying to setup a network?

Maybe renaming the thread to something more KDE-specific will attract more experienced KDE people (the topic gives you the impression that the problem is desktop-independent)? I doubt that **su** is your solution, anyway...

---

### Post by Tixer on 2006-02-13
I am simply trying to get on the internet. I will probably just abandon it for GNOME, as I have never tried it, and it may be a fun experience.

---

### Post by Adrian on 2006-02-13
[QUOTE=Tixer]I am simply trying to get on the internet. I will probably just abandon it for GNOME, as I have never tried it, and it may be a fun experience.[/QUOTE]

If you think it's fun, then go for it :)

You can then easily install KDE in Ubuntu when everything is working, by installing the **kubuntu-desktop** package (and then upgrade to KDE 3.5.1 afterwards :) )

A lot of people are having both Gnome and KDE installed at the same time.

---


---
title: "Installing KDE into Ubuntu 7.04"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-05-04
I am running Ubuntu 7.04 with the Gnome Desktop, but was thinking about trying the KDE Desktop. Am I able to install it or do I need to download it with another distribution. Will I lose the my data, or is it possible to have KDE and Gnome on the same computer and switch between them, similar to the dual boot between Windows and Linux?:confused:

---

### Post by bobplano on 2007-05-04
yep you can have KDE and GNOME.```
sudo aptitude install kubuntu-desktop
```
for all the kde apps or ```
sudo aptitude install kde-core
```
for just the kde look. then when it asks you to login go to options session and choose kde or gnome

---

### Post by Bachstelze on 2007-05-04
Just as a side note, *kubuntu-dektop* will install all the Kubuntu apps, not all the KDE apps (and will also install a few non-KDE apps). To install all the KDE apps, install *kde*.

Kubuntu is not KDE.

---

### Post by Wake Rider on 2007-05-04
OK I don't want Kubuntu... I want to stay with Ubuntu and be able to use both Gnome and KDE desktops. I tried the code but it failed as it couldn't get all the files. Why does the error 'Connection Reset by Peer' keep coming up? what does it mean? How can I get the necessary packages installed for KDE without it failing because of this error?

---

### Post by Bachstelze on 2007-05-04
Means you seems to have an instable Net connection, is it working fine otherwise ?

---

### Post by hyperair on 2007-05-04
I get that for certain packages in the Taiwan Ubuntu server ([http://tw.archive.ubuntu.com)](http://tw.archive.ubuntu.com)). When that happens I just wait until the problem goes away, or I change my repository to use the main server ([http://archive.ubuntu.com](http://archive.ubuntu.com))

---

### Post by Wake Rider on 2007-05-04
I installed the KDE core and it came up on the startup screen but as soon as I logged in my desktop came up exactly as it had been under Gnome! What am I doing wrong / not doing??:confused:

---

### Post by Wake Rider on 2007-05-04
> **hyperair said:**
> I get that for certain packages in the Taiwan Ubuntu server ([http://tw.archive.ubuntu.com)](http://tw.archive.ubuntu.com)). When that happens I just wait until the problem goes away, or I change my repository to use the main server ([http://archive.ubuntu.com](http://archive.ubuntu.com))

How do you change the repository server? BTW I am in New Zealand

---

### Post by hyperair on 2007-05-04
[quote=Wake Rider]How do you change the repository server? BTW I am in New Zealand[/quote]
Click on System->Administration->Software Sources. It's in there.

[quote=Wake Rider]I installed the KDE core and it came up on the startup screen but as soon as I logged in my desktop came up exactly as it had been under Gnome! What am I doing wrong / not doing??[/quote]
At your login screen, press F10 to select your session, and select KDE instead of Default Session or GNOME.

Then log in normally.

---

### Post by teddybairs1 on 2007-05-04
Wake Rider, install the kubuntu-desktop package. It is KDE it just does a few things differently from the straight KDE package. As far as your booting back into Gnome; go back to your login screen. click on "sessions". There should be a line which says "change session" or something to that effect. It should give you a list of options. Click "KDE". Login as usual.

---


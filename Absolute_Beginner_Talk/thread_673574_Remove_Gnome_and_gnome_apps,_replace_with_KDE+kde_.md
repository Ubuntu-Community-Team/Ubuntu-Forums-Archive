---
title: "Remove Gnome and gnome apps, replace with KDE+kde apps"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2008-01-20
Is this possible? i would like to remove everything gnome related, and replace with the KDE DE, but have the included kde apps etc, preferably KDE4 stable, i tried installing KDE4(via ubuntugeek guide) but the KDE DE had no apps! and gnome session got all mixed up with kde apps as well, so yeah just wondering if possible

i was thinking sudo apt-get install kubuntu-desktop, but then i want to remove gnome completely, and sudo apt-get remove ubuntu-desktop doesnt work cause apparently its not installed, however im using it lol?

---

### Post by cybertron3000 on 2008-01-20
This is a really good Q - wish I knew but I'm on week one of my Ubuntu experience (which is great).  I'd like to know how too...:confused:

---

### Post by JoshuaRL on 2008-01-20
Well, the easy way won't give you KDE4, but it will be stable.

```

sudo apt-get install kubuntu-desktop

```

That will give you the KDE desktop and all the apps that comes with it.  It's a metapackage, so it will download a lot others.  This will take a while.

Also, I found this if you just want KDE4 Stable:

[http://www.ubuntugeek.com/howto-install-kde-40-stable-in-ubuntu-gutsy.html](http://www.ubuntugeek.com/howto-install-kde-40-stable-in-ubuntu-gutsy.html)

---

### Post by rosegarden78 on 2008-01-20
United we stand divided we fall.  First install Ubuntu then add the KDE and XFCE packages.  On login select XFCE session at Startup right click mouse select Settings - Autostarted Programs & add new item and type "nautilus" - if you don't like what you see switch back to GNOME or KDE session.

---

### Post by dynamethod on 2008-01-20
Yeah going to install the kubuntu-desktop, but after doing so, if i uninstall the ubuntu-desktop(gnome i take it?) will that rid all the gnome apps so i got a pure KDE DE?, i dont have much diskspace and only want KDE, not gnome

---

### Post by dynamethod on 2008-01-20
I was going to reinstall with Kubuntu 7.10 but omfg wireless support is absolutly shocking for kubuntu, doesnt even pick up the WEP network lmao!

---

### Post by JoshuaRL on 2008-01-20
Yeah I believe that will.  However, you may loose support for Gnome apps so be careful.  What kind of disk space are we talking about?

---

### Post by dynamethod on 2008-01-20
about 30 gigs, but 6 gigs used up atm, so about 24 gigs left (im a poor student dont laugh)

---

### Post by JoshuaRL on 2008-01-20
Nah, that's only about 10gb less than I have on my biggest laptop.

Honestly, you should probably just keep Gnome.  That way you'll be more likely to have support for Gnome apps, like the wireless ones.

---

### Post by dynamethod on 2008-01-20
Yeah true, sad really cause KDE4 looks soo sexy

---

### Post by JoshuaRL on 2008-01-20
No, I mean you can have your Kake and eat it too (I just made that up :p)  Do what you were going to, but then just leave ubuntu-desktop on.  That way you keep that functionality.

---

### Post by GavinZac on 2008-01-20
If you really want to, the quickest way would be to install ubuntu-desktop so you have the full set of gnome apps with one package, then uninstall it again, to remove them all, then install kde-desktop.

alternatively, install kubuntu

---

### Post by rosegarden78 on 2008-01-20
A clean install of Xubuntu 7.10 should do the trick.  Then at the terminal type:

sudo aptitude install nautilus

Then you train your furry friend by installing your required programs.

Right click the mouse and select Settings - Autostarted Programs and add nautilus
Right click your launcher and add XFCE Menu.
Press Ctrl + Alt + Backspace to logout X server
Log back in to X server

You should be running Nautilus on XFCE with a custom launcher.
Now sudo aptitude your other required programs.
Maybe install some .deb packages

Click Xfce Menu - Settings - Sessions and Startup to enable GNOME and KDE support.

---

### Post by JoshuaRL on 2008-01-20
I think he wants KDE.  So it would be your "geary friend"?

---

### Post by dynamethod on 2008-01-20
> **GavinZac said:**
> If you really want to, the quickest way would be to install ubuntu-desktop so you have the full set of gnome apps with one package, then uninstall it again, to remove them all, then install kde-desktop.

alternatively, install kubuntu

Yeah thats the thing, im on a wireless network, and kubuntu live cd just doesnt pick up the network(i tried Wep 64bit still didnt work and i cant turn encryption off for 2 seconds or i end up with a massive bill) kubuntu wireless support = no good

---

### Post by rosegarden78 on 2008-01-22
Nice one!  Yes kde with xfce together make a furry gearhead.  I just use all three login with Xfce and run Nautilus.

EDIT:  Update I use Ubuntu GG with Compiz and Avant window manager on an Xfce desktop.

---

### Post by thelatinist on 2008-01-22
Removing ubuntu-desktop will *not* remove your Gnome apps.  Ubuntu-desktop is an empty package that makes all the default Ubuntu apps dependencies.  Therefore installing it causes the installation of all those dependencies, but uninstalling it will *not* remove them.

You will have to uninstall all the Gnome apps you don't want manually using your favorite package manager.  You can, I am sure, find a list of packages included in Ubuntu that aren't included in Kubuntu to use as a guide.

---

### Post by JoshuaRL on 2008-01-23
Oh, he's right.  Now that I hear the truth I recognise it.  You would go to ubuntupackages.com and look for ubuntu-desktop.  It will have a list of all the apps.

---


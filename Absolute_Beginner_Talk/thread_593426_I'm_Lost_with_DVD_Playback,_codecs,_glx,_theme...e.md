---
title: "I'm Lost with DVD Playback, codecs, glx, theme...etc"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by andaman on 2007-10-27
Hello, 


I"m brand new to Ubuntu 7.04.  Please help, and thank YOU ahead of time.

1. Cant play DVD.  i found a million links to have it work, but it seems not to work.  

2. What's Beryl, Gnome, KDE...etc? what do i need?

3. I cant even change theme.  how do it? i tried, but cant do it.

4. what's glx? do i need it? i have ATI.


Ok, i dont know how good or stable Ubuntu is, but i'm been trying to use it for a week now and it's really confusing to me.  the GUI here is very nice, but as far as user friendly...wow...SO FAR, comparing to windows, it's a lot more confusing. Please dont get me wrong, i'm new here, i'm willing to try and i just need a helping hand.

OOHH, when answering the questions above, please pretend that i just install a fresh copy of Ubuntu 7.04 with nothing yet, and let's start from there....


Thank you so much.

---

### Post by Qwerty_ on 2007-10-27
This should sort you out for playing restricted formats. I.e DVD's

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Before you start messing with any graphics settings you should install restricted drivers for your graphics card.

System>Administration>Restricted Drivers Manager.

---

### Post by Malta paul on 2007-10-27
Hi, You might like to check out:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Hope this helps you, :)

---

### Post by andaman on 2007-10-28
thanks you for the info links.


what about DVD playback? there are so many links out there, i know, and i've tried them but still cant get it to work.  please help.

---

### Post by derred on 2007-10-28
[http://www.medibuntu.org/](http://www.medibuntu.org/) is a source for non-free software
From the terminal do this:
```

sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install libdvdcss2 vlc mplayer w32codecs skype

```

this will add dvd playback(may be illegal in your country), 2 media players, non-free codecs (may be illegal in you country) and skype:)

---

### Post by Cato2 on 2007-10-28
For the playback of DVDs, and the various proprietary codecs needed for some multimedia (MP3 etc), just follow the instructions at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) - see the Ubuntu 7.04 section.

You should also run Restricted Drivers Manager from the System menu as well.

These two actions should sort out most of your issues.  To get themes configured, try the Ubuntu theme setup HOWTO at [http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

Hope that helps, comment here if you have problems!

---

### Post by Martje_001 on 2007-10-28
> **andaman said:**
> 1. Cant play DVD.  i found a million links to have it work, but it seems not to work.  

2. What's Beryl, Gnome, KDE...etc? what do i need?

3. I cant even change theme.  how do it? i tried, but cant do it.

4. what's glx? do i need it? i have ATI.
First: You should install gutsy, it's easier.

1. Just click an DVD, and ubuntu wil ask you to install the codecs.
2. Beryl does not exist anymore. It's now called Compiz Fusion. You should see [this]("http://youtube.com/watch?v=_ImW0-MgR8I"). Gnome is a Desktop Environment. Like [KDE]("http://members.home.nl/ralphm/screenshots-linuxpaginas/kde3-configuratiescherm1.jpg"), [xfce]("http://www.freesbie.org/share/1.1/manual/xfce.png"), [fluxbox]("http://damnsmalllinux.org/dsl-2.0RC2-fluxbox.jpg"). Etc. Just keep gnome. If you want to try kde install 'kubuntu-desktop' if you want to try xfce 'xfce-dektop'.
3. Go too [gnome-look.org]("http://www.gnome-look.org")
4. Glx is a method to render windows. If you use an ATI card you sould install the restricted drivers, and then install xserver-glx.

---

### Post by andaman on 2007-10-29
thank you,

let me try all that and we'll see.


but please, keep the help coming. i need all the help i can get. thank you

---

### Post by stchman on 2007-10-29
> **andaman said:**
> Hello, 


I"m brand new to Ubuntu 7.04.  Please help, and thank YOU ahead of time.

1. Cant play DVD.  i found a million links to have it work, but it seems not to work.  

2. What's Beryl, Gnome, KDE...etc? what do i need?

3. I cant even change theme.  how do it? i tried, but cant do it.

4. what's glx? do i need it? i have ATI.


Ok, i dont know how good or stable Ubuntu is, but i'm been trying to use it for a week now and it's really confusing to me.  the GUI here is very nice, but as far as user friendly...wow...SO FAR, comparing to windows, it's a lot more confusing. Please dont get me wrong, i'm new here, i'm willing to try and i just need a helping hand.

OOHH, when answering the questions above, please pretend that i just install a fresh copy of Ubuntu 7.04 with nothing yet, and let's start from there....


Thank you so much.

1. To play DVDs follow my tutorial.  [http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

2.  Gnome is the GUI for Ubuntu, KDE is the GUI for Kubuntu. Beryl or now known as compiz is a eye candy interface for Gnome.

3.  TO change themes go to System--->Preferences--->Theme and select a theme.

4.  GLX is openGL for X-windows.  fglrx is the restricted driver for ATI cards that you will need to enable glx.

Ubuntu Linux is not harder than Windows, just different.

---


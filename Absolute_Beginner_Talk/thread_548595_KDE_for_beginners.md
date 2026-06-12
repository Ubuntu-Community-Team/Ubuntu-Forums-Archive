---
title: "KDE for beginners"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by gt49ers on 2007-09-11
I would like to use the KDE desktop
so were do I need to go to get the software and what do I need to do once I have it
I am a newbie with Linux so be kind
:confused:

---

### Post by Eriksmits596 on 2007-09-11
You can download it from [www.kde.org]("www.kde.org").

---

### Post by Terl on 2007-09-11
> **gt49ers said:**
> I would like to use the KDE desktop
so were do I need to go to get the software and what do I need to do once I have it
I am a newbie with Linux so be kind
:confused:

You can get this all set up through synaptic.  There is a meta package for kde.  This would be the easiest way for you to get it.

If you have not installed anything at all yet (I noticed you have one post) you could alwas install Kubuntu which is Ubuntu already setup with kde for you.

---

### Post by forestpixie on 2007-09-11
have a look at [psychocats]("http://www.psychocats.net/ubuntu/index") - I use aptitude to get other desktops

```
sudo aptitude install kubuntu-desktop
```

---

### Post by gt49ers on 2007-09-11
OK, KDE.org is good,,
this sounds like a full feature version
is it something that is easy to install
:)

What is the Kubuntu ?
I looked in add/remove applications and saw nothing listed for that
were do I go, what do I do

:confused::confused:

---

### Post by LaRoza on 2007-09-11
> **gt49ers said:**
> 
What is the Kubuntu ?
I looked in add/remove applications and saw nothing listed for that
were do I go, what do I do


Kubuntu is just Ubuntu with different packages and uses KDE.

Type this command in the terminal:

```

sudo aptitude install kde-core

```
(or the above command, this one is smaller and size)

---

### Post by LowSky on 2007-09-11
click below to download the live cd version of kubuntu, all you need to do is pt it on a cd

[http://kubuntu.org/download.php#latest]("http://kubuntu.org/download.php#latest")

---

### Post by LaRoza on 2007-09-11
> **LowSky said:**
> click below to download the live cd version of kubuntu, all you need to do is pt it on a cd


If you already are using Ubuntu, just install KDE to your existing OS, using the commands above.

It is not necessary to get another OS for this. If you don't want KDE on Ubuntu, you can easily remove it.

---

### Post by Nythain on 2007-09-11
if you are this new to linux, i would have to suggest at this point in time to download the kubuntu cd and install kubuntu... kubuntu is basically ubuntu with kde as its desktop (and thus a bunch of kde apps instead of gtk/gnome apps) instead of Gnome.

If you already have ubuntu installed and dont want to reformat your system, then typing
```

sudo aptitude install kubuntu-desktop

```
in a terminal will install kde and the kde apps that get installed with kubuntu

once you get more familiar with ubuntu/linux you could go for a much cleaner install as outlined in a few different guides, wich consists of installing a command line system, then installing kde-base and the necessary packages you want/need (Note: This is a much more advanced approach and i would like to RE-suggest just installing kubuntu)

either way, i hope you figure it all out and enjoy your ubuntu/linux experience :)

---

### Post by gt49ers on 2007-09-12
I did the 'install Kubuntu-Desktop'
I selected KDE as default
When the login appeared it was in blue which I presume is the default KDE graphics
But when the Desktop appears I back in GNOME

What may I have done wrong to cause this ?
How can I correct this?

Also the options on the shutdown list has changed.. there isnt any poweroff option
just suspend and hibernate

All help is much appreciated

:)

---

### Post by jw5801 on 2007-09-12
When you get to the login screen there should be a button somewhere that will open up a "Sessions" dialogue, and you should be able to pick KDE from the list!

---

### Post by pilli on 2007-09-12
The button is options on the log-in screen.  Click on that and you can choose sessions and then from the list pick KDE.

---

### Post by gt49ers on 2007-09-12
I have KDE on Desktop

Thanks for all the help

---

### Post by jordanmthomas on 2007-09-12
Also, the reason you had lost your shutdown buttons in gnome while running the KDE login manager is that gnome uses gdm's raised privileges to reboot or shut down.  It can't get these privileges from kdm because it doesn't know how.

You'd get the same sort of result if you ran kde from the gnome login manager.

Hope that clarifies things for you.

---

### Post by gt49ers on 2007-09-27
I installed Ubuntu on another pc, got network and printing working
I went to install Kubuntu-desktop using the command
'sudo aptitude install kubuntu-desktop' and I get an line stating that it couldn't find any package that matched 'kubuntu-desktop'
I have the install CD in the drive

Any help is appreciated

:confused:

---

### Post by gt49ers on 2007-09-27
I install Ubuntu on another pc, network and printing is working
I went to install Kubuntu with the command line:
'sudo aptitude install kubuntu-desktop' and I got a line stating that it couldn't find any package by that name or description.
I have the install CD in the drive.

any suggestions on why it can't find the kubuntu package?

---

### Post by stevebakerj on 2007-09-27
> **gt49ers said:**
> I install Ubuntu on another pc, network and printing is working
I went to install Kubuntu with the command line:
'sudo aptitude install kubuntu-desktop' and I got a line stating that it couldn't find any package by that name or description.
I have the install CD in the drive.

any suggestions on why it can't find the kubuntu package?

Installing the Kubuntu desktop on top of the Ubuntu Desktop will cause you a lot of confusion as you will have multiple Ubuntu and Kubuntu entries in your menus. The download will also be approx 250Mb. If you just want the KDE way of doing things install kde-core

```
sudo apt-get install kde-core
```

Personally I would Download the latest Kubuntu iso:

[http://www.kubuntu.org/download.php#latest](http://www.kubuntu.org/download.php#latest)

Then install Kubuntu with separate / (root) and /home directory's and start afresh, then when 7.10 (Gutsy) goes final in October the upgrade path will be much easier.

IMHO of course

---


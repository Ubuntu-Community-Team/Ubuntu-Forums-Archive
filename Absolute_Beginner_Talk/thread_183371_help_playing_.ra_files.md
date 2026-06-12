---
title: "help playing .ra files"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-05-27
Hi, i recently downloaded the audio recording of [*The Cathedral and the Bazaar*]("http://www.catb.org/~esr/writings/cathedral-bazaar/")  (which can be downloaded [here]("http://www.catb.org/~esr/writings/cathedral-bazaar/linux1.d50.ra")) and i'm wondering what player or codec is needed to  play this file or other .ra files. so far I've tried aramoK, Kaffine, mplayer, vlc movie player, totem movie player, and rythembox. do i need a certain codec or and different player to play these type of files.

thanks,
cptjaben

---

### Post by adamkane on 2006-05-27
Are you using dapper or breezy?

This is either a poorly encoded file or it was encoded with advanced features. 

On breezy, I was only able to play the file with realplayer and xine.

I was also able to play it with amarok (amarok-xine):
[http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10]("http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10")

```

sudo gedit /etc/apt/sources.list

``` 
Add this line to the file:

> 
deb [http://archive.czessi.net/ubuntu]("http://archive.czessi.net/ubuntu") breezy main universe
 

Save and close the file. Continue:

```

cd ~/Desktop
wget http://www.czessi.net/kczessi.gpg
sudo apt-key add kczessi.gpg
sudo apt-get update 

``` 

If amarok is already installed:

```

sudo apt-get dist-upgrade

``` 
  
If amarok isn't already installed:

```

sudo apt-get dist-upgrade[FONT=monospace]
[/FONT]sudo apt-get install amarok amarok-xine

``` 

Be aware that amarok-gstreamer is not available for amarok 1.4. You will be using amarok-xine.

---

### Post by cptjaben on 2006-05-28
i''m currently running breezy with gnome, can i run aramok-xine in gnome or do i need kubuntu? sorry i'm still quite new to ubuntu as well as linux.

Thanks,
cptjaben

---

### Post by mostwanted on 2006-05-28
Yes you can. KDE apps can run in Gnome, Gnome apps in KDE. They just look like shit.

---


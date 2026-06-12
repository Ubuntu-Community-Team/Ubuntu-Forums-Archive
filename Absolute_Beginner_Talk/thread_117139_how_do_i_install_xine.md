---
title: "how do i install xine"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by mike63730 on 2006-01-14
hello i am new to ubuntu i am a former windows man till gates the devil started acting like he wants to take over the world (LOL) but anyway my question is how do i install xine i downloaded it and cant get it to do anything by clicking on install am i going about this the wrong way i am a tech on computers but i have always worked with windows till now i need to learn this stuff because i am going to start trying tw posts  	More than 15 replies or 150 viewso get all my customers to use the linux world too (the gatester is rich enough i think) any help is apreciated
thanks 
jim

---

### Post by 23meg on 2006-01-14
Type```
sudo apt-get install gxine
```to install gxine, a GTK frontend to xine, and/or ```
sudo apt-get install totem-xine
```to install the xine backend for the Totem movie player.

---

### Post by mike63730 on 2006-01-14
i teied that this is what i got 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gxineReading package lists... Done
Building dependency tree... Done
E: Couldn't find package gxine

---

### Post by 23meg on 2006-01-14
You'll need to [enable the Universe repository]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse") if you haven't.

---

### Post by Perfect Storm on 2006-01-14
You don't need to download it you can use the install program like apt-get. But first you need to setup yoour sourcelist for apt-get.
Open the terminal (application tab ---> accessories ---> terminal) and write:

```
sudo gedit /etc/apt/sources.list
```

erease all of it and add this instead:

> 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

save it.

Now back to the terminal

```

sudo apt-get update
sudo apt-get install xine-ui

```

Now to make xine play your media files when you click them:

```
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
killall gnome-panel
killall nautilus

```

Edit: ops...to slow lol

---

### Post by mike63730 on 2006-01-14
thanks that worked your a life saver worked great but thats a lot to remember to type in but i will ask for help on these issues till i getthe hang of it 
thanks a million 
jim

---


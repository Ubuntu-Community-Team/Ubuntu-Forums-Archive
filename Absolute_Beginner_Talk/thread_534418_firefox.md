---
title: "firefox"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2007-08-25
hi everyone
i am running ubuntu 7.04. i am not having any success running firefox at all.  i have tried uninstalling it using the synaptic manager; reinstalling it using the add/remve applications manager but to no avail. any suggestions? i am currently using opera but i prefer firefox.

---

### Post by Patrick793 on 2007-08-25
> **deepblue80 said:**
> hi everyone
i am running ubuntu 7.04. i am not having any success running firefox at all.  i have tried uninstalling it using the synaptic manager; reinstalling it using the add/remve applications manager but to no avail. any suggestions? i am currently using opera but i prefer firefox.

What exactly isn't working?

---

### Post by cypry on 2007-08-25
What happends when you type firefox in terminal?

---

### Post by deepblue80 on 2007-08-25
> **Patrick793 said:**
> What exactly isn't working?

when i click firefox icon it does not launch. it shows a window at the bottom of the screen and then dies i.e. just disappears. 

> **cypry said:**
> What happends when you type firefox in terminal?
this is what i get back in the terminal 

deep@deep-desktop:~$ terminal
bash: terminal: command not found
deep@deep-desktop:~$

---

### Post by forestpixie on 2007-08-25
type firefox into the terminal not terminal :)

---

### Post by Patrick793 on 2007-08-25
Try downloading the latest firefox from the [firefox website]("http://www.mozilla.com/en-US/firefox/"). That may work.

---

### Post by deepblue80 on 2007-08-25
> **mswillwin said:**
> You will always trouble with Mozilla Fire Fox on this SHITTY UNSECURE and UNSTABLE SYSTEM

Bill Gates and Steve Ballmer will own Liinux

BG

BG, mate i am really not in mood for any windows sell here. the more learning i do with Ubuntu/linux the more i hate MS. do everyone a favor and keep quiet.

---

### Post by deepblue80 on 2007-08-25
> **forestpixie said:**
> type firefox into the terminal not terminal :)

My mistake sorry. the terminal shows the following!

deep@deep-desktop:~$ firefox
Segmentation fault (core dumped)
deep@deep-desktop:~$ 


i did uninstall firefox and its supported applications using the add/remove applications tool - does this have anything to do with that?

---

### Post by alienexplorers on 2007-08-25
Go to the Mozilla website at;
> [http://www.mozillazine.org/](http://www.mozillazine.org/)
At the top of the page is a link to Firefox 2.0.0.6
Click on the link and look for the Linux sub-directory.
Download the tar.gz file
Move it to your home directory and un tar it using:
> tar -xvzf filename.tar.gz
Create a shortcut to The new file in the firefox directory and you should be running firefox,

---

### Post by deepblue80 on 2007-08-25
> **alienexplorers said:**
> Go to the Mozilla website at;

At the top of the page is a link to Firefox 2.0.0.6
Click on the link and look for the Linux sub-directory.
Download the tar.gz file
Move it to your home directory and un tar it using:

Create a shortcut to The new file in the firefox directory and you should be running firefox,

i extracted the tar.gz file to the desktop and i can run firefox by creating a new application launcher i.e. a new short cut to a file called 'Firefox' in the extracted folder. but the  firefox launcher in the applications/internet menu does not work? also if i delete the firefox folder from desktop the short cuts dont work - this is understandable but how do i install using the normal process i.e. where all the shortcuts are created for me and i dont have to  create anything myself? i av the firefox extracted file on desktop any commands available to install this package thru the terminal?

---

### Post by kerry_s on 2007-08-25
i'll try and talk you through it.
run these commands in terminal, copy & paste if you want get it right

sudo rm -rf /usr/lib/firefox
sudo rm /usr/bin/firefox
sudo cp ~/Desktop/firefox /usr/lib/firefox
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox
sudo rm -rf /usr/lib/firefox/plugins
sudo cp /usr/lib/mozilla/plugins /usr/lib/firefox/plugins

that should do it.

---

### Post by deepblue80 on 2007-08-25
> **kerry_s said:**
> i'll try and talk you through it.
run these commands in terminal, copy & paste if you want get it right

sudo rm -rf /usr/lib/firefox
sudo rm /usr/bin/firefox
sudo cp ~/Desktop/firefox /usr/lib/firefox
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox
sudo rm -rf /usr/lib/firefox/plugins
sudo cp /usr/lib/mozilla/plugins /usr/lib/firefox/plugins

that should do it.

thanks for the help! its up and running now!!

---


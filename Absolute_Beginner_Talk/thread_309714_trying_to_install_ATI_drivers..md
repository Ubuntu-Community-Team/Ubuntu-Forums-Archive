---
title: "trying to install ATI drivers."
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by lex on 2006-11-30
I'm following a how to, but I'm stuck at the start. I don't know how to do this, "change to the download directory, [COLOR=Red]and[/COLOR] Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list"
Can someone please help?
Thanks in advance.
Lex

---

### Post by nite owl on 2006-11-30
Hi go to sources.list and uncomment everything that has the repositories urls in them......that means delete the '#' in front of them.

---

### Post by nite owl on 2006-11-30
Oh and you'll probably need root to do this or you wont be able to save what you've done. Go to your command line and type the command *sudo chmod 777 /etc/apt/sources.list*.....Then youll be prompted for your pass, enter it. Then continue to save the file

---

### Post by lex on 2006-11-30
Thanks for your assistance nite owl, but i dont know where the sources.list is.

---

### Post by nite owl on 2006-11-30
Ok from the desktop go to Places ---> *Computer* ---> *Filesystem* ---> *etc* ---> *apt* --> and in apt there should be a file sources.list    .........However make sure you change the permissions first or it wont save 'sudo etc....'

---

### Post by RMorris78 on 2006-11-30
or in Synaptic > View > Manage Repositories

Thats graphical with a right click menu to disable/enable lines, a little bit easier if your new with it

Thats how it is in Adept in Kubuntu, i'd assume its similar in gnome

---

### Post by r4ik on 2006-11-30
For youre sources list, 

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

    * Save the edited file 

sudo apt-get update

and the file location  cd ~/where the file is.
(if i remember correctly)

Good luck !

---

### Post by lex on 2006-11-30
Thanks r4ik, i did as you suggested and will try again.
Also thanks, RMorris 78R and nite owl, for your advice.
Much appreciated.

---

### Post by Trance Gemini on 2006-11-30
or just read [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories") guide about adding extra repos, and you can peek [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") to get some answers to install ATI drivers :)

---


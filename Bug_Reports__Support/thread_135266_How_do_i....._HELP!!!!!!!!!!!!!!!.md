---
title: "How do i..... HELP!!!!!!!!!!!!!!!"
date: 2006-02-23
forum: Bug Reports / Support
---

### Post by msg plus freak on 2006-02-23
Hiya all,
How do i install stuff on linux ubuntu 5.04? Like firefox and stufff...
Many regards,
Nathan

---

### Post by knalle on 2006-02-23
[QUOTE=msg plus freak]Hiya all,
How do i install stuff on linux ubuntu 5.04? Like firefox and stufff...
Many regards,
Nathan[/QUOTE]

in the system menu look for a program called "package manager" or open a **terminal** and write

**sudo apt-get install firefox andstuff**

---

### Post by msg plus freak on 2006-02-23
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
I get that,
I also have a a broken file in package manager:
ZENITY:
Display graphical dialog boxes from shell scripts
Zenity allows you to display GTK+ dialogs from shell scripts; it is a
rewrite of the `gdialog' command from GNOME 1.

Zenity includes a gdialog wrapper script so that it can be used with
legacy scripts.

IS BROKEN
thanks

---

### Post by dbw on 2006-02-23
msg_plus_freak - it sounds like you are not running your package manager as root.  Alternatively, it is possible that you have multiple package managing apps open.  Close all of your install-type applications.  If you do npt know which these are, then just close out everything.  Now:
in a terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```

 -or-

open system>administrator>synaptic
 reload
 search for firefox
 click the box at left of firefox
 apply

if you cannot find synaptic, run gksudo synaptic in a terminal

good luck

---

### Post by msg plus freak on 2006-02-24
[QUOTE=dbw]msg_plus_freak - it sounds like you are not running your package manager as root.  Alternatively, it is possible that you have multiple package managing apps open.  Close all of your install-type applications.  If you do npt know which these are, then just close out everything.  Now:
in a terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```

 -or-

open system>administrator>synaptic
 reload
 search for firefox
 click the box at left of firefox
 apply

if you cannot find synaptic, run gksudo synaptic in a terminal

good luck[/QUOTE]
it comes up couldtnt find file firefox :@
Help please thanks

---

### Post by hegenious on 2006-02-24
probably you need to add extra repositories to your sources.list file.

update your /etc/sources.list to include universe and multiverse repositories.
after that:

sudo apt-get update
sudo apt-get install firefox

should work.
for info on how to update your 5.04 sources.list, and lots more, please follow this link: [http://ubuntuguide.org/](http://ubuntuguide.org/) 

hth

---

### Post by msg plus freak on 2006-02-24
How would I update them?

---

### Post by msg plus freak on 2006-02-24
oh sorry yes there,
But i still cant do it.
It says no such thing when i type in /etc/sources.list:@

---

### Post by hegenious on 2006-02-24
re-read my previous post, I edited it.

basically it is done by opening /etc/sources.list

code: 
sudo gedit /etc/apt/sources.list 

uncomment (remove the#) the entries for universe and multiverse.
save and close.

now in a terminal run: sudo apt-get update
that will update your package manager and from now on it will include the extra repositories in its search for software.

alternatively, I recommend you check out automatix, it's on the ubuntu forums.
with that you can install all kind of apps including firefox, java, codecs etc.
make sure to use the one for ubuntu 5.04 as that is what you are running.

---

### Post by msg plus freak on 2006-02-24
Ive tried using automatix it wouldnt let me install it

---

### Post by msg plus freak on 2006-02-24
E: Couldn't find package firefox
Is exactly what it comes up

---

### Post by hegenious on 2006-02-24
well forget about automatix then and check out [http://ubuntuguide.org/](http://ubuntuguide.org/)

your questions have probably been asked a million times by others and that's why people went trough the trouble of collecting all these issues and solutions and made it into a nice webpage that offers a lot of answers in just one place.

under TOPICS check out the third one.

edit: stupid me. its's /etc/apt/sources.list    I forgot to mention the apt subdirectory

---


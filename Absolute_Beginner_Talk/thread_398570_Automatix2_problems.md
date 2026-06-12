---
title: "Automatix2 problems"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-04-01
Hi
I´m having lots of update problems with automatix2 at the moment. When using sudo aptitude update the terminal is advising not to install untrusted updates, apparently a problem with the keys.

My question is, if i un-install automatix will i also un-install the drivers too? and what is the best way to do it?

Thanks in advance

Davesmith

---

### Post by STREETURCHINE on 2007-04-01
you will always get that warning with 3rd party repo's.it is not really any thing to worry about,i dont want to start a war here but there is nothing wrong with automatix2,or easy ubuntu for that matter ,they are usefull tools,

so it is not an automatix problem as the same warning comes with all third party  repositories or programs.

dont panic you have loaded automatix so trust it and install what you need.

my opinion..

if you wish to uninstall i think there is a method listed on the automatix site,sorry i dont have a link at the moment

---

### Post by Dayylin on 2007-04-01
You can remove automatix by the following:

sudo apt-get remove automatix2

---

### Post by davesmith on 2007-04-01
Thanks.

will sudo apt-get remove automatix2 also remove the drivers that came with it?

---

### Post by STREETURCHINE on 2007-04-01
the reason for the recent warnings is the gpg key has been changed ,it can be solved if you wish to keep it installed 

```
The Automatix GPG key has changed starting 03/15/2007 which will result in update-manager reporting "unverified updates" from the automatix repository. Please ignore this error and go ahead and upgrade automatix2 (It's a perfectly safe operation).

Method 1:
After upgrading to the latest version, run Automatix2, close it and then run the following command from terminal:
CODE
sudo apt-get update

It will import the new GPG key from getautomatix.com and this will fix the Automatix GPG verification error for all future updates from apt, synaptic and update-manager.

Method 2:
If you want to rectify the situation immediately, you can do the following from terminal (one after the other, hitting enter after each step):
CODE
wget http://www.getautomatix.com/keys/automatix2.key

CODE
gpg --import automatix2.key

CODE
gpg --export --armor E23C5FC3 | sudo apt-key add -

CODE
sudo apt-get update
```,

or just uninstall it  with

      ```
sudo apt-get remove automatix2
```

as to all the drivers i would say they would stay installed,just dont quote me on that,,:lolflag:

---

### Post by davesmith on 2007-04-01
sorry i mean drivers and codecs

---

### Post by davesmith on 2007-04-01
Anyway, importing the new key has worked, so un-install is uneccessary.
Many thanks Streeturchine!

---


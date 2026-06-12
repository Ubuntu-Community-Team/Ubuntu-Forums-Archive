---
title: "Gutsy (7.10) upgrade messed up"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by saltbar on 2007-10-25
Hi all

Last nite, I started the upgrade for my OS to go from Feisty to Gutsy. This morning, it was still half way as it want me to hit return on something before moving on. 

WHile getting ready for work, to my horror, my wife sat down and "Switch User" which went to splash login page but keep getting a pop up box saying "Authenthication is incorrect" with a single 'OK' button. I kept pressing it but nothing is happening as the pop up box keep returning. I could see behind it that the login accounts are not visible anymore on the login screen. 

I did a reboot cos I wasn't getting anywhere and now Ubuntu won't load - can't get past the GRUB stage. I don't know what I should do at the moment - reinstall Feisty or make a Live CD for Gutsy? Will all the personal settings and files be lost? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

Look forward to your comments.

---

### Post by darren1270 on 2007-10-25
The first thing I would do is..... Use a live cd and try to move any important data to a safe place..... 

I guess the first question I should ask you is .... did you backup before attempting the upgrade????

If you did I would just create a new Gutsy Cd and start from scratch....

Just my two cents worth....

Good Luck

Darren

---

### Post by Archmage on 2007-10-25
CTRL+ALT+F1

Enter there your username and password

Enter the following (you need to enter the root-password / the password of the first user).

```
sudo aptitude update ; sudo aptitude upgrade ; sudo aptitude dist-upgrade 
```

It should download/update the things you need. Maybe you need to repeat this, but at the end you should arrive at Gusty.

---

### Post by saltbar on 2007-10-25
I only switched to Ubuntu several months ago so we didn't have an terrible amount of data on the HD as backed up before the switch, and since then worked mainly from memory stick/Google Docs/Flickr/Picnik. but there are something we would like to recover from HD i.e. photos and recent job app forms. Whereas these would normally be under 'Home', using LIve CD (Feisty) for recovery, I couldn't locate them again. I have tried 'Search for Files' option.

OK, I'd best to make a Gusty Live. Advice for above greatly appreciated. 

Thanks

---

### Post by saltbar on 2007-10-25
@Archmage: where do I use that Ctrl-Alt-F1? Working from LIVE CD (Feisty)?

---


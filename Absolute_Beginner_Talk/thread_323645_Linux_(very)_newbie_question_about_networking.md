---
title: "Linux (very) newbie question about networking"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by tonynz on 2006-12-22
I've installed Ubuntu Linux dual-booting with WIN XP on a spare machine. So far, so hoopy. The machine is networked, and I can see and access the other machines on the network fine - they are all XP beasts. My problem is access the other way round. I have the Linux machine set to the correct workgroup by editing Samba.conf, so the other PCs can see it, but if I try to access the Linux PC from another machine, I get asked for a login and password, and whatever I supply does not seem to be accepted - it just re-displays the login request.

I presume there is something else I have to configure on the Linux PC - But what, I have no idea. Any suggestions?

This is absolutely my first foray into Linux, so please make all responses in words of one syllable, and a minimum of Linux geek-speak.:) :)

---

### Post by dannyboy79 on 2006-12-22
> **tonynz said:**
> I've installed Ubuntu Linux dual-booting with WIN XP on a spare machine. So far, so hoopy. The machine is networked, and I can see and access the other machines on the network fine - they are all XP beasts. My problem is access the other way round. I have the Linux machine set to the correct workgroup by editing Samba.conf, so the other PCs can see it, but if I try to access the Linux PC from another machine, I get asked for a login and password, and whatever I supply does not seem to be accepted - it just re-displays the login request.

I presume there is something else I have to configure on the Linux PC - But what, I have no idea. Any suggestions?

This is absolutely my first foray into Linux, so please make all responses in words of one syllable, and a minimum of Linux geek-speak.:) :)

simply do this at the command prompt 
sudo smbpasswd -a username
then it'll ask you for a password, enter it and hit return, then enter it again when it asks. this should be the username that you use on your ubuntu box. preferrably the same username as the one on your xp boxes as well but doesn't have to be. you should then be good to go. oh, you might want  to restart samba by doing this
sudo /etc/init.d/samba restart
I have a question for you. i can't see to be able to access my winxp shares? it says that there are no shares available despite the fact that there are. did you do anything special besides "sharing" the folders within xp? are you using home or pro? if pro, did you turn off simple file sharing? good luck and any answers to my questions would be helpful.

---

### Post by PriceChild on 2006-12-22
You could also edit your smb.conf file and set *security = share* instead of user.

---


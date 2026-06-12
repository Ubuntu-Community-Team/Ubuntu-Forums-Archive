---
title: "Configure Ubuntu for XP network login"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by DBrocks on 2008-04-21
Hey guys. I have a question: I want to know how to configure ubuntu SE for network-login on my XP machines at my house. I have a feeling its probably something to do with samba, but I'm lost after that. Any help is appreciated!

---

### Post by njparton on 2008-05-12
Could you be a bit clearer? 
 
Do you want to access files on your ubnutu PC from your windows PC?

---

### Post by mdr on 2008-05-12
I guess you want to setup your Ubuntu server to let your WinXP clients to login and browse shares etc.

Indeed it is Samba.  There are many good samba server tutorials on the web.
A starting point is here.
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
look for the 
**Samba Server Manual Configuration**
section
also try if you are on 7.10 - Gutsy
[http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller")
if you want samba as a domain rather than a simple share.

---

### Post by lswest on 2008-05-12
do you mean like what schools do, where they have student accounts set up on the network, so that when you log in with that username & password it loads up your samba share and gives you your saved settings?  If so, i'm not sure if it's possible to that extent in Ubuntu, but you can mount samba shares in Ubuntu (or just navigate to it via smb://<servername>/<sharename>/ and then log in)

---

### Post by DBrocks on 2008-05-12
> **lswest said:**
> do you mean like what schools do, where they have student accounts set up on the network, so that when you log in with that username & password it loads up your samba share and gives you your saved settings?  If so, i'm not sure if it's possible to that extent in Ubuntu, but you can mount samba shares in Ubuntu (or just navigate to it via smb://<servername>/<sharename>/ and then log in)

Yea, that's what I mean. My friend did that, but it's on a Gentoo server. I belive he had to set up samba as a domain controller.

---

### Post by lswest on 2008-05-12
hmm, if you want i can ask the IT guy at my school if he knows about it tomorrow (he actually hardly uses Linux, mainly just admins a red hat server and keeps all the mac & windows servers happy, however, he might know about it), and post back what i find out.  In any case, i'm not sure, but if it does work, that would be cool.

P.S. i just googled it, saw this: [http://ubuntuforums.org/archive/index.php/t-558481.html](http://ubuntuforums.org/archive/index.php/t-558481.html) not sure if that's exactly what you want though.  Maybe ask your friend how he did it, if you can?

---

### Post by DBrocks on 2008-05-12
Nah, I've decided not to do it. Thanks anyway guys. But lswest, post back how he does it.

---


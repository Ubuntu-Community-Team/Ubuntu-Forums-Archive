---
title: "Can't see second drive from windows machines."
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by hfnd on 2008-03-08
Total nube here, I started out looking for a less expensive alternative to NAS for my Windows home network. So Googling I must go,  stumbled upon Jon Peck's Blog (How to configure an $80 file server in 45 minutes),  went with it since most NAS have embedded Linux.  Well I'm re-evaluating the last 20 years of my life waisting my time with DOS and Windows. Ubuntu rocks. I used a spare P II, 400mhz, 512mb 1gb machine and aside from not hitting the spacebar to select LAMP and not knowing you had to sign in as root in SAMBA/SWAT web interface to commit changes, it all went pretty well. After experimenting with it for a month. I decided to take the plung and buy a 500gb drive and set it up as primary/slave formatted NTFS. While doing the research I noticed you could add a desktop to the server. Well the 1gb primary/master had to go (I know this is getting winded but please stay with me), I replaced the 1gb with a 60gb and started over. Here come the questions, I got the 500gb mounted and I can see it in COMPUTER on the gnome desktop but I can't see it on my Windows machines. Do I need to create a new share in SAMBA/SWAT and what path would I type ?  Also, I used the same hostname as the first build and I couldn't login to PHPmyadmin or Torrentflux. I was able to find the fix for PHPmyadmin but can't seem to find it for Torrentflux, any suggestions?

---

### Post by louieb on 2008-03-08
Which desktop did you install? ubuntu-desktop? 
You should be able to go into System>Adminstration>Shared Folders and set up a samba share there.  I've got a P2-400mHz w/384MB ram that I use for printer and file sharing. Slow but serviceable.  
   
Don't know anything about Torrentflux.

---

### Post by hfnd on 2008-03-08
Thanks,
Yes  installed ubuntu desktop, your suggestion worked.

---


---
title: "Out of box Server edition security?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by M374llic4 on 2007-12-10
How good is the security of the server edition on fresh install? I had redhat running xampp and with in a month it was hacked and completely destroyed. What can I do to prevent this problem in ubuntu? It looks like someone got in, then downloaded some files to the box and ran them and changed permissions around. 

    I was able to get back in to recover most of the web files and took it off the network. I now have a Ubuntu box running apache and all other programs gotten with apt-get instead of Xampp (which I secured with the included security program). I use webmin to administer the server. 

    Any help would be greatly appreciated as this is a live customer server : \

Thanks,
Dan

---

### Post by Orestes on 2007-12-10
Informal advice:

1. Close off any open ports
2. Disable unused services
2. make sure there's no telnet access, only ssh
3. Write a cron job to apt-get update & apt-get upgrade
4. Install tripwire and chkrootkit
5. disallow stupid passwords

I think that'll help to start with.

I've got an Ubuntu server, and it's been solid for about 8 months now.

HTH

---

### Post by M374llic4 on 2007-12-10
Thanks,
    I really appreciate the reply. Someone else also mentioned IPTables? I may have to check in to that also.

Thanks again,
Dan

---


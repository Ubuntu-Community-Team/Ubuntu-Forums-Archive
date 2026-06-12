---
title: "Question about partitions,samba, etc?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by lordViN on 2007-07-07
I want to make my main computer the data server of my LAN, and access all the data from xp/vista. I know I could use samba to make this right?. I have a 120GB and a 250GB hard drives, and my question is if I could make various directories in different drives or partitions to be shared  with samba. Or how could I share various partitions or drives ? 

what is the best method to do all this, please advice me!!  ;)

---

### Post by ukripper on 2007-07-07
Best method is to share directories using samba as you can set permissions for shares and would be able to change at anytime using chmod and chown

Here is guide -

[http://ubuntuforums.org/showthread.php?t=202605&highlight=how+to+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=how+to+samba)

---

### Post by lordViN on 2007-07-07
many thanks for you reply,  I have set up samba before, and I know that you need to specify your share directory in the smb.conf , but I want to share various partitions in 2 hard drives, can I specify different share directories, one for each partition? or how could I do this?

---

### Post by MatteBlack on 2007-07-07
Samba will let you export various directories as network shares. It won't mind if they are on different drives or partitions at all, it will just require additional entries in the configuration file. Concentrate on getting one directory to export as a share (there is normally some good example configurations in the smb.conf) Once you have one directory working as you like, then you can use the entry as a template for the rest.

If you have trouble understanding the example smb.conf try man smb.conf in the terminal for an explanation of the options.

If you get stuck also try the SAMBA checklist in the samba how to:

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

or even read the whole how to, that's what it's for!! ;)

---


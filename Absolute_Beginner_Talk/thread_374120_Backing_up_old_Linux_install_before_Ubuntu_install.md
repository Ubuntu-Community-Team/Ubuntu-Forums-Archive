---
title: "Backing up old Linux install before Ubuntu install"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-03-02
I'm going to install Ubuntu, but I previously used Linux - and after a lot of pain for a Linux newbie - got it running with an updated kernel.

I'd like to save this in case I ever need it again - how do I go about either backing up / saving the config before I install Ubuntu?

Thanks in advance!!!

---

### Post by xyz on 2007-03-02
Check [THIS]("http://www.ubuntuforums.org/search.php?searchid=15499063") out ...lots of ways to do it! Pick the one you feel most comfortable with.

---

### Post by qprfact on 2007-03-02
Thanks! I will have a read!

---

### Post by xyz on 2007-03-02
> **qprfact said:**
> Thanks! I will have a read!
You're welcome and don't hesitate to ask for help if need be. Good luck.

---

### Post by scxtt on 2007-03-02
"partimage" is GREAT for full backups of a working install ... i have quite a few, from different "restore points" even for different distros ...

**sudo aptitude install partimage** # from a live cd
mount the /dev/* where you want to store the image (DON'T mount the /dev/* to be backed up)
**sudo partimage** # it's intuitive to use, any questions, just ask :)
once the image is created, you've always got a usable backup you can fully restore from ...

one caveat - you'll need multiple HDDs in your PC (the one to backup, the one to save the backup to) ,,,

---

### Post by qprfact on 2007-03-02
And are all these backup methods non Ubuntu specific? i.e I can use them in Libranet to backup before I install Ubuntu?

---

### Post by qprfact on 2007-03-02
At home and ready to try - but all the links from xyz have gone!

Can someone remind me please?!!!

---

### Post by xyz on 2007-03-03
Here is a few:
[http://www.ubuntuforums.org/showthread.php?t=287522&highlight=qtparted](http://www.ubuntuforums.org/showthread.php?t=287522&highlight=qtparted)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup%2Crestore](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup%2Crestore)

---

### Post by qprfact on 2007-03-05
Thanks! I took the plunge at the weekend and all I can say is Wow!

Much more straightforward than Libranet (though I can't fault the support from other users on their forums), and works very intuitively.

Very impressed!

---


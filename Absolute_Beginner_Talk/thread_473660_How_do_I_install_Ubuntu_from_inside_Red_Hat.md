---
title: "How do I install Ubuntu from inside Red Hat"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by winsane on 2007-06-14
Hello...
I am using red hat linux and it is not my thing. What would be the easiest way to convert to ubuntu without losing my settings and files and bookmarks?

---

### Post by Seisen on 2007-06-14
I honestly don't think you can even do that.

---

### Post by Inxsible on 2007-06-14
Are you planning to do a dual boot with Red Hat?
 
You can shrink your red hat partition and install Ubuntu in the free space. If you have a separate /home partition, you can use the same for Ubuntu. But I do not think all your settings will be the same, because I imagine Red Hat and Ubuntu probably use different setting mechanisms.

---

### Post by Kobalt on 2007-06-14
The easiest will be to place your [Home folder onto a separate partition]("http://www.psychocats.net/ubuntu/separatehome"). This way you'll keep all your personal files and settings whatever distro you might install. 
You will install Ubuntu system on a partition giving it / as mount point and specify your Home partition with /home mount point, all this during the install process.

---

### Post by notwen on 2007-06-14
As posters above have stated, I'd recommend either backing up your /home and placing it into your fresh Ubuntu install.  It's very likely that lot of settings will not work, but you could always compare the settings from your backed up RH /home folder to the ones you create in your Ubuntu install.  Good luck w/ this. =]

---


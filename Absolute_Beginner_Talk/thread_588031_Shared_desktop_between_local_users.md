---
title: "Shared desktop between local users"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by clancymf on 2007-10-23
My wife is finally coming around to using linux (she doesnt really have a choice since I waxed windows).  However she wants her own log in so she doesnt have to look at my Dark theme.

We want to be able to have 2 user accounts but share all the same desktop folders so when she updates a folder I will see it and likewise.  Is there an easy way to set this up?

Thanks,
Mick

---

### Post by sugarland2k on 2007-10-23
My wife uses Ubuntu/Kubuntu a bit also.  I suggest you setup two seperate users accounts (yours and hers).  For shared files, I would suggest you create a share folder in /home as root.  I changed permissions in this folder chmod 777 /home/share, etc.  

Many on this list have fogotten more than I know but this has worked great for me.  Good luck.

---

### Post by clancymf on 2007-10-23
> **sugarland2k said:**
> My wife uses Ubuntu/Kubuntu a bit also.  I suggest you setup two seperate users accounts (yours and hers).  For shared files, I would suggest you create a share folder in /home as root.  I changed permissions in this folder chmod 777 /home/share, etc.  

Many on this list have fogotten more than I know but this has worked great for me.  Good luck.

Would this share folder be on our desktops or would she have to navigate to it?  
thanks for the response :)

---

### Post by digitalbenji on 2007-10-23
You could place a link to it on her desktop, and likewise on yours.

---

### Post by clancymf on 2007-10-23
Just to make sure i have this right:

ln /home/share/*foldername* /home/*wifeID*/Desktop/*foldername*

ln /home/share/*foldername* /home/*myID*/Desktop/*foldername*

Thanks.  

ps.  Im still pretty new at all this :) so I truly appriecate your alls help

---

### Post by bodhi.zazen on 2007-10-23
My wife and I share a box with this protocol :

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

The advantage is we do not have to log each other on and off to share.

If security is an issue, lock the desktop or log out.

---


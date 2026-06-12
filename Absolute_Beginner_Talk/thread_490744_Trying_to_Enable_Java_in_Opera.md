---
title: "Trying to Enable Java in Opera"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-07-02
Hi folks, 
Firefox has been giving me some problems the past couple of days, so I decided I needed an extra browser installed as a backup.  I installed Opera, and it works fine, unless I need Java for something.  I tried following the tutorial on the Opera site about enabling java, but when I get to the part where I enter the path to java, it can't read the jvm folder.  I'm assuming it's a permissions problem, but I'm still new at this, and not sure how to go about fixing it.  Any suggestions?  Thanks.

---

### Post by AdotB on 2007-07-02
Make sure all users can access the folder :

sudo chmod 755 -R path/to/java

Hope that helps.

---


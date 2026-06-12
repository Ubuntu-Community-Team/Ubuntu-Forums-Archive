---
title: "Need Help Installing Wine in Dapper"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by fattom23 on 2007-07-02
I'm a new linux user, running Dapper LTS.  I'm trying to install the newest Wine with Synaptic, but every time I try, I get the following message.  My best guess is that I need a new repo added to my list, but I have no idea which one.  Any help would be amazingly appreciated.  Thanks.  The error message is:

Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libgphoto2-2 (>=2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libgphoto2-port0 (>=2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.0.3-1ubuntu5 is to be installed
  Depends: libxml2 (>=2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
  Depends: libxslt1.1 (>=1.1.20) but 1.1.15-1ubuntu1 is to be installed

---

### Post by Computer-Geek on 2007-07-02
Try to install all the lib module in the message.

> 
Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
Depends: libc6 (>=2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed
Depends: libgcc1 (>=1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
Depends: libgphoto2-2 (>=2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
Depends: libgphoto2-port0 (>=2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
Depends: libstdc++6 (>=4.1.2) but 4.0.3-1ubuntu5 is to be installed
Depends: libxml2 (>=2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
Depends: libxslt1.1 (>=1.1.20) but 1.1.15-1ubuntu1 is to be installed


---

### Post by supersonicdarky on 2007-07-02
that means that those packages have to be installed before wine can be installed. it should automatically install them when you attempt to install wine. maybe you dont have universal repos enabled?

---

### Post by frodon on 2007-07-03
Explain what you mean fisrt by the "newest wine", which package have you downloaded or which repository did you add ?

---

### Post by fattom23 on 2007-07-03
Figured out the problem.  I had a repo enabled that had a Feisty only version of Wine on it.  My settings showed only the most recent version, which apparently wasn't compatible with Dapper.  When I disabled that repo, Wine installed with no problems.  Man, I would love to have the newest Ubuntu, but I was having so many stability problems with it.  Sigh.  Anyway, thanks a lot for the help.

---


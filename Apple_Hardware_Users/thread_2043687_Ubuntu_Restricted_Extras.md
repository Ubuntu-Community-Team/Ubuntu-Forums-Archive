---
title: "Ubuntu Restricted Extras"
date: 2012-08-17
forum: Apple Hardware Users
---

### Post by Dr. McKay on 2012-08-17
I'm running Ubuntu 12.04 on an early 2008 iMac and when I want to install the Ubuntu restricted extras, I get a message telling me I have to remove certain files.

I'm just wondering if it's safe to remove those files. Do other apps/services/etc. depend on them ? 

Same happened when I tried to install Wine...

Some help and/or advice, please !

---

### Post by Deepak J on 2012-08-17
What files does it ask to remove...?

---

### Post by Dr. McKay on 2012-08-17
Don't know by heart (I'm at work now). I'll have a look tonight and post the file name.

When I try to install Restricted Extras, it only asks me to remove one file, for Wine there's a whole bunch of 'em...

---

### Post by 2blue on 2012-08-17
You mean package manager/software center says something like " ___packages will be installed and ___ will be removed? I just press ok not really knowing what will happen, I have rarely had any problems. Perhaps some of the experts can give you better advice, but the restricted packages have never made a mess of anyting on my computers.

---

### Post by Deepak J on 2012-08-17
Yep it might be some kind of other files that have the same plugins included in the restricted extras that were installed when you installed some other kind of software.

Also Restricted extras, they don't cause much problem with the syst...
Also please try to post those files which are asked to remove or you can google it to have a better idea about those files.

---

### Post by Dr. McKay on 2012-08-17
To install Ubuntu restricted extras, these items must be removed :

Libav codec library
libavcodec53

and

Libav codec library
libavcodec51


To install wine, these items must be removed :
- alien
- debhelper
- gettext
- google-earth-stable (why on earth ?)
- intltool-debian
- lsb-core
- po-debconf


Any ideas ?

---

### Post by 2blue on 2012-08-17
Let the installer do it, or in terminal just press "Y", no worries.

---

### Post by Deepak J on 2012-08-17
libavcodec51,53  - it contains the plugins req to play mpeg,mpeg-2,mpeg-3,acc etc.

these will be replaced by those  in the restricted extras...

if any problem is found after the installation, you can install those from the software centre.

---

### Post by Dr. McKay on 2012-08-19
ok thx !

I suppose I can install wine as well then without worries ?

---

### Post by Deepak J on 2012-08-19
Well I don't think I can help you in that case, as I don't use wine...

But if you can pls tell the files that are being asked to be removed, well maybe I can give you an advice..

---


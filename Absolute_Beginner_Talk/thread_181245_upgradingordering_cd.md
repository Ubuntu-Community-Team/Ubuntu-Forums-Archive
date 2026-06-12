---
title: "upgrading/ordering cd"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by stansz on 2006-05-23
okay so im on the ShipIt website, and it says that the new version will start shipping june...but if i order now, will i get the new version??

on a different note, if i wanted to upgrade, how would i go about do that?? 

thanks all

---

### Post by aysiu on 2006-05-23
[QUOTE=stansz]okay so im on the ShipIt website, and it says that the new version will start shipping june...but if i order now, will i get the new version??[/quote] Yes, you'll get the new version.
> 
on a different note, if i wanted to upgrade, how would i go about do that?? 

thanks all Follow these directions: [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by stansz on 2006-05-23
sweet thnkx...is it the "stable" version yet? and is it wat is the main difference...?

---

### Post by aysiu on 2006-05-23
[QUOTE=stansz]sweet thnkx...is it the "stable" version yet? and is it wat is the main difference...?[/QUOTE] The one ShipIt sends you will be the stable version. Right now (and for the next week), it will be in Beta still, as the developers rush to patch all the bugs people have been reporting.

---

### Post by stansz on 2006-06-04
old thread revived...im having some problems upgrading to dapper...

this is the error message i get :

(gedit:18161): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by aysiu on 2006-06-04
Yeah, don't worry about that warning. A lot of times when you launch graphical applications from the terminal, you get all sorts  of weird warnings.

As you can, see it still lets you use Gedit.

---

### Post by stansz on 2006-06-04
thnkx..but: 
i got a window pop up..but its completely blank and i cant replace breezy with dapper causet heres nothing to replace

---

### Post by aysiu on 2006-06-04
[QUOTE=stansz]thnkx..but: 
i got a window pop up..but its completely blank and i cant replace breezy with dapper causet heres nothing to replace[/QUOTE] Are you sure you typed it in correctly? If you do ```
gksudo gedit /etc/apt/sources.list
``` it should pop up your sources.list. If you do, however, ```
gksudo gedit /etc/apt/sources.lst
``` it'll create a new file called *sources.lst* in the /etc/apt directory.

If you're not sure of your typing skills, try just copying and pasting the command from this post to your terminal (paste is Shift-Insert): ```
sudo cp /etc/apt/sources.list /etc/apt/sources_old.list
gksudo gedit /etc/apt/sources.list
```

---


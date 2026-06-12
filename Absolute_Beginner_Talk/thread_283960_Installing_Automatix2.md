---
title: "Installing Automatix2"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2006-10-24
I have automatix installed but would like to install automatix2. I'm trying to follows the directions in the WiKi pages for installing 2. When it say this: "NOTE: Kubuntu/Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository". what do I need to do? 

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)

---

### Post by tonyr on 2006-10-25
> **jmtjet said:**
> I have automatix installed but would like to install automatix2. I'm trying to follows the directions in the WiKi pages for installing 2. When it say this: "NOTE: Kubuntu/Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository". what do I need to do? 


The **sources** are listed in the file **/etc/apt/sources.list**.
Line in that file that star with **deb** or **deb-src** define
web sites where packages reside.  Some of those lines begin with a 
**#** character.  The instructions are telling you to remove the
**#** character at the beginning of those lines.

You will need to edit that file as **root**. using the **sudo**
command.  In Ubuntu, you might use the command 
```
sudo gedit /etc/apt/sources.list
```
In Kubuntu you might use **kwrite** instead of **gedit**
(or whatever editor you are comfortable with).

You will need to add this line at the bottom for the automatix package:
```
deb http://www.getautomatix.com/apt/ dapper main

```
if you are using Dapper (release 6.06).  Substitute **edgy**  if you
are using Edgy (release 6.10).

Most of this is documented at the Automatix website 
[http://www.getautomatix.com](http://www.getautomatix.com) on the **Install** page.

---

### Post by jmtjet on 2006-10-25
I'm embarrassed to say that I failed to read the instructions thoroughtly. I'm using Ubuntu not Kbuntu so the line in question in the instructions doesn't pertain to me. After I realized my oversite, I installed Automatix2 without a problem. Thanks for your reply.

---


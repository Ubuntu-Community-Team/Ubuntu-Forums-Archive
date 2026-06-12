---
title: "Radius"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by hohgch on 2006-05-05
Hi:

I am new to Ubuntu and Linux. I had little problems installing Ubuntu Breezy Badger, although it was a fun learning experience. 

I have two PCs running Ubuntu, one running the server and the other the desktop. I am trying the software freeRADIUS and have installed it on the desktop Ubuntu. I see it installed, but I can't seem to figure out how to run the app. I can't seem to find where it is located...

Help? Thanks a million.

---

### Post by glinsvad on 2006-05-05
A quick browse through the deb-package for freeradius reveals that binaries are placed /usr/bin/ with names such as radtest, radclient. Also I'm guessing that the primary program is called freeradius which is located in /usr/sbin/. These paths are normally defined in the environment, so Ubuntu should know where to look all by itself...

Basically you open up a terminal Applications -> Accessories -> Terminal and write:

> freeradius

If that does not work try:
> man freeradius

As a last resort, try:
> radtest

---

### Post by hohgch on 2006-05-05
I tried "freeradius" and the reply was error. cannot open file. no permission.

sigh.

---

### Post by Rinzwind on 2006-05-05
[QUOTE=hohgch]I tried "freeradius" and the reply was error. cannot open file. no permission.

sigh.[/QUOTE]
Try

**sudo freeradius**

Might have  to run it as root: 'No permission' is a normal notice ;)

---

### Post by hohgch on 2006-05-05
Thanks.

I tried that, and I got this:

starting. configure.

and that was it. is it suppose to be like that?

Sorry I am imposing like this. I really need to get freeRADIUS working urgently and there is really no one to help me in my area.

Thanks a million

---

### Post by glinsvad on 2006-05-08
Check out this tut - make sure you skip past the compile/installation part (don't you just love deb-packages :-)
[http://www.onlamp.com/pub/a/onlamp/excerpt/radius_5/index1.html?page=1](http://www.onlamp.com/pub/a/onlamp/excerpt/radius_5/index1.html?page=1)

Make sure you've got a directory /etc/raddb containing radiusd... this is probably the program then. Hopefully /etc/raddb is in your $PATH, you can see for yourself:
> echo $PATH

If it isn't, add it temporarily like this:
> export PATH="$PATH:/etc/raddb"

Then you can try opening up a port (here 12345) like this:
> radiusd -p 12345

Now, to see if you succeeded, view all listening ports:
> netstat -l

If you see port 12345 amongst them, then you'r made

---

### Post by user1397 on 2006-05-08
You might want to get this awesome app for searching for installed programs:
```
sudo apt-get update
```
```
sudo apt-get install xfce4-appfinder
```

---

### Post by hohgch on 2006-05-23
It has been a challenging week. I have been trying to setup a Ubuntu server with freeRadius, MySQL and phpmyprepaid to run... but to no avail. I keep getting these messages:

[4294673.483000] pnp:PnPACPI METHOD_NAME__CRS Failure for PNP0f13


and 

Error: /etc/freeradius/sql.conf [161]: Line is not in 'attribute = value' format



Can anyone help me out????? Thank you...

---


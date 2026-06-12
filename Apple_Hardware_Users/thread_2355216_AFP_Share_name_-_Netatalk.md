---
title: "AFP Share name - Netatalk"
date: 2017-03-10
forum: Apple Hardware Users
---

### Post by opabl on 2017-03-10
Hi Guys,
I have a very stupid issue that you probably will know how to easily correct.
I use Ubuntu 16.04 LTS with netatalk. Macs access this share via AFP. Although the share name is something i chose, when connecting to these shares you always see the name "Home Directory".
I've tried changing so many things already, i can't seem to find the right parameter to fix.
I'm attaching a picture of how the shares look like in a mac
[http://www.ayudatecno.com.ar/afp.jpg](http://www.ayudatecno.com.ar/afp.jpg)

Here's a thumbnail of said image:
[IMG]http://www.ayudatecno.com.ar/afp-thumb.png[/IMG]

and also this is my afpd.conf file (the part where the share is set):


> [inter]
path = /home/AFP
valid users = inter
comment = "INTER"




Please help me understand how to fix this, i just want the share to appear in Macs with the name i give them. everything else is working already.

Thanks in advance!

---

### Post by opabl on 2017-03-12
Hi!!!
I'm hoping someone is a lifesaver here and gives me a hint....
anyone around?

---

### Post by QIII on 2017-03-12
So the problem you are having is observed when you are on the Mac?

---

### Post by wildmanne39 on 2017-03-12
Please use thumbnails or Url's when posting images because many people have slow internet connections or limited band width.

---

### Post by opabl on 2017-03-18
Hi everyone,

i've fixed the image to a thumbnail.

Please help me out :)

---

### Post by opabl on 2017-03-21
bumping this thread up!! maybe someone around here knows the answer to this ???

---

### Post by QIII on 2017-03-21
Moved to Apple Hardware Users.

---

### Post by opabl on 2017-03-21
thanks, maybe someone here will know how to fix this!

---

### Post by scottt4 on 2017-03-21
Check out the configuration file /etc/netatalk/AppleVolumes.default at the very end of the file.  I've never used it, but it looks like what you are looking for.

---

### Post by katakaio on 2017-03-21
> **scottt4 said:**
> Check out the configuration file /etc/netatalk/AppleVolumes.default at the very end of the file.  I've never used it, but it looks like what you are looking for.

scottt4 is exactly right. The end of my (unmodified) AppleVolumes.default file reads:
```
# By default all users have access to their home directories.
~/                      "Home Directory"
```

Modifying the field in quotes will solve your issue, I believe.

> **QIII said:**
> Moved to Apple Hardware Users.

I respectfully disagree with the admin's move here...netatalk can run on any platform, not just Apple. While it's true that Mac machines are connecting to this service, this is an issue that someone running netatalk on an i386 version of Ubuntu could certainly run into.

---

### Post by opabl on 2017-03-22
Thanks @[COLOR=#DD4814][COLOR=#000000][katakaio]("https://ubuntuforums.org/member.php?u=303200") and @[/COLOR][/COLOR][[COLOR=#000000]scottt4[/COLOR]]("https://ubuntuforums.org/member.php?u=2027771")
[COLOR=#000000][/COLOR]
This appears to be the answer I was looking for.

Thanks for your help.

---


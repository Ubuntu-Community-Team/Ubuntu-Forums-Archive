---
title: "lightscribe label for Ubuntu 9.04"
date: 2009-04-25
forum: Art &amp; Design
---

### Post by waspinator on 2009-04-25
Here is a label I made to print on Lightscribe dvds. The included psd also has the words for other flavours of ubuntu.

To print these onto Lightscribe dvds in ubuntu use

1.Lightsctibe driver 
( [http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372) )

2. Laclie Labeler. 
( [http://www.lacie.com/support/drivers/driver.htm?id=10094](http://www.lacie.com/support/drivers/driver.htm?id=10094) )

The Laclie Labeler does not come in a deb (only rmp) so you'll have to convert it using alien or download the one I converted already.

psd and deb file for Laclie Labeler available here : [http://rapidshare.com/files/225621124/ubuntu_light_scribe.zip.html](http://rapidshare.com/files/225621124/ubuntu_light_scribe.zip.html)

EDIT: NEW LINK: [http://rapidshare.com/files/233267548/ubuntu_light_scribe.zip](http://rapidshare.com/files/233267548/ubuntu_light_scribe.zip)

Enjoy,

Waspinator

---

### Post by NFblaze on 2009-05-08
Pretty neat...Thanx

I just discovered that Linux has Lightscribe support...because the one in my Windows never works so I will definitely try this out. 

Thanks Again.

---

### Post by NFblaze on 2009-05-08
Aww...seems like the rapidshare link has maxed out...
heres another one only good for another 10 downloads

ill see if i can upload it using my premium acct later on
[http://rapidshare.com/files/230629363/4l_1.0-r6_i386_001.deb.html](http://rapidshare.com/files/230629363/4l_1.0-r6_i386_001.deb.html)

---

### Post by kamitsukai on 2009-05-08
I've put it on mint upload as well (only good for a couple of days but theres no wait time =])

> [http://files.mint-space.com/getfile,20090508170617,4l_1.0-r6_i386_001.deb.html]("http://files.mint-space.com/getfile,20090508170617,4l_1.0-r6_i386_001.deb.html")

---

### Post by waspinator on 2009-05-15
link updated

[http://rapidshare.com/files/233267548/ubuntu_light_scribe.zip](http://rapidshare.com/files/233267548/ubuntu_light_scribe.zip)

---

### Post by Gadgetech on 2009-05-15
I'll offer up my website to host this file.

[waspinator's Ubuntu 9.04 lightscribe package on TuxTweaks.com]("http://tuxtweaks.com/downloads/ubuntu_9.04_lightscribe.tar.bz2"):D

---

### Post by waspinator on 2009-06-10
Thanks Gadgetech!

---

### Post by ralley4 on 2009-06-13
Everything here is x86. :( I guess there is no 64-bit support yet?

---

### Post by Mike'sHardLinux on 2009-06-13
You can install the 32-bit packages in the 64-bit Ubuntu.

```

sudo dpkg -i --force-architecture package

```

---

### Post by ralley4 on 2009-06-13
Oh great, thanks for that insight!

---

### Post by pleasehelp123 on 2009-06-14
Please, please help - newbie here

In some earlier posts it is recommended that because the lightscribe software needs a root user to print - that you should add a user group called wheel - then add all users (so just me) to this group.  Then go ahead and install the software.

I have installed/uninstalled this piece of software about 20 times now, but no matter how I do it every time I install it, I need root privileges to print.

Where am I going wrong?

Thanks in advance for your help

---

### Post by Frdbrkl on 2009-06-24
> **pleasehelp123 said:**
> Please, please help - newbie here

I have installed/uninstalled this piece of software about 20 times now, but no matter how I do it every time I install it, I need root privileges to print.

Where am I going wrong?

Thanks in advance for your help

It seems to me that You're going absolutely *right*.  Call me insecure, but I *really* like an executable that asks me "are you SURE?".  As far as installing it to run without root, I believe that will require a script or at least modifying the executable permissions (hey, I'm noob as well, so I could be way off base here) of the file.

---


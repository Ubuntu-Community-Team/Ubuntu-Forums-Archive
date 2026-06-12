---
title: "Choppy Ubuntu screensavers with ATI 8.34.8"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by sam0t on 2007-03-01
Hello

Total newbie with Ubuntu 6.1 Edgy and I just installed latest ATI drivers using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I must add that I firsly installed the older drivers following the guides first method:
Method 1: Install the 8.28.8 Driver the Ubuntu Way

I then "updated" my ATI drivers using the following the guides "manual" way of doing thing. When I issue the command fglrxinfo in terminal I get the following info:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT
OpenGL version string: 2.0.6334 (8.34.8)

So it seems that the ATI drivers did indeed update but Iam having problems with my basic Ubuntu screensavers. With the old drivers they runned really smoothly but the screensaver failed to initialize properly (blank screen), so I decided to update the drivers. But now the 3D screensavers run really sluggishly and slowly :( 

Did I do something wrongly or is this common issue with the latest ATI drivers? Any help is apriciated :)

---

### Post by sam0t on 2007-03-02
bump, anybody got a clue?

---

### Post by Hallvor on 2007-03-02
I have an ATI Radeon 9600 myself, and it works great after installing the driver manually. All screensavers run very well. 

The manual installation here was the most useful for me. No problems.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

What you are experiencing is not normal, but since I`m a newbie, I can`t help. :(

---

### Post by sam0t on 2007-03-02
Yes it seems very strange since with the older drivers screensavers runned smoothly.

Could it be that did not even try to uninstall the old drivers? I just installed the new drivers over the old ones using the manual driver installation guide. 

Or could it be that the whole uninstalling software is my old Windows thinking? Any help is welcome.

---

### Post by igknighted on 2007-03-02
This seems to be a common issue.  I bet if you tried glxgears in the terminal you would get a very low FPS too.  Not sure there is a fix to this, you could go back and use the older drivers, that might help.

---

### Post by sam0t on 2007-03-05
The glxgears runs smoothly :confused: 

Yet when I preview 3D screensavers the performance is dreadful. Quess this is driver related problem, I see if I have the energy to try older drivers. Thanks for the help anyways :)

---


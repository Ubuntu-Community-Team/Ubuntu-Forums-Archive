---
title: "Slow Xubuntu on Old World iMac"
date: 2006-12-30
forum: Apple PPC Users
---

### Post by chocolatemintmocha on 2006-12-30
I have successfully installed Xubuntu on what I believe is an Old World iMac G3, but when I get to the log in screen it runs so slowly that it is unusable. When the login screen finally loads up, I can move the mouse around perfectley fine, but after I type in my login and press enter, it takes at least 10 minutes to load XUbuntu. Before Xubuntu was installed, this computer was running MacOS X, very smoothly. Is there anything that I can do, or tweaks that I can do to allow Xubuntu to run normally? Thanks.

---

### Post by maxamillion on 2006-12-30
It sounds like something horribly wrong has happened and I don't know where to start looking. I have Xubuntu on my iBookG4 and it gives me a notable performance increase over OS X, and interestingly enough gives me a longer battery life.

You might want to double check to md5sum of the your installation image.

---

### Post by chocolatemintmocha on 2006-12-30
How do I check it?

---

### Post by linear on 2006-12-30
> **chocolatemintmocha said:**
> I have successfully installed Xubuntu on what I believe is an Old World iMac G3

AFAIK, all iMac G3's are New World. No matter.

After installing, did you disable dri in xorg.conf?

---

### Post by chocolatemintmocha on 2006-12-31
> **linear said:**
> AFAIK, all iMac G3's are New World. No matter.

After installing, did you disable dri in xorg.conf?

I don't believe that I did disable it. How can I do this?

---

### Post by handylinux on 2006-12-31
> **linear said:**
> AFAIK, all iMac G3's are New World. No matter.
Yes, all iMacs are New World ROM. A few G3 Macs (the early platinum desktop models, and the original "WallStreet" PowerBook G3s) are Old World. The quick way to tell is if it has traditional Apple ADB and serial ports, it's Old World; if it has USB ports, it's New World.

And could this make a difference? I've installed Linux (Ubuntu) only on a couple of iBooks (New World), not on any Old World Mac; I understand the process for the latter is significantly different and a lot more hassle. Could it be that if the Old World installation procedure is used on a New World Mac Ubuntu might not run correctly?

---

### Post by chocolatemintmocha on 2007-01-01
I have finally solved the problem!! I want to say thanks to every one who has contributed to this thread. To get Xubuntu to run smoothly I loaded the bash shell prompt by pressing <controll-alt-f1> on the boot up. Then I logged in to my account. I typed the command sudo vi /etc/X11/xorg.conf. In the vi editor I typed i to enter edit mode I commented out Load "dri" from the Section "Module" section by typing # in front of it. Then I pressed escape to exit insert mode, and I saved it by typing :w, and exited with command :q. Then I typed <control-alt-delete> to reboot the system. On reboot It worked perfectly!  [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by 3rdalbum on 2007-01-01
> **handylinux said:**
> I've installed Linux (Ubuntu) only on a couple of iBooks (New World), not on any Old World Mac; I understand the process for the latter is significantly different and a lot more hassle. Could it be that if the Old World installation procedure is used on a New World Mac Ubuntu might not run correctly?

Linux won't load up at all if you tried the Old-world procedure on a New-world, so we definately know that the original poster has started Ubuntu in the correct way.

---

### Post by a2brute on 2008-01-22
I have just installed XUbuntu 7.10 on an iMac G3 500.  Once a user X session has loaded, the desktop is so slow it takes 10 to 30 seconds for keystrokes and mouse movements to register.

I opened the xorg.conf file as instructed, but I found no "module" section in the file, and nothing regarding "dri".

Does anyone know another method to resolving this problem?

---

### Post by a2brute on 2008-01-22
After I continued googling the problem, I found the answer here:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

I created the necessary "module" section in the xorg.conf disabling the "glx" and "dri" modules. Now the iMac runs great, even faster than with Mac OS.

Hope this link helps others.

---


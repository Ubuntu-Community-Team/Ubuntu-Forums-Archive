---
title: "Installing Firefox update"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by Edmund Hon on 2005-05-14
I just got Ubuntu installed OK (hey I am typing here, right?). I tried to get a new theme but firefox informed me that there is a newer version (Ubuntu installed 1.02, the latest is 1.04). So I downloaded the latest version and extracted it into a folder on my desktop. Now how do I install it over the Ubuntu default version?

---

### Post by thierry on 2005-05-14
To update your system go to System - Administration - Update Ubuntu.

This is much easier, and there are more updates than just Firefox :)

---

### Post by sleeping on 2005-05-14
[QUOTE=thierry]To update your system go to System - Administration - Update Ubuntu.

This is much easier, and there are more updates than just Firefox :)[/QUOTE]

True, however, as of today (May 14th), it says "Your system is up-to-date!", while I still have Firefox 1.0.2.

Since 1.0.4 addresses security issues, and it is now impossible to access the addons.update.mozilla.org website without a more recent version, it would be nice to see an updated package for Firefox.

---

### Post by thierry on 2005-05-14
Well then if you have the .deb package going to the folder where you downloaded it and type : sudo dpkg -i the name of the package.deb should do it.

---

### Post by bored2k on 2005-05-14
[QUOTE=thierry]Well then if you have the .deb package going to the folder where you downloaded it and type : sudo dpkg -i the name of the package.deb should do it.[/QUOTE]
 Don't guide newcomers the wrong way :(. There is no .deb package for Firefox 1.04.

Regarding the saving it over Ubuntu's Firefox. I could tell you how to do it, but don't. Let ubuntu update itself, don't it for him. YOu can open your extract firefox install opening "firefox" command.

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=sleeping]True, however, as of today (May 14th), it says "Your system is up-to-date!", while I still have Firefox 1.0.2.
[/QUOTE]

Ubuntu officially only fixes the security holes in the firefox that shipped the day of release. They will soon release an updated Firefox 1.0.2 with the holes fixed, but Firefox 1.0.4 will not be officially released because it might introduce instability that the developers don't want to deal with.

If all you care about is security, it is being dealt with and updates will be out soon.

If you want it for other reasons, there is a way to get it that works well. Wait for Jdong to stabilize his own version of Firefox 1.0.4:

[http://ubuntuforums.org/showthread.php?t=34099](http://ubuntuforums.org/showthread.php?t=34099)

---

### Post by chettyk on 2005-05-14
What I did was download Firefox 1.0.4 tar.gz file directly from the Firefox website and install it WITHOUT overwriting the Ubuntu Firefox. When one runs the downloaded Firefox, it reads the Ubuntu Firefox's bookmarks. This way, I can use the latest and more secure Firefox. When Ubuntu updates its Firefox, I can install that with apt-get/Synaptic.

---

### Post by Edmund Hon on 2005-05-14
FireFox won't let me install any themes without 1.04. I guess I could install 1.04 as a second copy of FireFox, but I don't really like having two copies of the same app on my system - it's just not my style.

---

### Post by picpak on 2005-05-14
I've been trying to get this to work too...Firefox releases too many programs at a time! :razz:

---

### Post by thierry on 2005-05-14
I hope this page (at the bottom) can help you :

[https://bugzilla.ubuntu.com/show_bug.cgi?id=10681]("https://bugzilla.ubuntu.com/show_bug.cgi?id=10681")

In your url type about:config
Look for the line general.useragent.vendorSub and replace 1.0 with 1.0.4

---

### Post by Edmund Hon on 2005-05-14
[QUOTE=thierry]I hope this page (at the bottom) can help you :

[https://bugzilla.ubuntu.com/show_bug.cgi?id=10681]("https://bugzilla.ubuntu.com/show_bug.cgi?id=10681")

In your url type about:config
Look for the line general.useragent.vendorSub and replace 1.0 with 1.0.4[/QUOTE]

That worked, thanks! I was able to download the theme that I wanted but now another problem. When I click on the "Install" link on the theme I was prompted to save the JAR file. I thought firefox was able to automatically extract in install that? What do I do with the JAR file?

---

### Post by N'Jal on 2005-05-14
Ah I can answer this one :D

Mozilla update is currently unsecure for a short ammount of time. Thus they make you install the theme's manually. This is the jar file. Click tools theme or extention then drag and drop the theme or extention onto the theme/extention list box.

This is the way mozilla reccomend for the time being that you install software

---

### Post by Edmund Hon on 2005-05-14
Got it. Thanks!

---

### Post by RobotoWorks on 2007-12-09
Just to tell you, they just released 2.0.0.11 And they are working on the Grand 3.0 :)

---


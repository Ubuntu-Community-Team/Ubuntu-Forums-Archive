---
title: "Java and Firefox 2.0"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by error691 on 2006-11-14
I'm having awful trouble getting Java to work in Firefox 2.0.
The site I'm using to test is chessgames.com.

I've tried about half a dozen different ways (from reading on forums and such) including installing manually and using Automatix2.
So I've probably ruined it somehow and need to link firefox to the correct installation.

When I look at "about:plugins" I get no Java plugin listed.

Can someone guide me through checking what I have now, and then maybe how to get Java working in Firefox?

Thanks a million.

ps. I'm using Ubuntu 6.06 with Gnome and am an absolute newbie to Linux!

---

### Post by LLRNR on 2006-11-14
Have you tried everything that's stated [here](https://help.ubuntu.com/community/Java) and it didn't work ?

---

### Post by error691 on 2006-11-15
Yes, I have tried everything on that list that is relevant to 6.06 Ubuntu.
This is why I thought maybe I've stuffed it up by trying so many different ways.
I don't know how Linux works but it is like Java is installed but Firefox does not know where to use it?

The only thing I haven't done is reboot my machine, which I'll try now, but I'm thinking that only Windows needs reboots after installing new programs?

---

### Post by littlespy on 2006-11-15
if you install the sun-java-jre in synaptic it should install the mozilla plugin

---

### Post by sushilksk on 2006-11-15
search for **sun java jre** in synaptic, it should show 

sun-java5-bin
sun-java5-fonts
sun-java5-jre
sun-java5-plugin

install plugin from here if java is already installed or install all packages

---

### Post by error691 on 2006-11-15
I checked Synaptic and had all of those already installed, but I reinstalled anyway just to be sure, but no difference.

I checked the Mozilla plugin help page, and found this:

# Make a symbolic link to libjavaplugin_oji.so in your Mozilla Plugins directory. Use the copy located in the plugin/i386/ns7 directory of JRE 5.0, or plugin/i386/ns610-gcc32 if you are using JRE 1.4.2.

Now I remember making this symbolic link while following instructions from some Ubuntu page, but maybe I've not linked to the correct location (as I would've copy-pasted), is there a way of checking where this should be?

Thanks for the help so far!

---

### Post by steve.horsley on 2006-11-15
Try this:
1:
Command **gksudo nautilus** to open a file manager with root priviledge
2:
navigate to /usr/lib/firefox/plugins
3:
menu File->Open New Window to get another root file manager
4:
navigate the new window to /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7
5:
use the **middle** mouse button (or both left and right buttons if you don't hvae a middle button) to drag the file **libjavaplugin_oji.so** from the second window to the first. You are asked whether to copy, move or link. Choose link.
6: 
close the nautilus windows, restart firefox (exit **all** firefox windows - command killall firefox-bin will do the trick).

---

### Post by error691 on 2006-11-25
I tried that too and it didn't work.

But good news.
I installed Opera web browser and it works perfectly. Didn't eben have to change the default configuration to get Java working.

I cannot believe how much time I wasted with Firefox when such a superior program was available!

I've used Firefox since it was Mozilla and then Firebird, but now I think that OPERA is my choice.

Thanks for all the help friendly people! =)

---

### Post by vayu on 2006-12-01
> **error691 said:**
> I tried that too and it didn't work.

But good news.
I installed Opera web browser and it works perfectly. Didn't eben have to change the default configuration to get Java working.

I cannot believe how much time I wasted with Firefox when such a superior program was available!

I've used Firefox since it was Mozilla and then Firebird, but now I think that OPERA is my choice.

Thanks for all the help friendly people! =)

Opera's a great browser but your problem has nothing to do with Firefox.  It's about getting the plugin in the right directory.

---

### Post by ddbann on 2006-12-02
thanks for the word about Opera. i was having trouble with for example [http://www.twit.tv](http://www.twit.tv) and [http://www.nickjr.com](http://www.nickjr.com) with opera 95% of my problem is gone and the sites don't crash out before they even load with Firefox.

---

### Post by HokeyFry on 2006-12-02
try using automatix2

google automatix2, i dont remember the website offhand

---

### Post by torbjorn on 2006-12-04
Are you sure your firefox 2.0 installation is located in /usr/lib/firefox?

When version 2.0 was new (and maybe still) it was recommended some places not to replace the firefox 1.5 files. My firefox-installation is for example located in /opt/firefox. Therefore the linking of the plugin (as described earlier in this thread) must then be done to the correct location for the 2.0 installation, which in my example would be /opt/firefox/plugins/

---


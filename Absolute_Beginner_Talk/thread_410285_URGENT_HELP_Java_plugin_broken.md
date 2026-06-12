---
title: "URGENT HELP Java plugin broken"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Kramxel on 2007-04-15
Hi
I just installed update 1 for java 6 following the tutorial I found on the site.
My problem is the libjavaplugin_oji.so link in the plugins folder of firefox is broken!
So firefox keeps using the older java 1.6.0 plugin.

I followed every step of the tutorial, including some (lazy) copy-paste of the inputs.

Help me
i'm desperate because i have to submit my IRS today, and the site applet only accepts java 6 update 1...

---

### Post by Seisen on 2007-04-15
Which tutorial did you use, please post the link.

---

### Post by Kramxel on 2007-04-15
This is the one I used, and the only one I know about.
I used jre version not the sdk one.

[http://ubuntuforums.org/showthread.php?t=332674#1](http://ubuntuforums.org/showthread.php?t=332674#1)

Thanks for your quick reply

---

### Post by Kramxel on 2007-04-15
FOUND IT!!!!

The problem was with the path!
After a whole afternoon spent trying to figure it out!
I feel like an *******...

The problem is with this line:

sudo ln -s /usr/lib/Java6u1/**jre**/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

It should be 
**/usr/lib/Java6u1/plugin/i386/ns7/libjavaplugin_oji.so**

Many thanks for your time!

---

### Post by thefoolisme on 2007-04-15
FYI, I believe the tax deadline is April 17th this year.  :-)

---


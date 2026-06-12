---
title: "MacMini PPC xorg"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by kingmoffa on 2008-05-06
Hi, 

After upgrading to 8.04 my mac mini becomes unresponsive every now and again. Im pretty sure its a problem with Xorg , as top shows its cpu usage much higher than normal.

It only happens at random points when using firefox (version 3 in herdy) or evolution. 

Im using a pretty basic xorg.conf - with X being able to detect things well. (It uses the radeon driver as it should) glxgears seems to work fine. 

Any suggestions?

---

### Post by stream303 on 2008-05-06
Ah, the Firefox and Evolution issues can be fixed, although I'm not sure if updates are fixing it yet.

For Firefox Beta5, you can disable it wanting to check for possible attack sites in Firefox in Edit > Preferences > Security

Then, close firefox, and delete the urlclassifier files in

~/.mozilla/firefox/[your profile].default/urlclassifier*.sqlite

where your profile usually looks like some random letters for a filename.

To enhance security, I like to run the Firefox extension add-on called "NOSCRIPT", leaving both javascript and java enabled in firefox, and let noscript deal with it instead.

Evolution:
It has been reported that disabling the alarm notifier helps by going into System > Preferences > Sessions and UNchecking the Evolution Alarm Notifier

See if these tips help - and again, future updates might fix these problems.  Other than that, glad to hear your ppc is up and running!

---

### Post by kingmoffa on 2008-05-07
Thanks for the advice. 

I have made changes to firefox and evolution. Fingers crossed.

---


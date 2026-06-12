---
title: "What does &quot;Reloading Postfix Configuration ... failed&quot; mean ?!"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-13
Hi folks !

I can't figure out why each time I boot my computer, when I see the (K)ubuntu logo with the verbose booting issues, I get, after the other lines of text,
```
Checking all filesystems ... ok
Reloading Postfix Configuration ... [COLOR="SeaGreen"]failed[/COLOR]
```

This has been happening for a few days now and I don't even know what Postfix Configuration is... :oops: 

Can someone "enlighten" me, please, I feel really stupid for not knowing what many of those things that come up when booting the PC mean... :oops:

Thanks in advance,

LLRNR

EDIT : I'm using Dapper.

---

### Post by JayTee on 2006-11-13
Are you using Evolution for E-mail which is what Dapper defaults with or have you switched to another email program like Thunderbird? Postfix is a suite of daemons for sendmail in Unix, Linux. It looks like something has mucked up it's configuration file.

---

### Post by LLRNR on 2006-11-13
Hi and thanks for your reply. Strange enough, i'm not using e-mail clients at all, I only check my mail online at yahoo.com when Kopete (I use KDE) announces me that I have new mail. Does Postfix do anything else beside handling mailing issues? 

The only "crazy" things I did recently are grabbing kubuntu-desktop (and I now use KDE display manager) and a few days ago, trying to set up Beryl/xgl (it ran kind of smooth for half an hour, and then crashed, so I removed XGL from my sessions menu and the autorun script in ~/.kde/Autostart)

Could there be anything else which causes Reloading Postfix configuration to fail ?

LLRNR

---

### Post by JayTee on 2006-11-13
I may have misled you. Postfix is a MTA or mail transport like sendmail. So something in the setup of your Dapper system wants to initialize that daemon and it's configuration is broken. I'm not that familiar with how Postfix is setup on Ubuntu but if you search there are several threads on it. I'm not using Kubuntu, I'm just running Dapper with Gnome and Beryl/XGL. I'm not sure why you're getting that error but was wondering if you installed the desktop version of Ubuntu or the server version and then added the KDE desktop afterwards as a gui. If you installed the server version that may have something to do with the error or it could just be a file for whatever sendmail services get setup by default in the Dapper install got corrupted when you were trying out Beryl/XGL. I'm wondering if something else got deleted from the autostart script that Postfix needed. I suppose if you can still get Yahoo mail and Kopete isn't broken and everything else works you could ignore it. Hopefully someone with more experience can add to this thread some ideas or a solution.

---

### Post by LLRNR on 2006-11-13
Thank you for your kindness and patience!

No I don't have the server version, I use Dapper - the desktop version, and as you guessed I just "aptitude install"-ed kubuntu-desktop.

When I installed Beryl with XGL, I followed a good HowTo I found around (sorry but I can't find the link right now) and I created another session called XGL and in my ~/.kde/Autostart folder - which was EMPTY - I added a script which I then made executable by modifying permissions, telling beryl-manager to load by default in the KDE session. 

So after Beryl crashed (in fact I don't know what exactly crashed, but my hunch is that it was a WM-crash since I lost focus control on windows and the windows' frames) I logged in using the Failsafe Terminal session and I just un-did the steps in the HowTo - mainly I deleted the .startup script for the XGL session and the autorun script I had just created in ~/.kde/Autostart... That folder was empty at the beginning, so I don't believe that it in particular had anything to do with the "Reloading Postfix configuration ... failed" status.

Yes otherwise anything seems to be ok (LOL except the HDD I have Ubuntu upon is DYING so I'll have to reinstall it on the other until-this-moment-good-HDD hahahaha !!)

Thank you again, JayTee !

LLRNR

---


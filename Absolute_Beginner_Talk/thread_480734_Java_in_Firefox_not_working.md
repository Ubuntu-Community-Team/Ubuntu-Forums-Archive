---
title: "Java in Firefox not working?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-06-21
I recently installed Ubuntu and think it's pretty cool. It automatically detected my hardware and everything seems to be running faster than with win XP.

There's one problem though:_ Java doesn't seem to work in Firefox!?_ I need it to be able to log in to my bank so this is a pretty serious problem for me.

Both Javascript and Java are enabled in Preferences, I simply can't figure out why it's not working.

Any input on how to solve this problem would be greatly appreciated!

---

### Post by FuturePilot on 2007-06-21
Have you installed Java with Synaptic? System>Administration>Synaptic Package Manager
Search for Java.

---

### Post by Majorix on 2007-06-21
OK how did you install Java? Through the repos or downloaded it off the net?

---

### Post by Pconfig on 2007-06-21
Try this one out:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

---

### Post by Martin Witte on 2007-06-21
you can follow this howto [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox) to get java going

---

### Post by old_geekster on 2007-06-21
The easiest way that I know to install Java so it works properly is using "Automatix2".  I tried every method with no success.  Try it.

Automatix2 is in "Synaptic Package Manager".

---

### Post by wormser on 2007-06-21
I had a problem with java and firefox and the following command solved it.

```
sudo apt-get install sun-java6-plugin
```

It installs the java plugin for firefox.

---

### Post by obbe on 2007-06-21
you need to install java by synaptic; you can search it directly by synaptic or typing ```
sudo apt-get install sun-java6-jre
```

---

### Post by manro on 2007-06-21
> **pointyblue said:**
> I recently installed Ubuntu and think it's pretty cool. It automatically detected my hardware and everything seems to be running faster than with win XP.

There's one problem though:_ Java doesn't seem to work in Firefox!?_ I need it to be able to log in to my bank so this is a pretty serious problem for me.

Both Javascript and Java are enabled in Preferences, I simply can't figure out why it's not working.

Any input on how to solve this problem would be greatly appreciated!

Try this: [http://ubuntuforums.org/showthread.php?t=436933&page=2 ]("http://ubuntuforums.org/showthread.php?t=436933&page=2")

MaNRo ;)

---

### Post by pointyblue on 2007-07-15
Thanks all of you for the input!

After trying a lot of different things and almost giving up I decided to try Automatix. (I heard someone say it could crash the system so I decided to try it only if all else failed.)

Anyway: It worked! 

:)

---


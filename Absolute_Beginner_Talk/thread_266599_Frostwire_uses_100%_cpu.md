---
title: "Frostwire uses 100% cpu"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by BlocknBleed on 2006-09-27
Is it normal for frostwire when doing a few searches and a few downloads to consume my entire 1800MHz processor. I have nothing else in use except firefox. My system monitor says the Frostwire>sh>Java  is the culprit. 
Would aMule be a better option?
Any thoughts?

---

### Post by sabitha on 2006-09-29
how you install that?
did you install with .deb or the package zip
i solve the problem like you with remove the .deb then reinstall with extrack the zip package to /opt 
hope this can help .... :)

---

### Post by JoshHendo on 2006-09-29
It is a feature built into Ubuntu to prevent you downloading illegal material.

Well, not quite.

I am assuming that it has to do with the fact that FrostWire uses Java. Do you get this much CPU usage for other Java apps?

- Josh

---

### Post by Boatswain on 2006-09-29
I've had a similar problem lately with Frostwire--it works fine for five or ten minutes, then slowly bogs down and goes nonresponsive.  This has been a recent thing for me though, like over the past 3 weeks or so.  Before that, it worked fine.  Perhaps there was a recent update to it, but I don't recall one off the top of my head.

---

### Post by Zyphrexi on 2006-11-03
java has done this for as long as I can remember, I wish there was a sticky on improving performance with java.

---

### Post by sabauma on 2008-01-28
I tried every other method mentioned to try to remedy the problem and had little success. There are several different java versions that you can try and some did seem to delay the problem. The thing that worked for me was surprisingly simple though.
1. Open the system monitor.
2. Find the power hogging java application under processes.
3. Right click on the java application and click on the option marked "change priority."
4. A window will pop up with a bar. Move the bar all the way to the right.
5. Be sure that frostwire is running while doing this.

This gives the java application a "nice" value of twenty which gives it a low processor priority. From what I have seen, it does not slow the application down at all and it then uses far less processing power.

---


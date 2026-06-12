---
title: "How does adept_notifier autostart on every session ???"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by afternine on 2007-04-13
Hi!

Can someone enlighten me what is the mechanism behind the adept_notifier autostart of every session? How is it started, where is this configured?


BTW; I have Kubuntu 6.10 32 bit.

Thanx

---

### Post by barbolani on 2007-08-26
In essence, in /user/share/autostart you will find a lot of files with the extension .desktop. Those .desktop files contain, one for each program, the set of programs that are run on every KDE startup. Among them is, guess what, adept_notifier_auto.desktop, which is the one responsible for executing the adept_notifier program.

---

### Post by afternine on 2007-09-05
Hi!

Thanx for reply, indeed there are the files responsible for autostarting the applications.

Sorry for late reply, had some issues with mail server (did not get notifications)

Bye

---


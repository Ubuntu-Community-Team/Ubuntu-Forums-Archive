---
title: "installing firefox updates"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by kanha on 2007-02-25
hi,
My firefox is crashing every 10 minutes.I thought that installing update may fix the problem.so please anybody guide me how to update firefox.
i am using 2.0.0.1 and 2.0.0.2 is out
there is a tab for update in preferences,but there is option for only add-ons and search engines

---

### Post by haricharan on 2007-02-25
try loading firefox from terminal and see if you could actually see whats making it crash!!....that way you can fix it

---

### Post by Chemist on 2007-02-25
i've been having a few problems lately of firefox crashing every hour or so. I didn't realise a new version was out. I'll try and update mine when I get on my linux box

---

### Post by kanha on 2007-02-25
> **haricharan said:**
> try loading firefox from terminal and see if you could actually see whats making it crash!!....that way you can fix it

it is not crashing during startup
it is arbitrary. It crashes whenever it wants,sometimes it does not crash.
so you are saying that i should leave my terminal open all time.
if yes then i will do that

---

### Post by karls0 on 2007-02-25
Hi Kanha,
I´m running Kubuntu 6.06 and using Firefox 2.0.0.1 and never have a problem. Maybe you should uninstall and do a new install? But remember, the personal settings are kept. I think they are in a hidden directory inside your /home. Maybe you move them to a safe place - in case the cause of the problem lies in them.

hth
Karl

---

### Post by JTP on 2007-02-25
You may want to have a look at your extensions.  Sometimes when they update, they can have an adverse effect.  So think about which ones you've updated recently.  It is a rather tedious process, but you can uninstall  (and then re-install) those recently updated extensions and see if the problems persist.  I can't remember the extension, but I had a similar problem about six months ago.  Once the extension was fixed I was able re-install it and run things the way I had before.  Also keep in mind that the combination of extension you have could be an issue as they update.  One extension may not cooperate with another.  

These aren't terribly specific suggestions, but maybe it'll help.

---

### Post by ThrobbingBrain66 on 2007-02-25
> **kanha said:**
> it is not crashing during startup
it is arbitrary. It crashes whenever it wants,sometimes it does not crash.
so you are saying that i should leave my terminal open all time.
if yes then i will do that

Yes, just leave it minimized until Firefox crashes.  The terminal will spit out an error message and we'll be better able to diagnose your problem.

---

### Post by ThrobbingBrain66 on 2007-02-25
> **Chemist said:**
> i've been having a few problems lately of firefox crashing every hour or so. I didn't realise a new version was out. I'll try and update mine when I get on my linux box

unless you installed yourself from mozilla's site, you'll have to wait for the repo's to be updated with 2.0.0.2 before you can update.

---

### Post by FLPCGuy on 2007-02-25
> **ThrobbingBrain66 said:**
> unless you installed yourself from mozilla's site, you'll have to wait for the repo's to be updated with 2.0.0.2 before you can update.
It appears automatic updates of Firefox are permanently disabled in the Ubuntu repository version that came pre-installed in Edgy. Why? What other changes were made to Firefox and can we expect the recent security fix to be posted to the repos anytime soon?

Has anyone tried removing Firefox and re-installing Mozilla's code manually to get the updates directly?  Is the delay in getting browser security updates from the Ubuntu repository an issue worthy of concern?

"[FONT=Arial,Helvetica][SIZE=2]Feb. 23, 2007 —[/SIZE][/FONT]                 [FONT=Arial,Helvetica][SIZE=2][IMG]http://www.desktoplinux.com/files/misc/firefox-thm.jpg[/IMG]Mozilla Corp. today released updated versions of the Firefox browser, v1.5.0.10 and v2.0.0.2, for Windows, Mac, and Linux, that close a major security flaw called the "location.hostname vulnerability." The fix stops hackers from being able to tamper with how websites are displayed. [/SIZE][/FONT]"

---

### Post by Detonate on 2007-02-25
I will say that JTP is the one with the solution.  Whenever I start having problems with FF, I disable each extension one by one to see if I can identify the one causing the problem.  Also I think the FF 
update function is not available in the Linux version, that's only for windows.  Probably because there are too many distros out there for the Mozilla folks to make a universal Linux update.

---

### Post by ThrobbingBrain66 on 2007-02-25
> **FLPCGuy said:**
> It appears automatic updates of Firefox are permanently disabled in the Ubuntu repository version that came pre-installed in Edgy. Why? What other changes were made to Firefox and can we expect the recent security fix to be posted to the repos anytime soon?

Has anyone tried removing Firefox and re-installing Mozilla's code manually to get the updates directly?  Is the delay in getting browser security updates from the Ubuntu repository an issue worthy of concern?

"[FONT=Arial,Helvetica][SIZE=2]Feb. 23, 2007 —[/SIZE][/FONT]                 [FONT=Arial,Helvetica][SIZE=2][IMG]http://www.desktoplinux.com/files/misc/firefox-thm.jpg[/IMG]Mozilla Corp. today released updated versions of the Firefox browser, v1.5.0.10 and v2.0.0.2, for Windows, Mac, and Linux, that close a major security flaw called the "location.hostname vulnerability." The fix stops hackers from being able to tamper with how websites are displayed. [/SIZE][/FONT]"

It's only a delay of a few days...a week at the most.  You surfed the Internet for x amount of time without the update.  A few extra days are of no concern.  btw, it IS possible to install mozilla's build to receive the updates right away if you wish.

---

### Post by r4ik on 2007-02-25
Firefox 2.0.0.2 still has a bug.

'quote"

"Well, it is here. The new FF 2.0.0.2 Final:

[http://www.mozilla.org/news.html](http://www.mozilla.org/news.html)

From what I have read, there is a bug. I bet it won't be long before it is patched"

So i guess you have to wait a little.

---


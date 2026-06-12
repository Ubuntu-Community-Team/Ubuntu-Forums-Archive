---
title: "Lucid keeps freezing"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by gotenks05 on 2010-04-30
Hello, I am running a web server on my old iMac5,1, which is also my main computer, but I'm having troubles.  I upgraded to Lucid because Hardy kept dropping my Internet, so my server would not work.  However, I have a different problem now.  Everytime I log into Ubuntu, it eventually lags in the GUI.  Sometimes, it even freezes entirely.  On my newer Macbook Pro5,3, running from a Live CD, it freezes there to.  It never froze in Ubuntu Hardy or Ubuntu Jaunty.  What is causing this constant freezing?

---

### Post by kosumi68 on 2010-05-01
> **gotenks05 said:**
> Hello, I am running a web server on my old iMac5,1, which is also my main computer, but I'm having troubles.  I upgraded to Lucid because Hardy kept dropping my Internet, so my server would not work.  However, I have a different problem now.  Everytime I log into Ubuntu, it eventually lags in the GUI.  Sometimes, it even freezes entirely.  On my newer Macbook Pro5,3, running from a Live CD, it freezes there to.  It never froze in Ubuntu Hardy or Ubuntu Jaunty.  What is causing this constant freezing?

Does the computer feel extra hot when it happens?

---

### Post by zeroti on 2010-05-01
also, is this freezing temporary or does it make you have to reboot? If it's temporary, is it just some application or is it the entire system?

---

### Post by gotenks05 on 2010-05-02
> **kosumi68 said:**
> Does the computer feel extra hot when it happens?

Not really.  I mainly use OS X on my MacbookPro5,3, so only ran Ubuntu from a LiveCD.  My iMac5,1 certainly did not feel hot.

> **zeroti said:**
> also, is this freezing temporary or does it make you have to reboot? If it's temporary, is it just some application or is it the entire system?

It forces me to do a hard reboot at almost every problem, one of which is the freezing that I mentioned and another is the screen sometimes goes black, which also forces a hard reboot to be issued, both from the installation on the iMac and from the LiveCD.

---

### Post by aaronluis26 on 2010-05-07
I'm having this problem too and I'm not sure why. I'm doing everything normally like I did in Karmic, but for whatever reason Lucid just wants to freeze. I'm having a lot of issues with Lucid right now and it's really driving me crazy. I wish I knew how to fix this because I'm having to hard boot it six times a day. It's really annoying -_-

---

### Post by Wr4tH on 2010-05-12
I think I have the same problem, my computer starts freezing randomly, but it occurs a lot more when I surf with chrome. Suddenly my screen starts freezing and updates about every 10s, even though I can see my mouse pointer in realtime. I mean moving my mouse is fine, but every time I click or move it over something animated like my dock, it takes a lot of time to take it into account and update what I see on my screen. It is very annoying, logging out and in does solve the problem, but you can imagine how long it takes, I need at least 4 clicks to log out...

---

### Post by Jakiejake on 2010-05-22
It happens to me too
I can't even use my mouse!

---

### Post by Jakiejake on 2010-05-22
I found this and supposedly
"Dig into this a bit more but I've read rumors of ATI driver issues in lucid...."
Well I got an ATI Card :(
Any Fix?

---

### Post by thomas_toscani on 2010-05-22
I'm having random freezing/lockups with Lucid as well.  I'm using a 64-bit Ubuntu 10.04.

Sometimes I can sort-of move my cursor up and down a little bit, but can't affect any actions.  Most of the time, though, the screen just locks up completely.  I can't drop out of X using control-alt-backspace either.  

Shame no one can suggest a solution.  This isn't an ATI problem, since I'm using an nVidia graphics card, but I suspect it might be an Xorg problem, since the frequency of freezing *appears *to have been reduced by disabling Xinerama.  Can't say for sure, though.

---

### Post by gotenks05 on 2010-09-09
Forgive me for posting to a possibly dead thread, but I found a possible solution, whether it is installable or not is questionable, since I am still doing things relating to it.  To get a Mac-compatible Lucid Installation medium, that works on an iMac5,1 and should work on later models, download a minimal install disc and run an installation in virtualization software. Next, configure it how you want (i.e. installing xorg, gnome, gdm, etc.).  Afterwards, add the respository for remastersys and create a Live CD/DVD (it helps if your Lucid VM or your current Ubuntu install has an FTP or samba server installed and active).  For the final step, test it out on the Mac (Note: it might not work on first time boot into the Live CD/DVD.  I had to hard reboot once into the LiveDVD before I saw a Desktop).  If everything works out, you will have a stable Lucid OS to install.  As I said before, I am working on creating my own live image and already verified that Lucid is definitely more stable through this method.

**Update:**  I got a working and installable image through the method.  If you want to try my configurations of Ubuntu, try the following.

[Ubuntu Mac Remaster]("http://www.filedropper.com/bryceubuntu")

---


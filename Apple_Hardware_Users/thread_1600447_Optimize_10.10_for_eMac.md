---
title: "Optimize 10.10 for eMac"
date: 2010-10-19
forum: Apple Hardware Users
---

### Post by thuntley on 2010-10-19
Ok, so, I snagged the 10.10 alternate install ISO for PPC and got it up and running on a 1ghz G4 eMac with 1gb of RAM and a 60gb HDD.  It runs... OK.  It could be a lot better.  I'm planning to shut off the bluetooth and CUPS services since neither apply to this system; are there any other services I can shut down, or any other tricks I could do to make it run a bit more smoothly?

What about alternate window managers?  I realise that the PPC platform kinda limits me, but what about TWM or FVWM?  Would those help?

---

### Post by linuxopjemac on 2010-10-19
go for LXDE.

---

### Post by thuntley on 2010-10-19
LXDE... *checks google*... yeah, ok, that could work.  Probably work really well.

So once I snag LXDE from the repos, how do I configure Ubuntu to use LXDE as its desktop instead of the "stock" desktop?  This machine is for my GF's kids, and I don't want them to have to choose LXDE each time they log in.  :)

---

### Post by linuxopjemac on 2010-10-19
```
sudo apt-get install lubuntu-desktop
```
at login screen choose lxde, then it asks to make it default, say yes.
easy as 1,2,3.

---

### Post by thuntley on 2010-10-19
Awesome, thanks.  I'll do this tonight.  :)

---

### Post by thuntley on 2010-10-20
Well, the command above didn't work because it depends on Chromium and Chromium, evidently, could not be installed.  I imagine that's because this is a PPC box.

I was able to snag lubuntu-core, the minimal installation, and that is a big improvement.  Sadly, flash via gnash is too slow to support all the Facebook flash games so I won't be giving it to my GF's kids.  

So what to do with a 1ghz PPC eMac running Ubuntu 10.10 with the lubuntu desktop core?

/rhetorical

Anyway, thanks for the help.  :)

---

### Post by linuxopjemac on 2010-10-20
Flash should be coming to powerpc. It's a matter of time.
[http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users](http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users)

---

### Post by avtolle on 2010-10-20
> **linuxopjemac said:**
> Flash should be coming to powerpc. It's a matter of time.
[http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users](http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users)

Uh, looks like it may be a long time, unfortunately. [https://answers.launchpad.net/lightspark/+question/127872](https://answers.launchpad.net/lightspark/+question/127872)

---

### Post by linuxopjemac on 2010-10-21
oops...big sigh..........

---


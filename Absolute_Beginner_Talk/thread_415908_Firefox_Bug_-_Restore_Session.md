---
title: "Firefox Bug - Restore Session?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-04-20
Greetings,

I just installed Ubuntu 7.04 and I'm having a very strange problem.  When I click on Firefox, every time I get the Restore Session dialogue before it loads.

If I click "Start New Session" and immediately click File > Quit and then open it again, I get the same dialogue!

If I click to Restore Session, same thing!

No matter what now, when I start Firefox I'm having that error.  I even tried removing firefox and completely reinstalling but I still have this problem.  Any way of "resetting" firefox so this doesn't happen?

Thanks in advance!

Chris Farrugia

---

### Post by Redache on 2007-04-20
It's something built into Firefox so that you can pick up where you left off from previous sessions. It will always do it if you don't close all open tabs. It can be a bit annoying but handy if you had a lot of pages up and it suddenly died on you :) 

It's nothing to worry about, and it's not a bug. I'm not sure if you can actually turn it off.

---

### Post by chrisf79 on 2007-04-20
Unfortunately, I have all tabs closed.  For example, the only Firefox window I have open at the moment is the one I'm typing this in.  No tabs open at all within this window.  Now, if I submit this post and then close this window, it'll happen again the very next time I click on Firefox!

It is nuts, I know :)

---

### Post by Redache on 2007-04-20
That is strange :confused: 

It might be worth looking into how to turn off the session restore, as I said I'm not sure where the option to kill it is but there must be one. 

It's thinking everything you do is wrong :lolflag:

---

### Post by jamespi on 2007-05-14
i have the same problem - i'm going to look on mozillazine to see if i can figure out the reason this is happening

---

### Post by Happy_Man on 2007-05-14
I would suggest deleting the .mozilla folder in your /home. That will erase all user settings (eg extensions), but it will also get rid of whatever is causing the dialog box.

---

### Post by MoxJet on 2007-05-14
I want to know how to disable restore session... I always get scared when I restore session and I'm logged on to various sites because of cookies. However, the worries doesn't last too long since I'm the only one who has physical access and passwords to this computer.

---

### Post by fataldata on 2007-06-25
Thanks,  Don't know what it was but this solution worked for me.  
> **Happy_Man said:**
> I would suggest deleting the .mozilla folder in your /home. That will erase all user settings (eg extensions), but it will also get rid of whatever is causing the dialog box.

---

### Post by SuperNatendo on 2007-06-25
I was having the same problem for the longest time, but I just ignored it, then, things got worse and worse!  everytime I started firefox instead of opening my home page which was still set to [www.google.com](www.google.com), it kept trying to open a site [www.%u.com](www.%u.com) which had nothing on it, but I could still hit the home button to get to google.  After a few more days finally, firefox would exit the instant it was started.  I had to uninstall mozilla in synaptic and reinstall before it worked again.

---

### Post by Songwind on 2007-06-25
To turn off this feature:

In a browser tab, enter "about:config" in the address bar.

In the "Filter" input box, put in "session"

Change he value of "browser.sessionstore.resume_from_crash" to false (double-click to change)

Restart Firefox to pick up the changes.

---

### Post by fataldata on 2007-06-27
The problem has returned.  I suspect after insalling flash player or something else.  I will try turning of the feature as Songwind suggessts> **fataldata said:**
> Thanks,  Don't know what it was but this solution worked for me.

---


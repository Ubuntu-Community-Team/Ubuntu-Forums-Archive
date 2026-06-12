---
title: "Problems shutting down Edgy--missing shutdown button"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-14
It doesn't look like Edgy likes me turning it off.

When I click the red power button on the top-right corner and the window pops up with the log off, hibernate, etc options, the 'Shutdown' option is conspicuously absent. I can still go to the terminal and type in the shutdown code from there, but that's a real bother and I shouldn't have to do that.

Any suggestions?

---

### Post by Hobo Joe on 2007-05-14
Was the session started through recovery mode?

---

### Post by zhinker on 2007-05-14
No, this is my regular session, and it's been this way for a few weeks now, it started just one or two days after I installed ubuntu.

---

### Post by JAPrufrock on 2007-05-14
You can add a quit button by right clicking on a panel.  A menu will pop up.  Click on add to panel.  You will find a quit button listed as one of the add-on options.  Add it to the panel and then move it to where you want.

---

### Post by zhinker on 2007-05-14
> **JAPrufrock said:**
> You can add a quit button by right clicking on a panel.  A menu will pop up.  Click on add to panel.  You will find a quit button listed as one of the add-on options.  Add it to the panel and then move it to where you want.

That didn't work, it just brings up the same screen as the default power off button, still lacking the shutdown option

---

### Post by jimrz on 2007-05-14
> **zhinker said:**
> That didn't work, it just brings up the same screen as the default power off button, still lacking the shutdown option

not sure how to get your option back but, from the terminal
```
sudo shutdown -P now
```
will shutdown your system and power it off

---

### Post by zhinker on 2007-05-14
yeah, that's what I'm doing right now but it's really annoying

---

### Post by JAPrufrock on 2007-05-15
Ok, my last idea.  Add a new panel to your desktop, say on the right hand side, and add a quit button to that panel, and see if the shutdown button is there.

---

### Post by zhinker on 2007-05-16
No go dude.  I found some packages in synaptic called 'wmshutdown' and 'hibernate' that I thought might solve the problem (my hibernate and sleep buttons were malfunctioning as well).  I haven't tried out the hibernate function yet but the sleep options seems to work fine now...except I still can't find that darned shutdown button.

---

### Post by finchair on 2007-06-10
Try this post if you haven't found the fix yet.

[http://ubuntuforums.org/showthread.php?t=429407&highlight=missing+shutdown+button](http://ubuntuforums.org/showthread.php?t=429407&highlight=missing+shutdown+button)

---

### Post by Bohlio on 2007-06-10
I dont have a shutdown button in there either. I just log out, then shutdown from the login screen. If you ever find out how to add it, post it up. But i dont see why its a huge problem, Just one more click for me.

---

### Post by kansei on 2007-07-06
So you don't have to dig through a few threads to get to the solution:

   1. From the top menu bar choose System
   2. Select the Administration menu option
   3. Then choose the Login Window menu option
   4. Enter your password when prompted
   5. Select the Local tab
   6. Check the box next to Show Actions Menu
   7. Make sure Include Host Names below it is checked as well

---


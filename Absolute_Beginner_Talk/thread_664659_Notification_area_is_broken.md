---
title: "Notification area is broken"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2008-01-11
This is a very annoying problem I have. Suddenly, my notification area becomes unresponsive, so I cannot access the programs there (I get the hand icon - for dragging things on the panel - instead). Right clicking on an icon gives me the right click menu for the whole applet. 

Any ideas? :(

---

### Post by Perpetual on 2008-01-11
> **Mazza558 said:**
> This is a very annoying problem I have. Suddenly, my notification area becomes unresponsive, so I cannot access the programs there (I get the hand icon - for dragging things on the panel - instead). Right clicking on an icon gives me the right click menu for the whole applet. 

Any ideas? :(

Just curious if you tried removing the applet and adding it back.

---

### Post by chewearn on 2008-01-14
I just got hit by exactly the same problem, while fooling around with a stupid howto on forwarding gnome via ssh.

The following **don't **solve the problem:
1. removing and putting back the notification area
2. putting bazillion notification areas, then delete them one by one
3. putting another notification area in another panel, delete the current notification area
4. create a few new panels, put notification areas in each one, delete the panels
5. etc etc

Finally, I hooked up a second monitor, set separate x sessions, remove all notification areas I can find in the second screen and the first screen.  Then switch to twinview, remove any more notification area I can find.  Then, add a single notification area, and the problem is finally solved.

---

### Post by chaosrl on 2008-01-25
AstalaVista, how would you recommend going about fixing it if I don't have access to another monitor? That said, could you also give a more detailed sort of step-by-step on how you fixed it? Mine's broken as well and I'm not sure how to do what you did. Thanks!

---

### Post by chewearn on 2008-01-26
> **chaosrl said:**
> AstalaVista, how would you recommend going about fixing it if I don't have access to another monitor? That said, could you also give a more detailed sort of step-by-step on how you fixed it? Mine's broken as well and I'm not sure how to do what you did. Thanks!

I can't give you a step-by-step, because there were so many things that I have tried, and I don't know exactly which steps solved it.

In fact, two days after it was solved, the problem came back again.  After some more fiddling around, I found that when creating a new user, the new user did not have this problem.  So, what I did next, I migrate all settings from current "broken" user to the new user.  This solve the problem for a few more days, but again, the new user got hit with the problem.

At this point, I am thinking it's between a reinstall or live with it.  I did find out yesterday, that if I restart xorg (CLRL+ALT+Backspace) once after log-in, the second log-in will not have this proble.  Since I don't restart my PC that often, I'm taking this workaround at the moment.

Sorry, I couldn't be more helpful.

---

### Post by chaosrl on 2008-01-26
Alright, thanks. Restarting X hasn't been working for me, I've just been getting by without using the notification area. I'm also trying to set up Trayer, but that's proven to be rather difficult to set up the way I want. But at least it works, :P

---

### Post by bobbob1016 on 2008-03-09
I'm having this issue on my Desktop and Laptop.  Just curious, you guys have AWN installed as well?  I found that by deleting everything gnome related hidden in my home folder, I was able to remedy this for a little while, then I got an error message asking if I wanted to delete the panel, I clicked no, since I was in a rush for something.

EDIT:  My Window List appears to be broken as well.  I can only select the first window in the list, the others are there, but I just get the hand grabbing again.

---

### Post by chewearn on 2008-03-09
The solution was found in another thread.

The problem is compiz freewins plug-ins; you have to disable the plug-ins to fix the problem.  Unfortunately, this means you lost the freewins functionalities.

---

### Post by bobbob1016 on 2008-03-10
Oh, ok.  Does that include the "Freely Transformable Windows" plugins plugin?  It's an offshoot of Freewins.  Now that I know what it is, I'll play with it, and see if I can get it working.  Thanks.

---

### Post by chewearn on 2008-03-10
Yes, that's the one.  Once you disabled it, the problem should go away.

---


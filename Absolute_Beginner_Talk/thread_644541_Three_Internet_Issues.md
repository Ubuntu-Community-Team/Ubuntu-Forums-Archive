---
title: "Three Internet Issues"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-19
Hey guys..Three new internet issues popped up and one non internet issue popped up while I tried to start a few things..

1.  When I boot up my machine i get the following "you passed a undefined mode number, if i hot spacebar, it boots though

2.  Opera says upon startup:  "it appears another opera instance is using the same config because the lock file is active, how do i fix this to use opera if i want?

3.  Firefox upon startup displays:KDEInit could not launch 'kgtk-wrapper'.:
Could not find 'kgtk-wrapper' executable.

Sorry for the posts, but im not sure where to go from here

---

### Post by Capricori on 2007-12-19
Hey Matt,

Your first question has been discussed a bit [here]("http://www.linuxquestions.org/questions/linux-newbie-8/you-passed-an-undefined-mode-number-124877/").
See if anything suggested in that thread fixes the issue.

Question 2: Did you force Opera to quit at some point? Make sure Opera isn't running, by typing 'killall opera' into a terminal. And then delete the lock file. The easiest way (for some) is to type 'rm ~/.opera/lock' into a terminal, or if you don't feel comfortable using random commands from the forum (and quite right too), use a file browser to navigate to your home folder, then make hidden files visible (in the browser options, somewhere). Go into the .opera folder, and delete the file called 'lock'

Question 3: Don't suppose you're using Kooldock? If so, try [this]("http://loscompanion.com/forums/index.php?topic=1787.0;msg=30292").

Let me know if any of that doesn't work and I'll see what else I can find :)

Regards, 

Capricori

---

### Post by sports fan Matt on 2007-12-19
Capri,

Thanks, I figured out issue three last night..Issue 2 i'll try in a few and will look at issue one in a minute and post back the results..had so much to do here for the holidays (packing for trips, etc, that I didnt have a shot to get back online and look)  

In looking at that page, im unsure how to get to that area (maybe its cause im a tad new to linux) im not sure where those settings are?  Could someone please help me locate them or how to get them?

---

### Post by sports fan Matt on 2007-12-19
Capri,

I tried deleting that lock file and rebooted and still Opera acts like it wants to open, it initilizes but doesnt open..Maybe I need to fresh install it?

---

### Post by Capricori on 2007-12-19
I'm not sure if reinstalling it is neccessary, but if you have things like bookmarks backed up, and you don't mind redo-ing the configuration, then you probably don't have much to lose :)

Sorry, but I was just leaving, it's some stupid time in the morning over here. I'll have a look at your problem in more detail when I wake up :)

Until then, if you can get onto IRC, try the #ubuntuforums-beginners channel. There's some good guys in there, know their stuff :)

Regards, 

Capricori

---

### Post by sports fan Matt on 2007-12-20
Last night I did attempt a reinstall to no avail of Opera, the file was still locked even after i deleted the lock file in the opera folder...Just providing an update on the steps ive taken...

---


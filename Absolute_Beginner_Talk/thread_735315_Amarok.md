---
title: "Amarok"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-25
When I click the icon for amarok. It loads about 1 min later? 

The harddrive doesn't go either in the 1 min delay? 
All my other applications open up when I click on them. Why does it take some time to load up?

---

### Post by smartboyathome on 2008-03-25
could be because it is trying to find the KDE resources, which doesn't have to make the HDD light light up.

---

### Post by herbster on 2008-03-25
Run amarok from the terminal and paste the output.

---

### Post by finer recliner on 2008-03-25
i assume you're using ubuntu (GNOME desktop environment). amarok was written to use many of the KDE libraries. so when you amarok for the first time, there are many other packages your computer has to load with it, which is probably why it takes a while to load up initially.

---

### Post by stchman on 2008-03-25
> **Tom--d said:**
> When I click the icon for amarok. It loads about 1 min later? 

The harddrive doesn't go either in the 1 min delay? 
All my other applications open up when I click on them. Why does it take some time to load up?

Yes, you need to load the KDE libraries at start up.  I can show you how.

[http://www.stchman.com/kde_fast.html](http://www.stchman.com/kde_fast.html)

Works for me.

---

### Post by Tom--d on 2008-03-25
> **stchman said:**
> Yes, you need to load the KDE libraries at start up.  I can show you how.

[http://www.stchman.com/kde_fast.html](http://www.stchman.com/kde_fast.html)

Works for me.

Thanks :)
Sounds promising :D

Just going to restart

---

### Post by Hospadar on 2008-03-25
Oop, that's the way to do it, never mind me


I've noticed amarok starting slow, but not that slow.

You might:
Make sure it hasn't started sooner, but is just sitting in the system tray with no window

Try starting it from a terminal and see if it gives any useful output to find out what it's hanging on

Try purging and re-installing amarok

---

### Post by Tomatz on 2008-03-25
I find preload speeds up apps alot. Especially kde apps if you use them often.

sudo apt-get install preload

---

### Post by Tom--d on 2008-03-25
When will the preload kick in?

---

### Post by Tomatz on 2008-03-25
It watches for library's you most use (eg kde libs) every 20 seconds and the ones you most use it loads into memory making the apps that use them start quicker :)

---


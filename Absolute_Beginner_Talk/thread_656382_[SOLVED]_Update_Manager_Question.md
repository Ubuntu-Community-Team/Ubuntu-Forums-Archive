---
title: "[SOLVED] Update Manager Question"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by jumboshrimp11 on 2008-01-02
So, I just recently in the past few weeks switched to using Ubuntu, and I was wondering- is it normal to not have any updates listed in the update manager since I installed it? It seems like there should have been some update or another in the time that I've been using it (approx. 3 weeks). 
So, is this normal, or do I have a problem?
Thank you!

---

### Post by philinux on 2008-01-02
Hi this is not normal unless you want to set it up that way.

Goto
System>Admin>Software Sources

Click the updates tab mine has two ticks for security and important and its set for daily update and only notify is checked.

---

### Post by Seisen on 2008-01-02
It depends on a number of factors, usually when you have a fresh install you have a lot of updates, at the beginning of the release of a new Ubuntu version there tend to be a lot of updates and after that updates tend to slow down. Also it depends on what applications you have installed, some might have more security updates etc....

I had a desktop I haven't used for four weeks and updated it last night and it only had 5 updates so.....

---

### Post by zipperback on 2008-01-02
> **jumboshrimp11 said:**
> So, I just recently in the past few weeks switched to using Ubuntu, and I was wondering- is it normal to not have any updates listed in the update manager since I installed it? It seems like there should have been some update or another in the time that I've been using it (approx. 3 weeks). 
So, is this normal, or do I have a problem?
Thank you!



Make sure you have your repositories active.

System -> Administration -> Synaptic Package Manager

This will start your package manager and prompt you for your password.

Now click Settings -> Repositories

Now go through each of the tabs and select the repositories that you want to get updates from.

Myself, I have them all checked, but some additional third party ones that I added later.

Click close.

Now click Reload at the top left corner of the application.

Now if you want to go ahead and just update all the available upgrades, click the icon at the top of the application that says "Mark All Upgrades", then click the "Apply" icon.

Then go ahead and install the updates.

Your update manager should be able to handle future updates for you, once you have the repositories active. Also, Synaptic Package Manager is a very useful application so that you can install additional packages that you might be interested in.

- zipperback
:popcorn:

---

### Post by TuxTech on 2008-01-02
Many helpful replies in this thread,as i was wondering the same thing. My Xubuntu desktop has numerous updates every week for various packages that i have installed, but my ubuntu notebook has had 1 in the past week since i installed it. Im going to try some of the tips in this thread and see if im missing anything.
   Thanks   :)

---

### Post by jumboshrimp11 on 2008-01-02
Ah, that's much better! Thank you all for your awesome advice! Now, I will spend the next year of my life downloading all the updates I've missed :(

---


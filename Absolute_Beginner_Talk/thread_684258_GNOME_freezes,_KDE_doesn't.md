---
title: "GNOME freezes, KDE doesn't"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by alphasurfari on 2008-01-31
The title says it all. GNOME will freeze up randomly. Immediately after login, or after an unpredictable amount of time up to hours and hours. Never triggered by any specific action. 

This started with Gutsy and continues in Hardy alpha 2 and 3 and Fedora 8 with GNOME. KDE does not have this problem in Kubuntu or Fedora 8 with KDE or Madriva 2008. 

My computer is a Dell Inspiron 600m. 

I want to run GNOME, not KDE! How can I even find out what is wrong?

---

### Post by SunnyRabbiera on 2008-01-31
yeh I know this issue well myself.
buy why use hardy though, if you are using it then certainly you can expect errors.

---

### Post by alphasurfari on 2008-01-31
I should mention that I was running Feisty before this without having any problems. The problems started in Gutsy (although not for some time after upgrading). I assumed that I must have applied an update to something which was now causing the crashes. I was hoping it would be fixed in Hardy and beyond.

---

### Post by SunnyRabbiera on 2008-01-31
well currently Hardy is not even in beta stage, its alpha quality right now.
My current suggestion is that if Feisty worked for you is if possible go back to it.
If you still have a install disk then back up your data and revert back...
If you dont well there isnt much I can suggest, except for possibly try a ubuntu fiesty derivative like linux mint

---

### Post by nick_h on 2008-02-01
Have you got Visual Effects enabled?  I had some random freezes with Visual Effects enabled in Gutsy.

---

### Post by alphasurfari on 2008-02-02
I did a clean install of Gutsy and did all the updates. It froze once during the updates, then ran fine for a few hours. This morning it froze once and then froze in the login screen after reboot. Does this mean it is something with the X server? How would I even troubleshoot this?

---

### Post by alphasurfari on 2008-02-06
No one? Still having this problem in Gutsy and openSUSE with gnome on the same machine. gnome freezes randomly. mouse frozen, keyboard unresponsive, screen locked. Have to hard reset.

---

### Post by yaknowwat on 2008-02-07
Do You have any desktop effects enable have you edited your Xorg.conf at all?
Do You have multiple monitors?
Do You have a Composite manager, Xgl ?
What what graphics card do you have?
Have drivers enabled ?


If it was the X server itself KDE would crash too, it seems to be that the newest GNOME might have something in it that is being used (possibly by special effects) that doesn't work with your drivers.

---

### Post by alphasurfari on 2008-02-07
I had all desktop effects off. The crashes persisted the same as before, so I tried turning them on to see if they would increase in frequency. It didn't make a difference.

The only edit I have made to my xorg.conf is to add Option "MaxTapTime" = "0" to disable my touchpad. I did this before and never had problems.

It's a laptop, no extra monitors.

I don't know what Xgl or a composite manager is. This is a fresh install of Gutsy, after running the update manager and applying all the updates (it crashed before the updates were applied as well though).

My graphics card is ATI RV250 Lf.

How do I enable drivers or see if they are enabled?

Thanks for your help!

---


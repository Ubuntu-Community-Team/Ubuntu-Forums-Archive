---
title: "Time/Clock Troubles"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-07-25
On my new [Dell Latitude L400]("http://www.mbhoy.com/21-07-2007/dell-latitude-l400-laptop"), never noticed this on the desktop...

Time is set to synchronize from local servers automatically. When syncing manually, it works well, with the time being perfect after sync, so I know the server time is right.

However, when I shutdown (on either setting), the clock seems to save the time of shutdown and use that at startup. So right now it says 3:45am when it's really some time after 1pm. 

Manually clicking "Synchronize Now" in time-admin solves this, but how do I stop it saving the time? Or make it sync on startup? 

- Matt

---

### Post by asmoore82 on 2007-07-25
is this machine dual-boot?

---

### Post by Old Pink on 2007-07-25
> **asmoore82 said:**
> is this machine dual-boot?No way, finished with other operating systems long, long ago. :)

---

### Post by edwardLS on 2007-07-25
I had a similar problem some time ago, and this forum provided an answer.  I am not sure it will help you, but I will pass it on for you to try.  I am not at my Ubuntu Desktop now, so I hope my memory can provide enough details.
In "/etc/default/" there is a file named "rcS"
If you edit that file (I think you need to use sudo) you should find an attribute 'UTC=yes'.  Changing that to 'UTC=no' fixed my problem with the time and clock.
Best of luck.

---

### Post by Old Pink on 2007-07-25
Right clicking the clock in GNOME Panel and clicking Preferences lets your enable/disable UTC. 

It's always been disabled.

---

### Post by edwardLS on 2007-07-26
I understand what you are saying, however.  I am using Dapper and you are using Feisty, so there may be a difference.  When I experienced the problem (in Dapper) I also used the preferences in the clock to play with the UTC enable/disable.  It did not solve my problem to which I requested help on these forums.  That is when I was told to edit the /etc/default/rcS file.  
At that time I was convinced that would not help, but I did use the preferences to enable and then disable the UTC and then checked the setting in /etc/default/rcS.  I found that the UTC parameter in /etc/default/rcS did not follow the setting by way of preferences in the clock.  So, I edit'ed the file as told, and I have not had clock problem since.

---

### Post by Old Pink on 2007-08-23
You're right, use UTC was disabled, yet it still said "UTC=yes" in that configuration file. I've changed it to no, and time will tell if that fixes anything. Thanks for the help, I'll update here often. :)

---


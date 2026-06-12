---
title: "is there something wrong with updates from Ubuntu?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Tzumli_D on 2006-12-09
Is something going wrong with the updates from Ubuntu?

After I entered my password to log into the gnome it was taking up to 3 minutes for the gui to come up with a message saying that there was an error starting the Gnome settings daemon.

After more than a week I got an update package yesterday morning which when I logged on again in the evening appeared to have fixed it because the gui opened immediately and there was no error message.

During my session last night I got another update, which just seemed to be gnome related 3 packages, and when I logged in this morning back to a 4 minute wait and the error message again. 

I had a look at the Ubuntu page, but must admit do not understand any of the recent news - eg is Ruby part of this problem?
Denise

---

### Post by riven0 on 2006-12-09
Do you remember exactly what the updates were? Perhaps there is a conflict.

---

### Post by Tzumli_D on 2006-12-09
No,I can't remember. I had alook at the explanations for the second one, as I said 3 for the Gnome, all by the same person. I thought it might be an additional tinker to fix something that was not quite perfect.
Denise

---

### Post by riven0 on 2006-12-09
I must say, I'm lost on this one. But it doesn't hurt to try this in the terminal:

sudo apt-get install --reinstall gnome-control-center-dev


Tell me if it works or not.

---

### Post by Tzumli_D on 2006-12-10
Thank you. Yes it seems to work. I restarted twice (ie without turning off the power) and the gui came up immediately.

Would this have had anything to do with the no network connection icon on my desktop? This is a standalone PC with broadband connection to the internet.
Denise

---

### Post by auburn on 2006-12-13
I had the same problem and the same error. The problem started to occur either Dec-13 or Dec-12. I can't remember now. The last aptitude update I did fixed it. The pkges that *seemed* to have fixed it were: automatix2, linux-image-2.6.17-10-386, linux-libc-dev. Attached is my aptitude log from the last few days. I've also wondered if it has anything to do with my networking. (I've been changing my settings around a lot the last few days and I have the NetworkManager installed.

---

### Post by auburn on 2006-12-14
the problem came back for me. It turned out it was a networking issue caused by a duplicate "auto eth0" in my /etc/network/interfaces file. But others are finding it's caused by other problems in networking config scripts. See this bug:
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381)

---


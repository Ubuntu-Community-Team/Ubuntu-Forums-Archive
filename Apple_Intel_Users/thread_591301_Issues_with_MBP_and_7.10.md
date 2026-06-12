---
title: "Issues with MBP and 7.10"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by Rempefiesta on 2007-10-25
I installed 7.10 on my 1st generation MacBookPro 17" on the day Gutsy was released and I'm really loving it.  There are just 2 small issues I'd like to try and find a solution to:

1st issue: When connecting to a wireless network with a WEP key, it doesn't let me connect properly.  I didn't install any wireless drivers since it worked right out of the box.  It works when the network is open, but not when it is secure.  I have searched for anything like this, but haven't see anyone else with this issue.

2nd issue: I've installed the ATI drivers on my MBP, but the desktop effects still won't turn on.  I've tried different things to try and turn them on, but all prove fruitless.  I'm not with my MBP now, but I believe it says: "Desktop effects could not be enabled". 

Any solutions on these 2 would be greatly appreciated.

---

### Post by cyberdork33 on 2007-10-25
> **Rempefiesta said:**
> 1st issue: When connecting to a wireless network with a WEP key, it doesn't let me connect properly.  I didn't install any wireless drivers since it worked right out of the box.  It works when the network is open, but not when it is secure.  I have searched for anything like this, but haven't see anyone else with this issue.

What exactly are you doing to connect?

> **Rempefiesta said:**
>  2nd issue: I've installed the ATI drivers on my MBP, but the desktop effects still won't turn on.  I've tried different things to try and turn them on, but all prove fruitless.  I'm not with my MBP now, but I believe it says: "Desktop effects could not be enabled".
The version of fglrx in the repos does not yet support compositing properly, and thus, you need XGL to provide that. You have two options:
1. sudo apt-get install xserver-xgl
2. install the very newest version of the driver (not yet in the repos) which can do compositing. (This has not out very long, and some are having trouble with it). You can check out this guide:
[http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/](http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/)

It says 64-bit, but the directions should be the same for 32bit (just get the right driver version to start with).

---

### Post by Rempefiesta on 2007-10-25
Well, I would click on the computer in the upper-right corner, select my WEP encrypted wireless network, then when it prompts me to type in my password, I would, then about a minute later, the password prompt screen would come back up.  During that time, I'm unable to view anything or use the Internet.

---

### Post by cyberdork33 on 2007-10-25
it sounds like it is not authenticating. can you try a different encryption type and see if that works?

---

### Post by Rempefiesta on 2007-10-26
Thank you very much for the link and information with the visual effects!  I was able to get mine up and running.  As for the wireless network, I'll work on that this weekend.

---


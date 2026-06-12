---
title: "&quot;Sorry, that didn't work.&quot; when logging in"
date: 2018-05-15
forum: Apple Hardware Users
---

### Post by colmars on 2018-05-15
I'm in the slightly unorthodox situation of running Ubuntu from an external USB device on a Macbook Air. It works great except for one problem.

Around half the time, when I attempt to login, I see the message "Sorry, that didn't work. Please try again." If I try and login again, I get an unusable blank screen as described in [this thread]("https://ubuntuforums.org/showthread.php?t=2390419&p=13766496#post13766496").  I have to try a few times before I can successfully log in, with a reboot each time.

I can't find anything to suggest what's going wrong or where I could look to see what's happening. Does anyone know why this message would be generated, and why it would be so non-deterministic?

---

### Post by PaulW2U on 2018-05-15
> **colmars said:**
> Does anyone know why this message would be generated, and why it would be so non-deterministic?
Isn't that message being generated as you have typed your password incorrectly? I often see those words when I inadvertently leave the caps lock on. I've just locked the screen and typed an obviously wrong password and saw that message followed by "Please try again."

I think your only issue here is the blank screen which although it has been reported elsewhere is not a problem here.

---

### Post by colmars on 2018-05-16
> **PaulW2U said:**
> Isn't that message being generated as you have typed your password incorrectly? I often see those words when I inadvertently leave the caps lock on. I've just locked the screen and typed an obviously wrong password and saw that message followed by "Please try again."

I think your only issue here is the blank screen which although it has been reported elsewhere is not a problem here.

Thanks for the response. No, it can't just be a typo in the password. Once I see "Sorry that didn't work", I'm guaranteed a blank screen the next time I login. If I don't see that message the first time, the window manager always seems to start correctly.

After a bit more experience, it seems after I get this message, I need to then login successfully, get the blank screen, reboot; then I will be able to login without issue. Something ends up in an inconsistent state somehow, and I have to go through this ritual to reset it. Very strange - not sure where to look.

---


---
title: "user/hostname problems"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by waggotamp on 2006-07-13
New to Ubuntu...

I cannot start the 'administrative programs' so, I cannot load updates or anything else. 

Can someone tell me in plain english what to do?

Thank you

running ubuntu on 3 machines - this laptop (acer) has the problem, I sign in as all other times, but it's not liking the hostname - I'm lost... help

---

### Post by falcon15500 on 2006-07-13
When you try to run an 'administrative program', what happens?  Are you asked for a password?  If so, enter your normal user password.

And with the laptop, what is wrong with the hostname?  What errors are you getting?  What _is_ the hostname? ;)

falc

---

### Post by waggotamp on 2006-07-14
Ok, I fixed the problem - 

Many thanks to the forums. 

Problem: 

Unable to upgrade/update the system because for some reason the hostname was not in sync with the host file. I was unable to open any program that required this 'administrative program' to launch.

Fix:

Restart in recovery mode and wait for the screen to stop scrolling with data. You will get a user@hostname # message. 

Then type: nano /etc/<hostname> The host name is the name you gave your computer in the setup. Or change it to your log in name like I did.

Then exit - with control key X  and then a Y, then type EXIT. This will boot the system into your normal version of Ubuntu. 

Then type: nano /etc/<hosts> The host name is the same name you gave your hostname above setup. 

Then exit - with control key X  and then a Y, then type EXIT. This will boot the system into your normal version of Ubuntu. 

You should find that now when you want to upgrade Ubuntu or just go into any administration area you will be asked for the password again.

Ubuntu - Thank you.

---


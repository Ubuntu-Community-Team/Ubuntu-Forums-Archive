---
title: "How to kill the update reminder?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by anaconda on 2006-06-12
Every time I boot my computer there comes the 
"there are new updates for your computer"(or similar) -flag on the top right corner of ubuntu

I hate it... reminds me of windows. I prefer updating the computer every few months or so.. not every day.

How can I disable it? (forever)

---

### Post by phido on 2006-06-12
System > Preferences > Sessions
Disable update-notifier in Startup Programs

---

### Post by anaconda on 2006-06-12
Thanks.

That was fast!   :D

---

### Post by Nikusan on 2006-06-12
Running for extended periods of time without patches would remind of windows more than an update notifier in the notfication area.

---

### Post by anaconda on 2006-06-12
Really?
I thought that linux/ubuntu is quite safe even vithout downloading updates every month..

Am I wrong?

Do you think that hadware firewall makes it safer to not download all updates?

---

### Post by Sef on 2006-06-12
> I thought that linux/ubuntu is quite safe even vithout downloading updates every month..

Updates make your system more secure.   If updates are not installed, then your system is vulnerable to attack through a known flaw.

> Do you think that hadware firewall makes it safer to not download all updates?

A firewall and updates are safer than just a firewall.

---

### Post by mostwanted on 2006-06-12
[QUOTE=phido]System > Preferences > Sessions
Disable update-notifier in Startup Programs[/QUOTE]

That's not a very *clean* way to do it.

The more clean way is to open up System &#8594; Administration &#8594; Software Settings (or whatever it's called in English), hit the second tab and uncheck the "Automatically check for updates" option.

---

### Post by nocturn on 2006-06-12
I cannot imagine why you would want to turn this off...

Patch management is an essential part of security and something that windows got very wrong (yes, you have windows-update, but it will only check for updates to windows and office, not other apps on your system).

Dapper only gets security or very critical updates, so it shouldn't cause you any functional problems...

---


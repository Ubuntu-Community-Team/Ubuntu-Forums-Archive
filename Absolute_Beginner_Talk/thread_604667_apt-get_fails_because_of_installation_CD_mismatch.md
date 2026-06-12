---
title: "apt-get fails because of installation CD mismatch"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by paradisebmk on 2007-11-06
Hi,

I am attempting to use apt-get.

Everthing appears to go well  thru the space prompt. I get a message to mount the installation disk (it specifies the label) but the label on my installation CD does exactly match the prompt so it keeps asking me to mount the installation CD.

The actual label is pretty much the same as the prompt but NOT an exact match.

When I burn CD from the dowloaded ISO (using NERO) I don't have any control over what the CD label will be (at least no way I've found). I guess it comes from the ISO itself.

Anyone know a workaround? A way to force it to use the CD I provide or maybe a way to direct apt-get to download instead of using the CD?


This is probably a no brainer to someone with more experience with Linux. Thanks (in advance) for your time and response.

---

### Post by irw on 2007-11-06
Go to System/Administration/Software sources  or sudo edit /etc/apt/sources.list and remove the cd-rom from the list.

It will then just look at the internet sources only and not ask for the CD

---

### Post by paradisebmk on 2007-11-06
Thank you for your response. I'll try it tonight.

---


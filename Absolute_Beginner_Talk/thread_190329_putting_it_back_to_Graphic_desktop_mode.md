---
title: "putting it back to Graphic desktop mode"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Sambie on 2006-06-06
I admit that I've been running windows for over a month now because I've been frustratedtowards Kubuntu, of which now I've got myself more educated. I do not know what I did wrong but now when I try to startup Kubuntu on restart it starts up on text mode. I want to put it back onto graphic mode… Does anybody happen to know how on text mode?

---

### Post by r4ik on 2006-06-06
From the command-line type youre usrname and passwrd hit enter.
Do a,

sudo dpkg-reconfigure xserver-xorg and hit enter,

just follow the defaults until you get to youre grapics card section select "nv" for Nvidia or "vesa" (ATI)

continue and finish with,

sudo /etc/init.d/gdm stop =>enter

sudo /etc/init.d/gdm start =>enter

Good luck !

---


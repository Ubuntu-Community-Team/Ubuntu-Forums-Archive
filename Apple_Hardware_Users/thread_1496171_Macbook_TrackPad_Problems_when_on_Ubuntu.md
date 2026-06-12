---
title: "Macbook TrackPad Problems when on Ubuntu"
date: 2010-05-28
forum: Apple Hardware Users
---

### Post by Singlish on 2010-05-28
I'm a new user, running on a MacBook, on Ubuntu.
My version, according to System> About Ubuntu, is 10.04 LTS - the Lucid Lynx.

When i use the trackpad, it doesn't respond very well. I need to use a lot of pressure to actually get the mouse moving. 

If normal pressure is applied, the mouse will either not move at all, or move a little, then stop when even a *little* pressure is released.

I did some googling, and found some brief mentions of software, but not enough to figure out what to do.
There was also this site, which had some code. The comments on it seems to be rather positive, but **i have no idea where to input it into. **I appreciate any help i can get on this problem

---

### Post by linuxopjemac on 2010-05-29
Install gsnyaptics. You can set the sensitivity there:

```
sudo apt-get install gsnyaptics
```

Then go to System -> Preferences -> Touchpad

---

### Post by Singlish on 2010-05-29
> **linuxopjemac said:**
> Install gsnyaptics. You can set the sensitivity there:

```
sudo apt-get install gsnyaptics
```

Then go to System -> Preferences -> Touchpad

Thanks for your help! Though i was unable to install it via terminal,
[SIZE="3"]singlish@Singlish-Linux:~$ sudo apt-get install gsnyaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gsnyaptics
singlish@Singlish-Linux:~$ 

[/SIZE]

i was able to find it through the Software center.

Once again, Thank you. Popcorn for you, sir. :popcorn:

---

### Post by linuxopjemac on 2010-05-29
I made a mistake, if you look well you will see what I mean ;)

gsynaptics instead of gsnyaptics

---


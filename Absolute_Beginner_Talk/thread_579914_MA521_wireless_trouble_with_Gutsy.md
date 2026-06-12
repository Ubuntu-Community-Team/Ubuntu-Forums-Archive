---
title: "MA521 wireless trouble with Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ovitz on 2007-10-18
HI there. I set up my Netgear wireless card on 7.04 using this wonderful guide...
[http://ubuntuforums.org/showthread.php?t=19978](http://ubuntuforums.org/showthread.php?t=19978)

However, now that I have updated to Gutsy, the wireless card freezes up the laptop when inserted. In order to get it to work, I have to remove the driver from ndiswrapper, and then install it again. Then the card will work when inserted.

Is it trying to use a different (non-ndiswrapper) driver, because even without the driver loaded, the tries to connect to a network and freezes?

Any help is greatly appreciated.

This is the first time I have tried Linux in years, and i am loving Ubuntu!

---

### Post by ovitz on 2007-10-18
With 7.04, my wireless card was not detected at all. Now, when I've removed ndiswrapper... my card is detected and it tries to connect to a network, at which point the whole thing freezes. 

What is running that's new to cause this, and how do I remove it? Thanks!

---

### Post by ovitz on 2007-10-19
I'm really getting frustrated. Any help is appreciated!

---

### Post by Monsuco on 2007-10-19
I have the same problem, Do you guys use WEP encrypted networks, because I think I got it to work on my school WiFi network which is unencrypted, but my encrypted home network causes it to crash. How do I downgrade to the old version or prevent NDISWrapper from doing this. This is horrible!

---

### Post by ovitz on 2007-10-20
> **Monsuco said:**
> I have the same problem, Do you guys use WEP encrypted networks, because I think I got it to work on my school WiFi network which is unencrypted, but my encrypted home network causes it to crash. How do I downgrade to the old version or prevent NDISWrapper from doing this. This is horrible!

My network has WEP, yes. Let me turn it off and see if it works.

EDIT: Yup. Works find without WEP enabled. Fixes?

---

### Post by ovitz on 2007-10-20
Just tried a fresh install. No ndiswrapper. Detects, but freezes with WEP. Any help here?

---

### Post by ovitz on 2007-10-20
Screw it. I'm going back to 7.04. Having too many issues here.

---

### Post by cjgwhite on 2007-10-23
Assuming your MA521 uses the rt8180 driver, then the problem is with the default supplied kernel driver.

I solved the problem by, in a terminal type...

sudo gedit /etc/modprobe.d/blacklist

... (use kedit if you are using kubuntu) and add the following to the end of the file

#causes the system to freeze
blacklist rt8180

... then save the file. 

Next follow the instructions for installing the driver through ndiswrapper as linked too in the initial post.

This sorted the whole problem out for me. No more freezes. wireless works a charm

AND WEP works fine too!!!

Chris.

---

### Post by plata77 on 2007-10-25
I  had the same problem and found this thread. It actually worked, but the driver's name is r8180 - so the blacklist should look like that:

#causes the system to freeze
blacklist r8180

Plata

---

### Post by ovitz on 2007-11-14
Thank you for the replys. I will try this asap!

---

### Post by eabhi on 2007-12-23
Hey this is great.

This worked for my Netgear MA521 Wireless Card. But as already mentioned above, the card uses the driver r8180. You'll come to know about this by the output of the command

$ndiswrapper -l

I had actually given up on Ubuntu. My Netgear didn't work in 7.04 nor in 7.10, :( though it use to work till 6.10 "out of the box". This should be supported out of the box :)

Good work!!!

--Update: This works amazing for the 1st time, but when I restarted, my Netgear Wireless Card itself is not getting detected.

1. If I remove the blacklist line, then the Card gets detected, but freezes when I connect to my WEP Enabled WiFi Network :(
2. If I keep the blacklist entry, then the Wireless Card doesn't get detected at all :(

Does anyone knows the solution of this problem!!! 

eabhi

> **cjgwhite said:**
> Assuming your MA521 uses the rt8180 driver, then the problem is with the default supplied kernel driver.

I solved the problem by, in a terminal type...

sudo gedit /etc/modprobe.d/blacklist

... (use kedit if you are using kubuntu) and add the following to the end of the file

#causes the system to freeze
blacklist rt8180

... then save the file. 

Next follow the instructions for installing the driver through ndiswrapper as linked too in the initial post.

This sorted the whole problem out for me. No more freezes. wireless works a charm

AND WEP works fine too!!!

Chris.

---

### Post by berralac on 2008-02-15
i keep getting net8180 invalid driver!  I am in desperate need of assistance.

---

### Post by arnabt on 2008-02-18
If I blacklist as suggested my card is not detected anymore. Please help me if anyone has fixed the problem.

---


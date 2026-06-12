---
title: "Need Help Macbook 6,2"
date: 2010-11-11
forum: Apple Hardware Users
---

### Post by kjiang on 2010-11-11
Hey,

I just installed Ubuntu on my Macbook 6,2 and I have a bunch of questions.

So I'm trying to get all my drivers installed and working by following "MacBookPro6-2Lucid" in community documentation.

I installed alsamixer because I read I could unmute my speakers with it. I tried and I set the value of "Front Sp" to 9 but there still is no sound.

Also, whenever I shut my laptop and reopen it I get some error and then it powers down. 

I'm also trying to install the brodcom STA wireless drivers but I'm getting no luck there either.

---

### Post by blueridgedog on 2010-11-12
> **kjiang said:**
> 
I installed alsamixer because I read I could unmute my speakers with it. I tried and I set the value of "Front Sp" to 9 but there still is no sound.


Run alsamixer, select the front speakers, press "M" to mute or unmute (if MM is displayed, it is muted).

---

### Post by kjiang on 2010-11-12
Wow I'm stupid. Thanks, haha

---

### Post by blueridgedog on 2010-11-13
Dont feel bad.  I too turned up the volume and was stumped as to why it still didn't work...I finally had to read the alsamixer docs to understand what MM meant.

---

### Post by itismike on 2010-11-14
> **kjiang said:**
> ...Also, whenever I shut my laptop and reopen it I get some error and then it powers down.
Never saw this behavior. Double-check your power settings under System > Preferences > Power Management.

> I'm also trying to install the brodcom STA wireless drivers but I'm getting no luck there either.
The drivers will offer to be installed automatically once you perform an update. Plug it into an Ethernet jack, perform an update, then reboot. You should see a notice by the clock to enable restricted drivers. If not, look under System > Administration > Additional Drivers.

---

### Post by kjiang on 2010-11-14
> **itismike said:**
> Never saw this behavior. Double-check your power settings under System > Preferences > Power Management.

What should I set it to do when I close my laptop? I think I have it on Hibernate right now. 

When I close and reopen it I get 4 or 5 error message saying something like, "ata2:1 failed to resume link"

---

### Post by itismike on 2010-11-14
> **kjiang said:**
> What should I set it to do when I close my laptop
Only you know the answer to this. :)
Mine is set to suspend, and I'm happy with it. Hibernation is sometimes tricky to get working. But if you're closing and opening the laptop within a few seconds, this could be why hibernate is failing. It is less-than graceful in my experience, and asking it to stop hibernating in the middle of a hibernation is particularly troublesome. Either let it sit closed until you hear the hard drive shut off, or set it to "turn off display" or "suspend" and see if that makes a difference. You could also set it to 'do nothing', but that's not very energy-conscious.

---

### Post by dobe2049 on 2010-11-15
I have the same Mac and my speakers still don't work even after unmuting in alsamixer.

---

### Post by dobe2049 on 2010-11-15
> **dobe2049 said:**
> I have the same Mac and my speakers still don't work even after unmuting in alsamixer.

Nevermind I figured it out. Just needed to read some more.

---


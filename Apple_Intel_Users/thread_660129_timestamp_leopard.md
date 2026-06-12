---
title: "timestamp leopard"
date: 2008-01-06
forum: Apple Intel Users
---

### Post by p0rtlandcubsfan on 2008-01-06
I am running a dual boot on my second-gen macbook using rEFIt, Gutsy and Leopard and I can't seem to reconcile the timestamps between OSX.5 and Ubuntu 7.10.  In other words, when I correct the time in Leopard it makes the time in Gutsy wrong, and vice versa.  Anybody got a fix, or know where I might look for one?

---

### Post by cyberdork33 on 2008-01-07
> **p0rtlandcubsfan said:**
> I am running a dual boot on my second-gen macbook using rEFIt, Gutsy and Leopard and I can't seem to reconcile the timestamps between OSX.5 and Ubuntu 7.10. In other words, when I correct the time in Leopard it makes the time in Gutsy wrong, and vice versa. Anybody got a fix, or know where I might look for one?

I would say that your timezone offset is incorrect or something... check that the timezone settings are correct in both OS installs. This is something that should not be an issue in Ubuntu.

---

### Post by p0rtlandcubsfan on 2008-01-07
> **cyberdork33 said:**
> I would say that your timezone offset is incorrect or something... check that the timezone settings are correct in both OS installs. This is something that should not be an issue in Ubuntu.
I checked the timezones, and if the timezone is correct in leopard it is wrong in gutsy.  if its correct in gutsy its wrong in leopard.  when I correct it in one it makes it wrong in the other.  if there's nothing I can do, then ok whatever I can just set it to be right in the OS I use more.  I'm just wondering if there is any way to reconcile one with the other.  Like I said, every time I try to do this it changes in both

---

### Post by cyberdork33 on 2008-01-07
> **p0rtlandcubsfan said:**
> I checked the timezones, and if the timezone is correct in leopard it is wrong in gutsy.  if its correct in gutsy its wrong in leopard.  when I correct it in one it makes it wrong in the other.  if there's nothing I can do, then ok whatever I can just set it to be right in the OS I use more.  I'm just wondering if there is any way to reconcile one with the other.  Like I said, every time I try to do this it changes in both

I was not talking about changing the time... you will get this problem if the offset is wrong, because the time is stored in a hardware clock, to which the offset is applied. This offset can be 0 if your hardware clock is set to the local time, or, as is the standard case in linux / unix, the hardware clock is set to UTC/GMT, and the offset applied by the operating system (i.e. the timezone). 

In Oregon, you are on Pacific time, so if you set the time zone to Pacific, and make sure the local time is correct in one OS, then setting the timezone to Pacific in the other OS should yield the same result, I am not sure what to tell you if you are getting a different result in each. Changing the set timezone in one should have no effect on the set timezone of the other, nor would I begin to be able to explain how one would affect the other.

The changing time issue is usually a problem when dual booting a machine with windows, as it like the hardware clock set to the local time.

---

### Post by p0rtlandcubsfan on 2008-01-07
Ok, now I understand what you are talking about.  Now, I see you are running a Dell and I understand that the process for changing the offset is likely to be different between our computers.  That said, is there anything you can tell me about how to find out if the time offset is indeed the issue and if it is, to fix it?  If not, thanks anyways.  You've been most helpful.

---

### Post by cyberdork33 on 2008-01-07
> **p0rtlandcubsfan said:**
> Ok, now I understand what you are talking about.  Now, I see you are running a Dell and I understand that the process for changing the offset is likely to be different between our computers.  That said, is there anything you can tell me about how to find out if the time offset is indeed the issue and if it is, to fix it?  If not, thanks anyways.  You've been most helpful.
I do have a Dell, but I also have an iMac...

What I am getting at is that if you just change the set time in either, it will of course affect the other OS, you need to check that both the time and timezone is set correctly in both at once.

I guess you could just choose another timezone for Ubuntu that makes the time appear correct (setting the timezone is essentially, just altering the time offset from UTC... EST = -5, CST = -6, etc), This is not a perfect fix, but should get your time to display right in both systems. For example, If I have everything set correctly, and my time is still 2 hours off from my normal central time, then I might try setting the timezone to pacific or atlantic to compensate for the error.

---

### Post by p0rtlandcubsfan on 2008-01-07
thanks a bunch, I think that will suffice until I figure something else out.  You are very kind for helping me, I'm sure you're just as busy as I am and I want to thank you for taking time out of your day to even think about this.

---

### Post by cyberdork33 on 2008-01-07
no problem. Just like to help.

---

### Post by cyberdork33 on 2008-01-07
ran across this, don't know if it will help:
```
sudo dpkg-reconfigure tzdata
```

---

### Post by Discerptor on 2008-06-13
Out of curiosity, did you formerly have a Windows install in the partition you installed Ubuntu in?

Actually, I have a possible solution for you- a friend of mine had a similar problem recently, and this definitely works.

Install rclock from the repositories (sudo apt-get install rclock).

Login as super user with the command **sudo -i**

Pick the time server that works for you and type in Terminal

**rclock [server]**

(Replace [server] with what it actually is; in my case, I used time.nrc.ca.)

If it reports the correct time (as it should), follow up with the command

**hwclock**

That should set your clock correctly. Type **exit** to leave the super user shell, and you're done.

I'm not sure how this will affect the OS X partition, though... get back to me on how this goes.

---


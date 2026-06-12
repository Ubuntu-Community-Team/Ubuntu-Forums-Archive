---
title: "time sync program"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-04-10
Is there a program for Ubuntu 5.10 there will perform the same function that the Atomic Time Pro does for Windows based systems, i.e. sync the computers time clock to the national standard time at set intervals ?

Thanks.

---

### Post by sYs^ on 2006-04-10
System -> Administration -> Time and Date 

You will find that you're looking for :>

Edit: I'm using 6.06 but I think in 5.10 is an option like this too.

---

### Post by wpshooter on 2006-04-10
What is 6.06, I thought 5.10 was the latest version ?

I installed all of the updates (I think about 77 of them that came up when the installation finished).  Does that bring me up to 6.06 or is that something else, a beta perhaps ?

Thanks.

---

### Post by sYs^ on 2006-04-10
Yup, it's named "Dapper Drake", it's *Development Release*. It'll be the next release after Breezy Badger.

Some further informations:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/DapperDrake](https://wiki.ubuntu.com/DapperDrake)

---

### Post by wpshooter on 2006-04-10
When this is ready for final release, will this be an update to the 5.10 version via internet or is this something that will require a complete re-installation or some other process ?

Thanks.

---

### Post by christhemonkey on 2006-04-10
You can update to dapper drake now, search in the wiki for a howto.
wiki.ubuntu.com

But as for time syncing, i thought that at everyboot up, pcs sync their clock with ntp.ubuntu.com?

---

### Post by wpshooter on 2006-04-10
Yes, come to think of it, you are correct, I have noticed that time sync on bootup.  But I would like to sync on a regular basis during loooooooong uptime/sessions.

---

### Post by christhemonkey on 2006-04-10
```
sudo /etc/init.d/ntpdate restart
```
Synchronises the clock, as in boot up.

---

### Post by sYs^ on 2006-04-10
[QUOTE=christhemonkey]```
sudo /etc/init.d/ntpdate restart
```
Synchronises the clock, as in boot up.[/QUOTE]

Imho you could add this to crontab.

---


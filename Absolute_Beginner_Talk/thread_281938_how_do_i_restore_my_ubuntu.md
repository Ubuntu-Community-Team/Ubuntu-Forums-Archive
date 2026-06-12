---
title: "how do i restore my ubuntu ?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by InfectedJ11 on 2006-10-21
wait i messed up my system and now i was wondering if you could restore your ubuntu back in =hours or days like you do in windows....help please...:(

---

### Post by meng on 2006-10-21
Going to need to know more information than that - how did you mess it up, what is the problem now, and do you have any data on separate partitions, e.g. a separate /home partition?

We're not mind readers here.

---

### Post by InfectedJ11 on 2006-10-21
well when i go to the automatix, add/remove or synaptic package manager i get this message...[IMG]http://img221.imageshack.us/img221/377/screenshotml6.png[/IMG]

---

### Post by meng on 2006-10-21
If this is the only problem, this is not a mess up of your system at all, merely a failure to authenticate the getautomatix repository with a GPG key. I don't know how to solve the problem, but it shouldn't cause any other problems with your system.

If you don't need automatix any more, the easiest solution would be to drop to the command line,

gksu gedit /etc/apt/sources.list

and place a # sign in front of the line containing the text "www.getautomatix.com" (I assume such a line exists, I don't use or advocate the use of automatix.)
then save the file and (again from command line)

sudo aptitude update

DO NOT REINSTALL UBUNTU! This is unnecessary (see how important it is to explain your problem?)

---

### Post by InfectedJ11 on 2006-10-21
well now how do i removed this problem 


[IMG]http://img80.imageshack.us/img80/57/screenshotev4.png[/IMG]

---

### Post by meng on 2006-10-21
Wow - what did you do? (I can see the terminal output behind the dialog, something must have happened, did you do that or was it automatix?)

---

### Post by InfectedJ11 on 2006-10-21
> **meng said:**
> Wow - what did you do? (I can see the terminal output behind the dialog, something must have happened, did you do that or was it automatix?)

no man i dont know it just came after i did the thing for automatix i dont have no idea man....do you know?

---

### Post by Dual Cortex on 2006-10-21
> **meng said:**
> Wow - what did you do? (I can see the terminal output behind the dialog, something must have happened, did you do that or was it automatix?)

???? That always shows up!

Anyway, it's just an error with your sources.list, but no biggie. I dont really know how to solve your problem but I know somebody else will (i'm just a 3 week old noob)

---

### Post by InfectedJ11 on 2006-10-21
> **Dual Cortex said:**
> ???? That always shows up!

Anyway, it's just an error with your sources.list, but no biggie. I dont really know how to solve your problem but I know somebody else will (i'm just a 3 week old noob)

me im just a week noob in ubuntu but a master in windows and FreeBSD and h0x0r :cool:

---

### Post by meng on 2006-10-21
Aha this must be what people talk about when they say that Automatix can "break your system". Have you tried the forums at getautomatix.com? I don't want to discourage you from seeking help in these forums, but the maker of automatix doesn't much like this place, for his own personal reasons.

Otherwise, IF you have no critical data on your system, you can overwrite your install of Ubuntu with a fresh install and start over. Depending on what you want Automatix to install for you (e.g. video codecs, multimedia players, java, flash, Adobe reader), you can actually do this all manually with fairly little investment of time. There are lots of wikis here that explain how to do it using the official Ubuntu repositories.

If you want to persist with Automatix, then all the best of luck to you. And I'm sorry I couldn't be more helpful, I just do things the "old-fashioned" way (that works).

---

### Post by InfectedJ11 on 2006-10-21
> **meng said:**
> Aha this must be what people talk about when they say that Automatix can "break your system". Have you tried the forums at getautomatix.com? I don't want to discourage you from seeking help in these forums, but the maker of automatix doesn't much like this place, for his own personal reasons.

Otherwise, IF you have no critical data on your system, you can overwrite your install of Ubuntu with a fresh install and start over. Depending on what you want Automatix to install for you (e.g. video codecs, multimedia players, java, flash, Adobe reader), you can actually do this all manually with fairly little investment of time. There are lots of wikis here that explain how to do it using the official Ubuntu repositories.

If you want to persist with Automatix, then all the best of luck to you. And I'm sorry I couldn't be more helpful, I just do things the "old-fashioned" way (that works).

thanks man but i think there is a way to fix this small bug...damn

---

### Post by junglepeanut on 2006-10-22
Quick google search pulled up

[https://launchpad.net/distros/ubuntu/+ticket/2012](https://launchpad.net/distros/ubuntu/+ticket/2012)

The first link very concisely says ->

sudo apt-get remove clvm -f --purge

and says if that does not work go to this second link 

[http://ubuntuforums.org/showthread.php?t=186356](http://ubuntuforums.org/showthread.php?t=186356)

and do what it says at the bottom.

Hope this helps.

---

### Post by arnieboy on 2006-10-22
just a small note folks.. before people get too excited and and reinstall dapper.
The release key in the AX dapper repositories was broken and it was causing this error (quite trivial). The release key has since been updated and fixed
Simply do a 
```
sudo apt-get update
```
and everything will be fine.

---


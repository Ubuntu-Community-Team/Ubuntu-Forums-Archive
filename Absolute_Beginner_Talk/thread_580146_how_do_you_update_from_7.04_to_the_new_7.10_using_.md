---
title: "how do you update from 7.04 to the new 7.10 using the cd?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by chaoswings on 2007-10-18
how do you update from 7.04 to the new 7.10 using the cd?


I downloaded the new ubuntu iso how do I use it to upgrade my current version?

If i go to update manager it wants to download things from the internet....is there anyway i can use the cd to upgrade without having to download anything?


besides a fresh install of course...that's a last resort

---

### Post by onelife151 on 2007-10-18
I am pretty sure you should be able to uncomment the line from your sources.list that listed the cdrom. Pop that disk in and do an apt-get update and it should be able to read the new packages off the cd. bare in mind if you installed any packages from other repositories you will need to be care full with that and possibly change the links in your sources.list from edgy to gutsy and hope it doesn't blow up in your face. Hope this helps some. Feel free to comment back if you have any questions!

---

### Post by chuckyp on 2007-10-18
Use the apt-cdrom command.  You can type in man apt-cdrom in terminal to get more info on its usage.

---


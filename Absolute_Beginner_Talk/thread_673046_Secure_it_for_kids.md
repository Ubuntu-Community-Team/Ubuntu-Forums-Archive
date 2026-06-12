---
title: "Secure it for kids"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by novellred on 2008-01-20
I have an account on this Ubuntu machine for my kids, and I would like to be able to lock it down so that they can't get into certain applications / areas, and can only use Firefox in Safe Mode - things like that.

How do I accomplish this?

Thank you.

---

### Post by Mud.Knee.Havoc on 2008-01-20
Not exactly what you're asking for, but here's something else you might like to look into for a kids' machine: change your DNS settings to the ones listed at ScrubIT.com (67.138.54.100 and 207.225.209.66)

ScrubIT will filter out malicious sites/porn/etc.

In terms of allowing them to use certain applications and areas, you might want to create a group called "kids" or something like that.  Give members of this group access only to those applications/areas that you want.

---

### Post by Malta paul on 2008-01-20
Hi, You can create a separate account for them with limitations,
System>Administrator> Users and groups  ' Add a user'.
There is a video at [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) that may help you.
Have fun:)

---

### Post by Rhubarb on 2008-01-20
**pessulus** could be the answer you're after, it's in the ubuntu repositories.
Also remove items (such as the terminal) from the applications menu) System --> Preferences --> Main Menu.
You could change the permissions on some files in their home folder, make them read only / change the ownership of them.

I'm sure there's more steps you could do, it's just an internet search away.

---

### Post by billgoldberg on 2008-01-20
Changing the /etc/hosts file to ban certain websites can help.

Or take a look at this firefox add-on (goes without saying they shouldn't have any others browsers installed). [http://www.glubble.com/index.php](http://www.glubble.com/index.php)

---

### Post by novellred on 2008-01-20
Thanks!

I changed the DNS settings, but can't seem to do anything with the Group Properties but to add members.  What am I doing wrong?

Thanks again!

---


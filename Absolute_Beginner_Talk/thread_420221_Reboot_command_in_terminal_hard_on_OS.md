---
title: "Reboot command in terminal hard on OS?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by adampyre on 2007-04-23
Hi,

I have gDesklets and I am using it's launcher dock. I created a launcher that points to a text file that I made executable. Within the executable file I placed the line:

sudo reboot; (my password)

I did this so I had a quick and easy way of restarting the system/shutting it down. 

So, I guess my question in a nutshell is:

Is it hard on the OS to use the reboot command in bash when Gnome is running?

Thanks!

---

### Post by Cypher on 2007-04-23
Nope..the reboot should work fine..

Regards

---

### Post by Pobega on 2007-04-23
It should work fine.

What you could do is make is so that you don't need a password to shutdown, so put something like this in /etc/sudoers (I use it myself and it works fine):

pobega  ALL=NOPASSWD: /sbin/reboot

And then just use "sudo reboot" in your script. Things like this is why reading the sudoers man page is very useful :D

---

### Post by adampyre on 2007-04-23
Thanks for the responses!

---

### Post by brennydoogles on 2007-04-23
> **Pobega said:**
> It should work fine.

What you could do is make is so that you don't need a password to shutdown, so put something like this in /etc/sudoers (I use it myself and it works fine):

pobega  ALL=NOPASSWD: /sbin/reboot

And then just use "sudo reboot" in your script. Things like this is why reading the sudoers man page is very useful :D

So explain this more if you don't mind... You can set certain sudo commands to not require that password from Administrator accounts?? Could it be applied to aliases as well?? That could save me a bunch of time!!

---


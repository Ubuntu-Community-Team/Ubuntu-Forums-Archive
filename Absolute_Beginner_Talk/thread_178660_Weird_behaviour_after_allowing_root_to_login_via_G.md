---
title: "Weird behaviour after allowing root to login via GDM"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-05-18
I changed the randomly generated password of root to something I could remember. Then I allowed root to login in GNOME. Then I logged out, and tried to login in GNOME as root.

I wrote "root" in the box, and then the password. Then I pressed Enter. Nothing happened, except I was being asked again for the username.

Now I know this seems similar to a forgotten password, but I assure you, I still know the password. Actually, I noticed that whenever I insert a wrong password, GNOME spends some time till telling me it's wrong. This is not the case. After inserting root/root's password, there is no waiting time, I'm instantly prompted to enter the username again. As if I'm still not allowed to login. Also, there is no message appearing (such as "check the CAPS" or "this user is not allowed to login" or "wrong password/username" or anything else).

This is creepy. Someone help me out.

---

### Post by agyeya on 2006-05-18
Which version of Ubuntu are you using. I have Dapper Drake. And have done the same things that you have mentioned. But I do not recieve any such anomaly. Check if there is any other setting that you might have missed in the GDM setup.

---

### Post by zugu on 2006-05-18
I'm using Ubuntu 5.10. I have also done this thing in the past, with no problems occuring. But now the creepy thing won't allow me to login as root via GNOME. I can still login using the console.

---

### Post by Kobalt on 2006-05-18
There is actually no root user in ubuntu, only a regular user, which can be granted root privilege after logging in, in command line by typing : 
```
sudo command-you-want-to-execute-as-root
```

---

### Post by mostwanted on 2006-05-18
Ubuntu uses sudo instead of root (similar to Mac OS X):

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by zugu on 2006-05-18
Kobalt and mostwanted:

Thank you for the replies, but they are not related to my problem. I need to login to GNOME as root, not to perform commands via sudo.

---

### Post by Kobalt on 2006-05-18
Why do you need as root ? What do you need to do ? Everything can be done as root with command lines. There is no way of logging in as root in Gnome with Ubuntu...

---

### Post by zugu on 2006-05-18
Kobalt, I know you want to help, but I think my question was clear enough.

It's irrelevant if I can do something through the command line or not. All it matters for me now is that I see a feature that does not work for me and I'm just trying to find out why.

If a feature is in Ubuntu, one would expect it to work, wouldn't (s)he?

And it is possible to login as root through GDM. Check this thread out: [http://www.ubuntuforums.org/printthread.php?t=31053](http://www.ubuntuforums.org/printthread.php?t=31053)

---


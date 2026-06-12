---
title: "Can't gain Root access"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-02-07
So I just installed Ubuntu, and it's working fine. But I can't log in as root. It keeps saying "invalid password"....can I somehow bypass my personal accounts admin restructions to reset my root password without having to reinstall the whole OS? 

And before anyone starts accusing me of trying to hack Ubuntu, I'm not...this is a serious problem I'm having.

---

### Post by aujames95 on 2006-02-07
"sudo passwd root" will allow you to set the root password. You should then be able to login.

---

### Post by The Mekon on 2006-02-07
I believe that I just clicked System/Administration/Users and Groups which, after entering my normal password, enabled me to set up a root account with a new password.

I can log in as root or myself.  sudo works with my password and su uses the root passwork to run as super user.  Of course use root or su very carefully.

---

### Post by Sutekh on 2006-02-07
> **darkbullet87]So I just installed Ubuntu, and it's working fine. But I can't log in as root. It keeps saying "invalid password"....can I somehow bypass my personal accounts admin restructions to reset my root password without having to reinstall the whole OS? [/QUOTE]
You shouldn't be able to log in as root, if you've *just* installed Ubuntu. 

The first user you created has all the power of root availble to it, you just need to use the **sudo** command to unleash it.
-The often cited link can explain said:**
> Ubuntu Wiki - Root and Sudo[/URL]

If you *really* want to use the root account (not recommended) you need to enable it by the command **aujames95** gave you (boy am I late on this one)

[QUOTE]
And before anyone starts accusing me of trying to hack Ubuntu, I'm not...this is a serious problem I'm having.
There is *nothing* wrong with trying to hack Ubuntu :D   That's where the real fun is!

---

### Post by darkbullet87 on 2006-02-07
Thanks for the info.  I didn't realize that Sudo was the same as root access.

---


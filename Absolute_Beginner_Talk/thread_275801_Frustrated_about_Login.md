---
title: "Frustrated about Login"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by akhtet on 2006-10-11
Okay, I hate to post another thread about the beginners, but I had to. 

After my Ubuntu installation was complete, it rebooted, and then asked me for login. I didn't specify any user name and password during the installation process, but now it's asking me for Login, and I have no idea what user/pass to use.

I think it is because there was something wrong with the installation. I've installed ubuntu before and I don't remember how I managed to get my own user/pass.

Can anyone help me with this? Thanks!

---

### Post by whiterabbit on 2006-10-11
If I remember correctly, you should be able to create a user during the installation process.  Are you installing from the same CD you used prior?  You may have accidentally skipped that step.

---

### Post by akhtet on 2006-10-11
The one I've used before is 6.06. But now I downloaded 6.06.1 ISO last night, and burned a new CD. I guess I might have to reinstall it, unless somebody came up with a solution. Thanks.

---

### Post by meng on 2006-10-11
Otherwise try username:password ubuntu:ubuntu
If you do need to reinstall, make sure you don't skip over any steps (by pressing Enter too quickly, I mean).

---

### Post by taurus on 2006-10-11
Boot your machine into recovery mode from GRUB and at the prompt, do

```

useradd -m -G adm,admin john
passwd john
(assuming john is your username...)

```

---

### Post by akhtet on 2006-10-12
I tried adding the user by user add.
However, it didn't work out.

So I reinstalled using the same CD.
This time it asked me to give user name to create.
So, finally I was able to login.

I don't think I accidently skipped the user creation step.
Even if I accidently skipped, it should prompt an error.

But now, I'm facing the same problem, why I didn't use my previous Ubuntu 6.06. HTTPS and Instant Messaging don't work. Only HTTP pages came up.
I'm gonna post this with a new topic.

---


---
title: "Troubles with server X after dist-upgrade - 6.06 to 6.10"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by dudz5150 on 2006-11-29
First of all, good night for all of you!

Well, I've upgraded my system ubuntu 6.06 to the 6.10 version, thought the apt-get dist-upgrade, and then I've installed ubuntu-minimals, cause a friend told me to do that. And now, when I reboot the system, my server X doesn't load. I receive this message(or some thing like this, I'm translating it): Server X failure trying to start. Probably it isn't configured right.

Does anybody here knows what's happening?


Thanks for your attention! =]
Eduardo Carvalho 

P.S.:I'm sorry for my bad english, and I promise that I'll learn it better, some day!

---

### Post by taurus on 2006-11-29
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dppkg-reconfigure xserver-xorg
```

---

### Post by dudz5150 on 2006-11-29
Thanks for answering!

Ok, I've tried it...

I entered the code, and the answer was: 
xserver-xorg is broken or not fully installed.

Could I try to reinstall it? The xserver
What is the code? by an apt-get way, may be?

---

### Post by taurus on 2006-11-29
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install xserver-xorg
```

---

### Post by dudz5150 on 2006-11-29
Wow! That's what I call a fast answer!

Thank you taurus! I'm doing the whole thing in here, and waiting for the finished installation... 
Wait a minute... 
One more... and done!

yeah! I've restarted the system, and everything seems to works fine, including the xserver! 

Thank you man, thank you soo much!

Now, can I ask what is this code apititude? Its something like the apt-get?

=]

---

### Post by CatKiller on 2006-11-30
> **dudz5150 said:**
> Now, can I ask what is this code apititude? Its something like the apt-get?

[aptitude versus apt-get]("http://www.psychocats.net/ubuntu/aptitude")

---


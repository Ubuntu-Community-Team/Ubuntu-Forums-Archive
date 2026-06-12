---
title: "[SOLVED] Cant run Synaptic"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by franzziss on 2007-11-14
I just Installed my Ubuntu 7.10 last night. I'm a beginner with the linux. My problem is I can't start my Synaptic Package Manager. The Message is:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report[/B]

Then I try this one in my Terminal:

**dpkg --configure -a**

But Here'e the Message:

[B]francis@francis-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
francis@francis-laptop:~$ [/B]

What will I do to this one?

---

### Post by Inxsible on 2007-11-14
run```
sudo dpkg --configure -s
```

---

### Post by Dr Small on 2007-11-14
> **Inxsible said:**
> run```
sudo dpkg --configure -s
```
+1
Whenever you need to be super user, you use sudo ;)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by franzziss on 2007-11-14
Thanks the -s doesn't work. I replaced it to -a. Now it works. THANKS :)

---

### Post by Inxsible on 2007-11-14
> **franzziss said:**
> Thanks the -s doesn't work. I replaced it to -a. Now it works. THANKS :)yeah that was a typo on my part. I hadn't noticed it until you pointed out. Sorry !!

---


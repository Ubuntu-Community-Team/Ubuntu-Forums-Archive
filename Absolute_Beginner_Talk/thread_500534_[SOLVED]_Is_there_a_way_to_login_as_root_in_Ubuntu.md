---
title: "[SOLVED] Is there a way to login as root in Ubuntu?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by atri_2k7 on 2007-07-14
Hi,
I want to login as root. Is there a way to do this? Or do I always need to login as non-root and then su to root from a terminal to run administrator commands?

Thanks,
Atri.

---

### Post by Malibu Illusion on 2007-07-14
You can, but why would you need to?  Using sudo/su is the recommended method of executing commands; running continually as root is potentially insecure and dangerous.

After a 5 second search:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_root_user_to_login_into_GNOME)

---

### Post by aysiu on 2007-07-14
You don't need to log in as root. It isn't secure or convenient.

Read more here:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

Post back any further questions you may have.

---

### Post by Nussbaum on 2007-07-14
++

---

### Post by kevinlyfellow on 2007-07-14
You can login as root if you need to do more complex administrative tasks by doing this trick
```
sudo su -
```

You won't need to unlock your root account

---

### Post by marsbt on 2007-07-14
**atri_2k7** - check the following page, its a good read. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by xubu_caapn on 2007-07-14
he didn't ask if it is recommended, or good security practices. please don't respond with that sort of rubbish. you can cause the same amount of damage by editing a file by sudo that you can if your logged in as root. linux is about choice, and if by some off-chance he hoses his system in root, it's a lesson learned. please don't tell him what HE wants to do with HIS system.

---

### Post by kittyhawk63 on 2007-07-14
> **xubu_caapn said:**
> he didn't ask if it is recommended, or good security practices. please don't respond with that sort of rubbish. you can cause the same amount of damage by editing a file by sudo that you can if your logged in as root. linux is about choice, and if by some off-chance he hoses his system in root, it's a lesson learned. please don't tell him what HE wants to do with HIS system.

He would have been told to do the same thing by some of the masters here on the forum. Lighten up and have another cup of Java. But you are right, if he wants to experiment and learn by doing, that is his privilege. If he messes up, he can always reinstall. However, you telling someone not to say something is no different than them telling him not to do something. Sip. Slurp. Hmmm. Good!
kh

Edit: Aysiu is not some bozo with a noob's inability to tell the difference between sudo and su. He's one of the forum's staff members. I would take his advice if he offered it. BTW, he has never led me wrong any time he has addressed one of my questions.

---

### Post by Paul_world10 on 2007-07-14
a boot loader password  .  This is a great read

---

### Post by mikewhatever on 2007-07-14
> **xubu_caapn said:**
> he didn't ask if it is recommended, or good security practices. please don't respond with that sort of rubbish. you can cause the same amount of damage by editing a file by sudo that you can if your logged in as root. linux is about choice, and if by some off-chance he hoses his system in root, it's a lesson learned. please don't tell him what HE wants to do with HIS system.

I second the opinions already posted not to login as root. That advice is not rubbish, and forum members are not dummies that answer the question asked, but unable to express their opinion. Calm down.

---

### Post by atri_2k7 on 2007-07-14
Thank all of you very much for posting ur replies.  I wanted to some experiments with my system, so I wanted root access - instead of doing a sudo every time. And actually most of the other linux distros allow the user to login as root, so I don't see anything wrong there.

 Yes, I was able to login as root, thanks to your replies.

---


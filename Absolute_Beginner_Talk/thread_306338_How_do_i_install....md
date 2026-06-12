---
title: "How do i install..."
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by serosis on 2006-11-24
How do I install Firefox 2.0 manually if I supposedly don't have "Owner" permissions, or how do I get "Owner" permissions?

It really pisses me off that I installed Ubuntu but yet I'm not considered the "owner".

---

### Post by taurus on 2006-11-24
You are the owner of your $HOME directory but not the whole system in case you screw it up!!!  But if you install Edgy, then you would have firefox 2.0.  Otherwise, here is how you install it by hand on your Dapper...

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by CatKiller on 2006-11-24
You'll probably also find these to be useful reading:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PrairieShaman on 2006-11-24
This is part of the reason that linux is so secure! To make any serious changes to the system you must **sudo** and then type in your password, or log in as root.

I had a hard time figuring it out myself, but now that i have arrived here at ubuntuforums I've started to get a pretty good grasp on running linux! It's excellent!8)

---

### Post by serosis on 2006-11-25
thanks alot guys, i really appreciate the links and the info.

sorry if i came off like an *******, just me being temperamental.

---

### Post by nuclearj on 2006-11-25
> **serosis said:**
> thanks alot guys, i really appreciate the links and the info.

sorry if i came off like an *******, just me being temperamental.

What does ******* mean?  LOL JK!  Carry on... ;)

---

### Post by serosis on 2006-11-25
ok another question...

how do i enable the ability to have root permission all the time?

or something like a temporary root permission?

---

### Post by junglepeanut on 2006-11-25
Be careful

sudo su

or

sudo -s

---

### Post by nekr0z on 2006-11-25
Try the "su" command in terminal. You may also want to read help on this with "man su" first.

But I strongly advise you to think about it once more and consider if you *really* want it. For me it is always enough to have sudo for each root command, and being root for some time is always bad for system security. Even enabling this option is bad, actually.

By the way, having to print "sudo" every time you do something that requires root access by itself makes you think once more. Thus you have more time to think of what you're doing, and less chance to spoil the system by mistype or something... For a temperamented person like me (and you) this is really a good thing...

---

### Post by gschoper on 2006-11-25
> **serosis said:**
> ok another question...

how do i enable the ability to have root permission all the time?

or something like a temporary root permission?

Not that I'd recommend this unless you know what your doing, but this will give you a root prompt:
```
sudo -s -H
```

HTH,

gschoper

---

### Post by CatKiller on 2006-11-25
> **serosis said:**
> ok another question...

how do i enable the ability to have root permission all the time?

or something like a temporary root permission?

Did you read the links?

---


---
title: "Linux Swap"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by peterhuang913 on 2007-12-27
I messed with Gparted and now under System Monitor, my Used Swap is zero. I do have a swap partition on /dev/hda3, how do I tell Ubuntu to use that as the swap?

---

### Post by overdrank on 2007-12-27
> **peterhuang913 said:**
> I messed with Gparted and now under System Monitor, my Used Swap is zero. I do have a swap partition on /dev/hda3, how do I tell Ubuntu to use that as the swap?

HI and maybe this link will help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by peterhuang913 on 2007-12-27
I tried mkswap but it says permission denied or it doesn't work.

EDIT: NVM, I used sudo before my mkswap and swapon and it works now.

Can someone explain what sudo is?

---

### Post by taurus on 2007-12-27
> **peterhuang913 said:**
> 
Can someone explain what sudo is?

Enjoy.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PmDematagoda on 2007-12-27
EDIT:- taurus beat me to it again, curse you taurus:).

---

### Post by peterhuang913 on 2007-12-27
It seems like my swap settings arn't saving. When I restart, the swap is gone.

---

### Post by taurus on 2007-12-27
You should add an entry in /etc/fstab for your swap partition so that it would be mounted each time you boot Ubuntu.  The entry should look something like,

```
/dev/hda3   none   swap   sw   0   0
```
assuming /dev/hda3 is your swap partition.

---

### Post by peterhuang913 on 2007-12-27
> **taurus said:**
> You should add an entry in /etc/fstab for your swap partition so that it would be mounted each time you boot Ubuntu.  The entry should look something like,

```
/dev/hda3   none   swap   sw   0   0
```
assuming /dev/hda3 is your swap partition.

I did what you said and it works now. Thank you all for your help!

One more question, should the swap partition be a primary or extended one?

---

### Post by overdrank on 2007-12-27
> **peterhuang913 said:**
> I did what you said and it works now. Thank you all for your help!

One more question, should the swap partition be a primary or extended one?

Neither swap is swap. Did you take a look at the link I posted?

---

### Post by peterhuang913 on 2007-12-27
> **overdrank said:**
> Neither swap is swap. Did you take a look at the link I posted?

I did. It mentioned both a swap file and the swap partition and how to make the file.

---

### Post by bodhi.zazen on 2007-12-27
> **peterhuang913 said:**
> I did what you said and it works now. Thank you all for your help!

One more question, should the swap partition be a primary or extended one?

I do not think it really matters if swap is a file or partition (primary or logical) [extended partitions house logical partitions].

There may be a slight performance boost if swap is a partition rather then a file, but i would bet most users will not notice it as swap is slower then RAM.

---


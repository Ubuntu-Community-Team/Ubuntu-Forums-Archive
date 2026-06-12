---
title: "Live CD problems asking for password"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Randy133 on 2007-07-26
I  am trying to install ubuntu on a windows xp machine.  I used this cd to install Ubuntu on my laptop.  It is working great!  But this install is asking me for a user name and password with I boot from the live cd.  Ok, so I got on here and looked up the live cd problem.  I found that it may be the cd meida, so I tryed the live cd in a second XP machine, and it worked just fine, no password it just came up.  So the cd is fine.  I did try to install Ubuntu on this machine before and it would not install, not enough memory.  I installed more memory and I removed the partition before trying to install again.  I am installing a dual boot system  XP and Ubuntu.  I did this on my HP laptop   and it works just fine.  Just can't get it to boot without going to User name and password.  I have tried: Ubuntu no password, Windows user name no password, windows user name and windows password.  nothing works.  I hope someone can help.

---

### Post by aspen_dv on 2007-07-27
at which point  does it ask you for username and password?

---

### Post by wolfen69 on 2007-07-27
sometimes using a different disk such as the alternate cd can make a difference. you might even consider xubuntu as an option.

---

### Post by Randy133 on 2007-07-27
The Live cd loads up it has the brown screen, but it is before seeing all the objects loading.  

:)

Why Xubuntu,  I have Ubuntu on about 4 machines, and planning on putting it on all my other machines in my shop.  why would I want to change?  why not just fix the problem, not just run away from it.  I just may learn something in the process.
:guitar:

---

### Post by aspen_dv on 2007-07-27
My feeling is  there was already linux partition on the hard drive. I would also check the BIOS to make sure no any password is set.
ok, can you boot the CD in single mode? I think at boot prompt just type "linux single".  If you could  get into single mode, try
fdisk -l

---

### Post by Randy133 on 2007-07-27
> **aspen_dv said:**
> My feeling is  there was already linux partition on the hard drive. I would also check the BIOS to make sure no any password is set.
ok, can you boot the CD in single mode? I think at boot prompt just type "linux single".  If you could  get into single mode, try
fdisk -l

I thought the same thing, that there is a partition still on the HD.  But I used Partition majic and looked with no luck.  I see no extra partitions.  The Live cd is bootable, I dont see a prompt.  How would I go to a prompt?  ca I boot from my windows XP?

---

### Post by Randy133 on 2007-07-28
> **Randy133 said:**
> I thought the same thing, that there is a partition still on the HD.  But I used Partition majic and looked with no luck.  I see no extra partitions.  The Live cd is bootable, I dont see a prompt.  How would I go to a prompt?  ca I boot from my windows XP?

I fond the problem!   I went into partition magic and formated the free space that was allocated.  Then I deleted it so That it was unallocated  block.  Put in the live Cd no password.  It is install now.
Thanks for all the help:popcorn:

---


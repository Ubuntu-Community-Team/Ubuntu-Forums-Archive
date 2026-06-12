---
title: "Need partitioning advice for Ubuntu and OS X dual boot"
date: 2009-07-10
forum: Apple Hardware Users
---

### Post by Aybara on 2009-07-10
I'm gonna install Ubuntu on my MBP. Have tried Virtualbox, but I want a native install after all.

I have a 250GB drive, and I thought I'd make an ext3 partition of 15GB to install Ubuntu on. What I'm unsure about is where Ubuntu should read/write media and documents. I believe OS X is fond of having the User folder on the same partition as the rest, so I thought maybe I could just mount my OS X /home with read/write support in Ubuntu, and let it work with the Documents/Photos/Movies/Music-folders there.

Do you see any pitfalls with this? As long as it's mostly media and stuff I access, I shouldn't screw up permissions or other stuff for OS X, I think.

---

### Post by kidders on 2009-07-11
Hi there,

> **Aybara said:**
> I believe OS X is fond of having the User folder on the same partition as the restOS X doesn't really care where the /Users directory is. Personally, I would put it on an unjournaled HFS+ filesystem. That way, you could avoid having to mount your MacOS root filesystem in Linux.

> **Aybara said:**
> As long as it's mostly media and stuff I access, I shouldn't screw up permissions or other stuff for OS X, I think.The best way to avoid running into problems with permissions is to change your MacOS user IDs from 501/502/etc. to 1000/1001/etc. so they match up properly with Ubuntu's user IDs.

Putting /Users on a separate partition has certain advantages. It makes it easier to reinstall OS X from scratch without losing user data, and can boost the long-term performance of your root filesystem by keeping a lid on fragmentation. The main *dis*advantages of doing so are (a) moving something into /Users from elsewhere would no longer be instant, and (b) disabling journaling for the sake of better compatibility with Linux elevates the risk of filesystem corruption in the event of a sudden power loss.

I hope that helps.

---

### Post by Richardcavell on 2009-07-11
Aybara,

I just want to clarify something in case you didn't quite catch it: There are two problems that you have. First, you need to use the same user id in both Linux and OS X. That's do-able. The second problem is that OS X doesn't really work well with ext3 and Ubuntu doesn't work well with HFS+.  You're going to have to use a file system for your /home partition that both can read and write. Unjournaled plain HFS will work, as kidders said, but you're giving up the benefits of having journaled HFS+.

Richard

---

### Post by Aybara on 2009-07-11
Thanks for the replies guys. I was a bit unclear when I said that I believe that "OS X is fond of having the User folder on the same partition as the rest". The only thing I'm actually thinking of is if Time Machine will cope.

The UID issue is also something I know about. Any particular reason I should change the ID in OS X and not in Ubuntu?

I like the idea of a dedicated media partition, and I think that the loss of journaling is ok.

---

### Post by kidders on 2009-07-12
Hey again,

**Time Machine**
There are a few ways of linking a Users partition to the rest of your MacOS system (for example, a symlink to /Volumes/Users, modifying your /etc/fstab, tinkering with your user configurations to point home directories somewhere other than /Users/<username>, and so on). Depending on how you do it, Time Machine *might* back up your Users partition twice, so the worst case scenario is that you may have to manually exclude one of the copies in your Time Machine preferences. 

Other than that, Time Machine should be fine.

**Other Stuff**
Technically, all IDs under 1000 are reserved by Linux for system use, so given the choice, it's safer to change OS X's UIDs than Ubuntu's. Although I can't think of a good example off the top of my head, something you install on Linux in the future may try to use UID/GID 501.

Incidentally, Richardcavell and I were so preoccupied with the down-side of unjournaled HFS+, neither of us mentioned that you should get slightly better performance out of it, so you'll be able to mess around with your media files that bit faster.

---

### Post by Aybara on 2009-07-12
Thanks for the feedback!

---


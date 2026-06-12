---
title: "Programs on 686"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by EnderTheThird on 2005-08-26
I'm having problems doing some things now that I'm running the 686 kernel:

1.  I can't get Wine to install, apt-get/Synaptic won't allow the install.  This seems to be happening with a lot of programs, not sure if it's related or not?

2.  I'm not sure what to do about the ATI drivers, because the downloaded file says it's for 386.

3.  I can't find the 1.0.6 update for Firefox now.  I'm not sure if the repository or repositories that have it are down, or if it's just not showing it to me because of the different kernel.

I'd like to continue running the 686 kernel, because supposedly it will give better performance for my P4.  Is the different kernel that cause for these problems?  If so, is there a way to fix them, or should I just say screw it and go back to running it under 386?  Thanks for any help you guys can give me.

---

### Post by Lord Illidan on 2005-08-26
1. What does Synaptic say in the error message?
2. I don't have ATI, but I think 386 will still work on 686..
3. Disable the backports.. Put a hash (#) in front of them in the sources.list

---

### Post by EnderTheThird on 2005-08-26
1.  ```
wine:
  Depends: libwine (=0.0.20050310-1.1) but 0.0.20050419-1~5.04ubp1 is to be installed
```
I've been getting similar error messages when trying to install other programs.  I've looked for the packages that it tells me to install, but I can't find them.

2.  OK, maybe I'll give them a try later.

3.  I've tried with and without the backports enabled, and double-checked with the Ubuntu Guide to make sure I had the same repositories listed, but it still won't find 1.0.6.  It shows that the latest version is 1.0.6, and that I have 1.0.2 installed, but it can't seem to find 1.0.6 so I can install it.

---


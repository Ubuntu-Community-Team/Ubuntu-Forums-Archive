---
title: "Linux Overheat"
date: 2013-07-10
forum: Apple Hardware Users
---

### Post by pdiddles03 on 2013-07-10
I have searched and searched and don't seem to get an answer, why do macbooks overheat when running Linux?  is there a solution for this?

---

### Post by rkmugen on 2013-07-10
Are you talking about MacBooks in general, or your specific MacBook (which exact model is it by the way)?  And which version of Ubuntu are you using?  Are you running the appropriate kernel?

Having said that, you'd probably want to refer to these forum postings to see if you can get better control over your MacBook's fan:
  
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=2113900](http://ubuntuforums.org/showthread.php?t=2113900)
[*][http://ubuntuforums.org/showthread.php?t=1467062&page=4&p=9778072#post9778072](http://ubuntuforums.org/showthread.php?t=1467062&page=4&p=9778072#post9778072)
[*][http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431)
[/LIST]

---

### Post by pdiddles03 on 2013-07-10
I have a early 2011 macBook pro 8,2 15". I didn't know there was different kernels that were compatible with Mac.  I have run the newest version of Ubuntu, Linux Mint, Kubunue Xubuntu and so on.  But all the same thing.  I don't want to kick my fan into high gear because that is the only solution i saw is to have it constantly run at a high speed.  If that is the solution, I won't install it.

---

### Post by buzzingrobot on 2013-07-10
Fan control utilities exist for Linux on Macbooks. I can't vouch for their effectivness.

If your machine has two video chips -- an onboard Intel and a discrete AMD or Nvidia, odds are it will run cooler and quieter if you can get it to use only the Intel.  Doing this can be problematic depending on the specific Macbook model you're working with. But, it does require installing and booting in EFI mode. (Ubuntu's Mac-friendly ISO image, the one with "mac"' in the filename, does not boot or install in EFI mode.)

Linux thermal control, in my experience with my Macbook, not in the same game with OS X.

---


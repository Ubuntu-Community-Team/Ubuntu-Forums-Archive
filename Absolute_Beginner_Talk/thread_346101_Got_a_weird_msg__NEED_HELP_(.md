---
title: "Got a weird msg ?? NEED HELP :("
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-25
Hi all, 
Everytime i type 
```
$sudo aptitude update 

```
i got this msg at the end?!?!?
> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Same msg if i use apt-get update also the GUI interface for updates

??? 

Can some one explain ??

---

### Post by Jussi Kukkonen on 2007-01-25
Signatures ensure that you only install files that are signed by someone you trust -- in this case *ftpmaster@ubuntu.com* had signed the package list you downloaded. For some reason the signature didn't match (and the list is thus not used). 

In theory it's possible that it's a man in the middle attack -- as in some unknown site poses as ubuntu.com -- but a more probable explanation is that *ftpmaster@ubuntu.com* just made a mistake... Try again tomorrow, it's probably been fixed. If not. post a reply here.

---

### Post by Mba7eth on 2007-01-25
But i got the same msg using liveCD and after installation ?
So Theoretically my box is safe ;)

---

### Post by valkarin on 2007-01-25
The problem is not at your end, but at the server you are trying to download from.  Which version on ubuntu are you running?  If it is not edgy, then it is an error at your end.  

You may also want to try 

sudo apt-get update

This may fix your problem.

---

### Post by valkarin on 2007-01-25
Did a little more checking.  Do you have the main, restricted, universe, and multiverse repositories enabled?  This might be your problem as well.  If not the there is a howto at [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu").

See if any of these fix it for you.

---


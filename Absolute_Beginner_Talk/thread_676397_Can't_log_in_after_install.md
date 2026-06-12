---
title: "Can't log in after install"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Toribor on 2008-01-23
I've been having lots of issues so thanks in advance for any help.

I just installed Ubuntu 7.10 Gutsy Gibbon on my external hard drive through USB. I used the Alternate CD because the live CD quit working at 15%. Everything seemed fine but when I tried to log in for the first time using my username and password it told me I was logged in for less than ten seconds and to try using the safe logins. I tried this, and none of them seem to work either. Where do I go from here? :confused:  Do I need to reinstall? I'm really having a lot of issues with this... :(

---

### Post by chewearn on 2008-01-23
Any particular reason why you are installing on external USB harddrive?  Apologies, I don't have a direct solution to offer, but rather a suggestion.  Try a run-off-mill internal IDE harddisk installation.

.

---

### Post by wormser on 2008-01-23
I am not sure how to solve your issue but here is something else to try.  Log in recovery mode.  Try changing the password of that user and creating a new account.

```
passwd username
```

```
adduser username
```

You are root in recovery mode so you do not have to use sudo.  Good luck.

---


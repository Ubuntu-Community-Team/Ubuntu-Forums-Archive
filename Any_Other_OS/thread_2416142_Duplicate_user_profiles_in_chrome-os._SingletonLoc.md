---
title: "Duplicate user profiles in chrome-os. SingletonLock and SingletonCookie error."
date: 2019-04-05
forum: Any Other OS
---

### Post by tuthree8 on 2019-04-05
After chromebook restart and login chromebook requested password and passphrase. The password was able to log me in. After logging all user profile settings, apps and extensions were missing which looked like a new profile, it still had the original user profile name. I tried ¨reset sync¨ to remove passphrase, it did not work. Reset sync removed all data showing the apps, settings and extensions that were originally sync to the original user profile. Doing research describes an error with chrome-os not recognizing user profile and then creates a new one. My question is the data that was erased or moved still on the original user profile. Also is the original still accessible or can the duplicate user profile just be deleted or removed.Below is information that was retrieved from chrome-os /home/chronos terminal showing the error. I do not know how to post image. 

```
lrwxrwxrwx 1 chronos chronos 20 Apr 3 22:09 SingletonCookie -> 15231020882235353038


lrwxrwxrwx 1 chronos chronos 14 Apr 3 22:09 SingletonLock ->localhost-1440


lrwxrwxrwx 1 chronos chronos 46 Apr 3 22:09 SingletonSocket -> /tmp/.com.google.Chrome.KyLWg5/SingletonSocket


drwxr-xr-x 3 chronos chronos 4096 Jan 10 15:20 SSLErrorAssistant


drwxr-xr-x 4 chronos chronos 4096 Apr 5 2017 'Subresource Filter'


drwx------ 2 root root 4096 Aug 19 2017 u-11d70123c6f2770fb077046f73f1a133bfeeb66e


drwx--x--- 40 chronos chronos-access 4096 Apr 4 19:30 u-395c47cefe914112166e46d2cbb21e8b759397af


drwx------ 2 root root 4096 Apr 2 23:03 u-62100bbe8980246638c0d68fb17c5917f7324ebb


drwx--x--- 40 chronos chronos-access 4096 Apr 4 19:30 user
```

---

### Post by wildmanne39 on 2019-04-05
Hello and welcome to the forum!

*Thread moved to **Any Other OS a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by tuthree8 on 2019-04-06
I was not very certain where to start out with my first post, I just choose one sub-forum that seemed appropriate.

---


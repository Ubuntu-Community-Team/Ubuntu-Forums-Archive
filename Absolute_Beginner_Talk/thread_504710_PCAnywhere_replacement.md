---
title: "PCAnywhere replacement"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2007-07-19
Is there an open source replacement for PCAnywhere on Linux? I know UltraVNC is under the GPL, but only runs on Windows.

---

### Post by reckless2k2 on 2007-07-19
there are tons of freeware vnc options and ubuntu has it built in with rdesktop. you just need client on other side like tightvnc executable on a windows desktop. is that what you're asking. if it's linux to linux, run X over ssh...easy to do.

---

### Post by Ephilei on 2007-07-19
But pcanywhere doesn't use the vnc protocol, it using something of their own.

---

### Post by reckless2k2 on 2007-07-20
i'm confused...are you looking for a pcanywhere alternative on linux or are you looking for pcanywhere to support linux? you're the one that mentioned ultravnc. there are various remote desktop type wares for linux. remote desktop began with unix/linux.

---

### Post by slacker9876 on 2007-07-20
I too am using rdesktop as it works great. I do have a question myself though. I am able to connect at 800x600 and also at full screen, however, when I use "rdesktop -g:1024x768" I am given this error:

ERROR: invalid geometry

I must assume I have entered the parameter incorrectly as I know this is a valid resolution. Is someone here able to help with my fat-fingers?

Thanks!

---

### Post by Ephilei on 2007-07-21
I work IT supporting Windows machines running the pcanywhere client. I'd like to just run just Linux, but I'm stuck spending some time on Windows just to use pcanywhere.

---

### Post by scxtt on 2007-07-21
> **slacker9876 said:**
> I too am using rdesktop as it works great. I do have a question myself though. I am able to connect at 800x600 and also at full screen, however, when I use "rdesktop -g:1024x768" I am given this error:

ERROR: invalid geometry

I must assume I have entered the parameter incorrectly as I know this is a valid resolution. Is someone here able to help with my fat-fingers?

Thanks!rdesktop -g 1024x768

---

### Post by slacker9876 on 2007-07-21
Thanks! I should have also posted that after reviewing the man page you can use % too!! I so love this OS, it  does more than I could imagine!

---


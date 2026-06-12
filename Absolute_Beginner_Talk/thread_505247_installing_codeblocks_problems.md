---
title: "installing codeblocks problems"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by resistantgnome on 2007-07-20
I tried this on terminal **sudo dpkg -i CB_20070715_rev4266_Ubuntu6.10+7.04_wx2.8.4.deb **
Got few errors. Can anyone help me to move ahead
```

(Reading database ... 130089 files and directories currently installed.)
Preparing to replace codeblocks 1.0svn-rev4266 (using CB_20070715_rev4266_Ubuntu6.10+7.04_wx2.8.4.deb) ...
Unpacking replacement codeblocks ...
dpkg: dependency problems prevent configuration of codeblocks:
 codeblocks depends on libwxbase2.8-0 (>= 2.8.4.0); however:
  Version of libwxbase2.8-0 on system is 2.8.1.1-0ubuntu4.
 codeblocks depends on libwxgtk2.8-0 (>= 2.8.4.0); however:
  Version of libwxgtk2.8-0 on system is 2.8.1.1-0ubuntu4.
dpkg: error processing codeblocks (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks

```

---

### Post by wolfen69 on 2007-07-20
this isnt a beginners problem.

---

### Post by wolfen69 on 2007-07-20
it says ABSOLUTE beginners. am i missing something?

---

### Post by JesterDev on 2007-07-20
> **wolfen69 said:**
> it says ABSOLUTE beginners. am i missing something?

Under to assumption that he/she is a beginner and didn´t post in the wrong forum:

He/She is a beginner. The topic or level of needed experience is of little consequence when the person asking the question is a beginner.

---

In any case it looks like you need to upgrade to the latest version(s) of ibwxbase and libwxgtk as the ones you have installed
are older.

---

### Post by resistantgnome on 2007-07-20
Sorry for posting it here. I have posted the same question on installation section. I'll wait for replies there.

---


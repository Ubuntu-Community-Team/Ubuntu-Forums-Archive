---
title: "Lost icon for Thunderbird 2 in feisty"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by zyrmjy on 2007-05-14
I know some one asked similar question
[http://ubuntuforums.org/showthread.php?t=435413&highlight=thunderbird+icon](http://ubuntuforums.org/showthread.php?t=435413&highlight=thunderbird+icon)

but it seems not working for my case.

What I did was adding a source for third party software from
[http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing)

The installation went through and I am able to use TB2 now. But the icon is missing in the Applications->Internet for this thing. Any one has an idea about this?

Thanks in advance.

---

### Post by terdon on 2007-05-16
This should find the icon:```
 locate thunderbird | grep icons | grep default.xpm
```

---


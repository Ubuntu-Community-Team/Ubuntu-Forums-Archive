---
title: "I Screwed Up"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by 565Customz on 2008-01-26
ok so i enabled the root user thinking that i would be able to  run in that mode to do system task through the desktop environment....wrong! lol so i  took my user administrator rights away  and now im stuck on setting things back to default.

i tried sudo adduser username admin 

and it said that it added me back but when i log in i cant change anything...anyone that can help me put things back the way they were.

---

### Post by LookTJ on 2008-01-26
Isn't it:
```
 sudo gpasswd -a **username group**
```Let me read your post one more time

Edit: the group that has access to sudo is **adm** in Ubuntu.

To disable root(for security reasons)
```
sudo passwd -l root
```

---

### Post by 565Customz on 2008-01-26
actuall that code i used must of worked. i restarted cuz i wanted to see if it wouldnt let me logon at the main screen. (like it wont do for root if you have it on) but it let me in and worked fine...the power of the restart...lol thanks though

---

### Post by LookTJ on 2008-01-26
> **565Customz said:**
> actuall that code i used must of worked. i restarted cuz i wanted to see if it wouldnt let me logon at the main screen. (like it wont do for root if you have it on) but it let me in and worked fine...the power of the restart...lol thanks though
Look at my previous edited post to disable the root account if you actually enabled it.

---


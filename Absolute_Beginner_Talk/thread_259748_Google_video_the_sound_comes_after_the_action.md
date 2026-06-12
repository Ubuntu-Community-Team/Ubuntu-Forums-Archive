---
title: "Google video the sound comes after the action???"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by thenewdeal38 on 2006-09-17
PLease how do i fix this??

---

### Post by Anduu on 2006-09-18
[http://www.ubuntuforums.org/showthread.php?t=186594&highlight=flash+sound+sync](http://www.ubuntuforums.org/showthread.php?t=186594&highlight=flash+sound+sync)

---

### Post by andb on 2006-09-18
The solution that worked for me:
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
Ive seen lots of ways to "fix" the sound in flash in firefox. I have this run in a startup script when I log on, so it works for each user. (the 1000 changes, of course, with each user ID. NO OTHER CHANGES are necessary, at least on my machine. The simplest fix is the best one, I think, and Id rather not use OSS. You may have to reverse the changes you made to get it to work before. Let me know if this works for you. Also, concider using swiftfox, [http://www.getswiftfox.com/](http://www.getswiftfox.com/)

---


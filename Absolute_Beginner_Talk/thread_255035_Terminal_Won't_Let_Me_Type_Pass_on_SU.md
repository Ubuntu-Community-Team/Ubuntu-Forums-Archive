---
title: "Terminal Won't Let Me Type Pass on SU"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by djcaston on 2006-09-10
This is probably a total noob question, but when i try to do su on terminal, and the password line comes up, it doesn't let me type the pass in. It blinks, but when i start to type, nothing comes up. Please Help.

---

### Post by ewl1217 on 2006-09-10
It's normal for nothing to show up when you type a password with "sudo" or "su". Just type it like normal and it should work.

---

### Post by edrodgers731 on 2006-09-10
The root password is disables in Ubuntu.  Try prepending a 'sudo' in front of your commands to run as root.

---

### Post by djcaston on 2006-09-10
i thought about that. so i tried it. it didnt work. i typed in my pass and it didn't work.

---

### Post by jordanmthomas on 2006-09-10
If you need to use root for a while...
```

sudo su

```
Type your password and press enter.  You can't see it but trust me...it's accepting it.
Your prompt should then aknowledge that you are root.

---

### Post by djcaston on 2006-09-10
thanks so much! it worked

---


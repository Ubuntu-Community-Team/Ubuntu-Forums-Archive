---
title: "CD-ROM name thorugh command line"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by LHZ on 2005-10-28
Is there a shell command that will give me the name of the cd-rom currently in the drive? I'm pretty sure there must be one, but googling and searching the forums didn't turn up anything.

Thanks.

---

### Post by Kyral on 2005-10-28
Like what it is called (Like if I have my Jedi Academy Disc 1 in the drive you want it to return "Jedi Academy Disc 1"?)

I don't think there is a command line tool to do that, but I could be wrong, I never thought about it ;P

---

### Post by LHZ on 2005-10-28
Yes, that's it. It seems like basic functionality, but I haven't been able to find it anywhere.

---

### Post by ChrisTheGeek on 2005-10-28
You're right it wasn't easy to google for.  I think I've dug up something that will work for you though - 'volname'

[http://linuxcommand.org/man_pages/volname1.html](http://linuxcommand.org/man_pages/volname1.html)

Let me know if it works.
Chris

---

### Post by LHZ on 2005-10-28
[QUOTE=ChrisTheGeek]You're right it wasn't easy to google for.  I think I've dug up something that will work for you though - 'volname'

[http://linuxcommand.org/man_pages/volname1.html](http://linuxcommand.org/man_pages/volname1.html)

Let me know if it works.
Chris[/QUOTE]

Thanks! I'll try that when I get home. Just out of curiosity, where did you find it?

---

### Post by ChrisTheGeek on 2005-10-28
I consulted the wonderous Google oracle.  Did a few searches using quotes and ignoring some unhelpful terms and eventually something popped up about volume labels.  Searching on that turned up the command.  Hope it works for you :)

---

### Post by LHZ on 2005-10-29
It works, thanks!

---


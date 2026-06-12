---
title: "A newbie question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by tbresson on 2007-02-16
I was trying to move a file test.txt to my desktop when I by accident wrote:
mv test.txt /Desktop

When I should have written mv test.txt Desktop/

Now the file is gone.. it's not important since it was just a test file with not much content .. but what happend to the file?

---

### Post by meng on 2007-02-16
Look for a file in your root folder:
cd /
ls Desktop
cat Desktop
(it should be your test.txt file, renamed)

---

### Post by sloggerkhan on 2007-02-16
I wouldn't think that'd do anything without sudo.

---

### Post by meng on 2007-02-16
Good point, but since the file disappeared, it must have gone somewhere.

---

### Post by darrenm on 2007-02-16
If you were not root at the time or you didnt type sudo before it then it would have said permission denied.

The only other explanation is you typed the command differently to what you've put here.

---

### Post by tbresson on 2007-02-16
Yes, found the file in the root dir as you wrote.

PS: Yes I used sudo - I didn't think there would be a different answer whether or not I used sudo.

---

### Post by ac7ss on 2007-02-16
you can always do a 
```
ls -l `locate Desktop`
```
and see what shows up. :)

---


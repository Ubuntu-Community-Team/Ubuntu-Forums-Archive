---
title: "Run script when drive is mounted?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-22
I need to run a script when I mount a flash drive. How can I do this?

---

### Post by tdrusk on 2007-11-22
anybody? please?

---

### Post by kellemes on 2007-11-22
I actually don't know.. assuming you want automounting that is..
But you could write a script that mounts the stick **and** does the thing you want it to do..

---

### Post by tdrusk on 2007-11-22
I'm doing this for an old person. 

I have the script working, but it needs to run when the drive is inserted. No clicking involved.

---

### Post by kellemes on 2007-11-22
Well, I guess you need to write a udev-rule..

[https://help.ubuntu.com/community/UsbDriveDoSomethingHowto]("https://help.ubuntu.com/community/UsbDriveDoSomethingHowto")
[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")
[http://www.reactivated.net/writing_udev_rules.html#syntax]("http://www.reactivated.net/writing_udev_rules.html#syntax")

---

### Post by tdrusk on 2007-11-22
I figured it out.

I'm actually using Mint Linux, but it's all similar.
I opened this and did this
[IMG]http://i16.tinypic.com/6yvrb7d.jpg[/IMG]

runs great!

---

### Post by mdpalow on 2007-11-22
Why did they have to be "an old person" ???  

"I'm trying to write a script that will help someone who's not very familiar with Linux/Computers"

Just playin'  :guitar:

---

### Post by tdrusk on 2007-11-22
> **mdpalow said:**
> Why did they have to be "an old person" ???  

"I'm trying to write a script that will help someone who's not very familiar with Linux/Computers"

Just playin'  :guitar:
I think there's a difference. Some people have slight experience with technology (most jobs require it). 

On the other hand, old people probably didn't have a job in computers.

---


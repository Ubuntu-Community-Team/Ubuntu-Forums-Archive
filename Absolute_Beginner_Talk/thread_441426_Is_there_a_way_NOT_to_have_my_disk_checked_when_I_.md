---
title: "Is there a way NOT to have my disk checked when I boot?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-12
Every so often, I get a message on boot that

"This disk has been mounted 25 times without being checked.  Checking now"

What is this, and can it be avoided?

---

### Post by oilchangeguy on 2007-05-12
it's much like windows check disk. there's no reson to remove it. it can alert you if there's a problem with your hard drive.

---

### Post by Campingman on 2007-05-12
Mine checks every 30 times, why is it different?

---

### Post by gohanssjn on 2007-05-12
No clue.  And here's the weird thing, I haven't booted 25 times, so what is going on?  Do I have a mounting issue?

---

### Post by oilchangeguy on 2007-05-12
how do you know you haven't booted 25 times? time flies when you're having fun (using ubuntu). and as long as no problems are reported everything should be fine.

---

### Post by cotcot on 2007-05-12
You can skip the check by change the last column of the partition in fstab by a zero instead of 1 or 2. For instance change 
> # /dev/sda3
UUID=e5a5e8db-9f58-4ff0-b225-123775c1b723 /media/sda3     ext3    defaults        0       [COLOR="Red"]2[/COLOR]
to
> # /dev/sda3
UUID=e5a5e8db-9f58-4ff0-b225-123775c1b723 /media/sda3     ext3    defaults        0      [COLOR="#ff0000"] 0[/COLOR]
There is also a way to change the frequency of the check, but i do remember it for the moment.

---

### Post by orb9220 on 2007-05-12
> how do you know you haven't booted 25 times? 

I know and I also have this issue that I may have rebooted to my xp side 10times or so and then I get that message.

---

### Post by lobner on 2007-07-25
> **cotcot said:**
> 
There is also a way to change the frequency of the check, but i do remember it for the moment.

Anyone care to follow-up? How do I set this frequency to something higher?

This is exactly what I was looking for!
I run Ubuntu on my laptop, and reboot quite often. Hence the disk also gets re-mounted quite often.

/lobner

---

### Post by gn2 on 2007-07-25
Here's a thread which will explain all: [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by lobner on 2007-07-25
Hello again...

Thank you very much for the quick reply :)

---


---
title: "[SOLVED] two users?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by jakelute on 2008-02-10
I have a possibly stupid question:

$ top

top - 11:45:50 up 42 min,  2 users,  load average: 0.06, 0.07, 0.07
Tasks: 127 total,   6 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.5%us,  0.0%sy,  0.0%ni, 87.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    969536k total,   493360k used,   476176k free,    24548k buffers
Swap:  2835432k total,        0k used,  2835432k free,   246636k cache


Why 2 users? What does that mean?
Thanks!
Best wishes.....

---

### Post by LaRoza on 2008-02-10
Mine says 4 users, don't know what that means. Maybe it counts the times you ran something as root, or when you used a virtual terminal.

---

### Post by barbedsaber on 2008-02-10
mine says 2 users, but I get the feeling that we are all ok, I use sudo quite recently.(I craved the power!:twisted:)

---

### Post by PeterJS on 2008-02-10
Just ran a little experiment, I had top open in a terminal and started opening more terminals. As I opened more terminals and logged in to more pts, the number of users in top went up. If you're wondering who the two users, open up a terminal and run w, it will tell you about all the users logged in, you should see your X session on tty7, and then one pts session for each terminal you have open.

---

### Post by barbedsaber on 2008-02-10
right, well now that that's cleared up, could you please mark this thread as solved, by clicking thread tools, and then mark thread as sloved.

---


---
title: "Synaptic Package Manager crashes [Resolved ... sort of]"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Colorado_baja on 2007-05-05
When ever I try to open the package manager it appears for a second and then just disappears, no  error message or anything.. I'm running feisty.. It was working earlier in my session and then just quit.. 

Can anyone point me in the right direction?

Thanks in advance

Greg

---

### Post by aysiu on 2007-05-05
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gksudo synaptic
``` After Synaptic disappears, copy and paste the terminal output back to this thread.

---

### Post by Colorado_baja on 2007-05-05
It prompted me for my password and then did the same thing appeared for a second and then was gone, no error message..

---

### Post by Colorado_baja on 2007-05-05
Here are the terminal contents

gharmon@Welder:~$ gksudo synaptic
gharmon@Welder:~$

---

### Post by Colorado_baja on 2007-05-05
Add/Remove seems to be down as well..:confused:

---

### Post by aysiu on 2007-05-05
That's really weird... no error message at all.

Can you see if [this](http://www.psychocats.net/ubuntu/sudo) helps?

---

### Post by Colorado_baja on 2007-05-05
Here is the contents of the Terminal when I tryed to run Synaptic today as root.

harmonl@Welder:~$ su root
Password: 
root@Welder:/home/harmonl# synaptic
Segmentation fault (core dumped)
root@Welder:/home/harmonl# 

In retrospect I think I broke it trying to manually install Flash 8..:( 
Other commands that I execute under sudo work just fine.

I'm guessing its restore time?

Thanks for the tips.

Greg

---

### Post by Colorado_baja on 2007-05-06
Just decided to nuke it and start over, it was a fairly fresh load in any case.. Thanks again for the tips.

Greg

---


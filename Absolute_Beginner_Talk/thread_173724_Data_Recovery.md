---
title: "Data Recovery"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by blueoyster on 2006-05-10
While installing Ubuntu Dapper to dual boot, I accidentally formated a Fat32 partition that I wanted to keep. The partition has not been moved or resized and it's still a fat32. I mounted it as /shared to access it from both windows and linux. I can;t acces the data anymore either from Linux or Windows.

Is there a way for me to recover the data?

---

### Post by Sef on 2006-05-10
Try using this:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by blueoyster on 2006-05-10
Thanks for the quick reply.

I'll try it out and tell you how it went.

---

### Post by Sef on 2006-05-10
You're welcome.  I do hope that you can recover all your data.

---

### Post by blueoyster on 2006-05-10
so i  burned the cd now... and thinking that it would be simple i restarted the comp and booted up the rescue kit. 
However i have little to no idea what to do next, i was perhaps expecting a gui.  I tried reading the howto on the trinity web site but i didnt gain anything from that.

Do you know what i should be doing now? I have no idea.

I know some basic bash do i tried to **cd** to /shared but that was not allowed.

---

### Post by blueoyster on 2006-05-10
ok i found some info about the **fatback** script and i tried to use it but with no success, 
does anyone know the proper syntax or what exactly i should be defining for the script to work?

---

### Post by nocturn on 2006-05-11
I don't think fatback will do what you want, it undeletes file that are still in the File Allocation Table AFAIK.

You need some form of unformat utility, I'm not sure which are good on Linux.

---

### Post by nocturn on 2006-05-11
Maybe browse over here:
[http://www.fileedge.com/get/unformat/](http://www.fileedge.com/get/unformat/)

---


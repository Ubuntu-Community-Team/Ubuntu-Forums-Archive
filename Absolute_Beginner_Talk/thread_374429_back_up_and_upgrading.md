---
title: "back up and upgrading"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by bronevaya on 2007-03-02
how friendly is ubuntu when it comes to upgrading to newer versions? lets say I wanted to upgrade to fiesty, is it as easy as upgrading to vista from xp?

also, is there any kind of backup/restore software? lets say I screw up my install and delete my desktop or something, is there anything i can use to go back in time?

---

### Post by bronevaya on 2007-03-02
no one? no one?

---

### Post by namelessone on 2007-03-02
I upgraded from 6.06 to 6.10 and it was a piece of cake.

As for something like windows restore points, I'm not sure one exists. But then again, they aren't as necessary because there's no viruses to worry about.

Just back up your system by imaging your disk with a utility like g4l or by copying important files to another hard drive.

---

### Post by bronevaya on 2007-03-02
how is it done? can i use a live cd? will break my old install?

---

### Post by namelessone on 2007-03-03
> how is it done? can i use a live cd? will break my old install?

If by "it" you mean upgrading, I just read the instructions I found on the ubuntu site. It was some simple terminal command, I think. the command pretty much just apt-get'd a whole bunch of packages so all my previous settings were left intact.

If by "it" you mean backing up, you can do it from a live cd if you are disk imaging, but If you are just copying your important files (like the /home directory) to another hard drive, you don't need a live cd. And no, this won't break your current install (but there's a slight possibility that if you image your drive, the resulting image won't work properly).

---


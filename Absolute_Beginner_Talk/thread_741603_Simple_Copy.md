---
title: "Simple Copy"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by gallam on 2008-03-31
Everyone,

I feel like a total idiot.  I need help.

I have a folder on my desktop called Sounds that has system sound files in it.

I want to move it to /usr/share/sounds

What is the correct syntax?  I know it will be sudo.....  but I can't remember to save my life.

Can someone point the way?

Thanks.

---

### Post by alexforcefive on 2008-03-31
Err... good question actually! 

You could always just alt+F2 > gksudo nautilus and drag the files :)

---

### Post by Inxsible on 2008-03-31
> **gallam said:**
> Everyone,

I feel like a total idiot.  I need help.

I have a folder on my desktop called Sounds that has system sound files in it.

I want to move it to /usr/share/sounds

What is the correct syntax?  I know it will be sudo.....  but I can't remember to save my life.

Can someone point the way?

Thanks.

```
sudo cp -R /home/<username>/Desktop/Sounds /usr/share/sounds
```This will transfer all files from folder called Sounds to /usr/share/sounds. You can then delete the one on your desktop after you have made sure that the files have been copied over.

---

### Post by gallam on 2008-03-31
Thanks so much for the fast response.  Worked like a charm.

I'll write it down!  Thanks again, guys!

---

### Post by Inxsible on 2008-03-31
> **gallam said:**
> Thanks so much for the fast response.  Worked like a charm.

I'll write it down!  Thanks again, guys!Threads can be marked solved by going to Thread Tools>>Mark Thread as Solved :)  just so you know

---


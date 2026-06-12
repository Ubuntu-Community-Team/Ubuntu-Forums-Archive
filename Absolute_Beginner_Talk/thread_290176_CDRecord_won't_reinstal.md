---
title: "CDRecord won't reinstal"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-10-31
I have been recommended to reinstal CDRecord ([http://ubuntuforums.org/showthread.php?t=288500](http://ubuntuforums.org/showthread.php?t=288500))
So I used synaptic manager, marked cdrecord for reinstallation then applied changes. Then appeared the "downloading file" box but nothing was actually happening. Progress just remained at 0%. Looked like it wasn't downloading anything at all. What to do?
Thanks
Justin

---

### Post by Marsolin on 2006-10-31
It is trying to ask you a question, but Synaptic doesn't always pop-up the message. Click where is says show details (or something to that effect) and follow the prompt. If I remember the question correctly, you want to say yes. The goal is to make sure that cdrecord can act as root.

---

### Post by woodlandjustin on 2006-11-01
> **Marsolin said:**
> It is trying to ask you a question, but Synaptic doesn't always pop-up the message. Click where is says show details (or something to that effect) and follow the prompt. If I remember the question correctly, you want to say yes. The goal is to make sure that cdrecord can act as root.

I'm not sure that that is the case. It had asked me all the questions, and finally should have been dowloading the file. Indeed it said it was! But wasn't. The bar showing progress was empty. There was a part showing something like details for each file progress too, but opening that showed nothing (as there was no file being downloaded!)
I repeated the whole process twice to check, and it was the same. Now after a break I have come back, and readning your post wanted to repeat the process to tell you precisely what it says. However this time, having done the exact same thing, it worked fine. For me, sadly this is just another of the far-too-many inconsistencies since I have been using ubuntu. I really want it to work, but so many things just seem to be random, working this time, not the next. And on and on. Very unreliable from the experience I have had since installing.:(

---

### Post by Sef on 2006-11-01
Have you enabled the [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") ?  I think it is universe.

If so, try this and copy and paste any error messages, if any.

Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install cdrecord

---


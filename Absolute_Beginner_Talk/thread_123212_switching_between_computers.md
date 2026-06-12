---
title: "switching between computers"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by matthewthebig on 2006-01-29
I'm posting this here but i am not sure if it is in the right place. Feel free to move it.

I installed Ubuntu on a 20gig IDE drive in a computer i wasn't using, as I wanted to see what it was like.

I recently decided to add the hard drive to my current computer.

however when i boot it it mentions that there is some sort of graphics error and will only run in the command line.

Is this to do with the change in graphics card?

Any help would be appriciated

---

### Post by mgmiller on 2006-01-29
Almost certainly, this problem is caused by having different graphics cards in the 2 machines.  What was the original card Ubuntu was installed with and what is the card in the new computer?

---

### Post by matthewthebig on 2006-01-29
[QUOTE=mgmiller]Almost certainly, this problem is caused by having different graphics cards in the 2 machines.  What was the original card Ubuntu was installed with and what is the card in the new computer?[/QUOTE]

old: nvidea gfore 2mx
new: radeon x300 se

---

### Post by benplaut on 2006-01-29
if you can get to a command line, login and type

sudo dpkg-reconfigure xserver-xorg

---

### Post by matthewthebig on 2006-02-01
That worked.

thank you very much.

---


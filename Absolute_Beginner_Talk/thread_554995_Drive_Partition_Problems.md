---
title: "Drive Partition Problems"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by oakbz on 2007-09-19
OK, I'm kind of a novice, but heres my deal:
I have 2 hard drives in my PC, 120gig and 500gig.  On my 120 gig I have windows XP home edition, and I installed Ubuntu on my 500gig.  Everything is working great, on start up my PC asks if I want to run in Ubuntu or Windows, however theres a problem with Ubuntu that I can't figure out. 
1.  I can't create new folders in the 500gig Filesystem Ubuntu is on.
2.  On my Ubuntu desktop, there is the 120gig Hard drive, that it seems to be reading off of because I can access all my windows files, (although most dont work on Ubuntu, which is fine)
3. During the Ubuntu install process, I partitioned my 500gig hard drive into 150gigs (Ubuntu saving space), 10gigs (swap) and then 340gigs (free space).  I want to be able to make it so that the 350gig's is able to be read by Windows (BTW windows no longer see's the 500gig drive).  

If that didn't make sense try this.
500gig partitioned in 2 -- 160gigs towards Ubuntu -- 340gigs to Windows

120gig (which is completely full) NOT paritioned -- towards Windows

If anyone can understand my problem, please help me.

Thanks

---

### Post by mysticmatrix on 2007-09-19
> **oakbz said:**
> OK, I'm kind of a novice, but heres my deal:
I have 2 hard drives in my PC, 120gig and 500gig.  On my 120 gig I have windows XP home edition, and I installed Ubuntu on my 500gig.  Everything is working great, on start up my PC asks if I want to run in Ubuntu or Windows, however theres a problem with Ubuntu that I can't figure out. 
1.  I can't create new folders in the 500gig Filesystem Ubuntu is on.
2.  On my Ubuntu desktop, there is the 120gig Hard drive, that it seems to be reading off of because I can access all my windows files, (although most dont work on Ubuntu, which is fine)
3. During the Ubuntu install process, I partitioned my 500gig hard drive into 150gigs (Ubuntu saving space), 10gigs (swap) and then 340gigs (free space).  I want to be able to make it so that the 350gig's is able to be read by Windows (BTW windows no longer see's the 500gig drive).  

If that didn't make sense try this.
500gig partitioned in 2 -- 160gigs towards Ubuntu -- 340gigs to Windows

120gig (which is completely full) NOT paritioned -- towards Windows

If anyone can understand my problem, please help me.

Thanks

1) You can use as much space is available under your HOME folder, all other places are meant for Administrative purposes.

2) Use Add/Remove and install ntfs-3g application to enable writing to Windows.

3) Have you checked by disk management under Windows that there exists the 500 GB drive or not?

---

### Post by forestpixie on 2007-09-19
you can use [this]("http://www.fs-driver.org/") to read linux files in windows

---

### Post by oakbz on 2007-09-19
I don't want to be able to save to my windows drive, I want the window's drive to be completely seperate. 500gig partitioned in 2 so that I can write on 340gigs through windows, and 160gigs through Ubuntu.  And no, I do not see the 500gig drive in windows.

---

### Post by oakbz on 2007-09-19
anyone know how do accomplish this?

---

### Post by mysticmatrix on 2007-09-21
> **oakbz said:**
> anyone know how do accomplish this?

Accomplish what? Can you state your goals more clearly....

Are they 
A) I want windows to see my 500 GB harddrive?
B) Ubuntu cannot write/read form the 160GB partition I made.

Please be a little more specific.

---

### Post by oakbz on 2007-09-21
yes, I would like to accomplish both of those.  I would like to be able to write to the 160gig partition in Ubuntu, and I would like to use the free space left on the 500gig to be writeable by windows.

---

### Post by oakbz on 2007-09-24
mysticmatrix, do you know how to write to the 160gig partition with ubuntu, and use the free space left to write with windows?

---


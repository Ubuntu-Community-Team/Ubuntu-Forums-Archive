---
title: "PSP says it only has 2.7mb of free space but there 1108mb"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2008-01-12
1. Whenever I hook my PSP up to Ubuntu it says that I only have 2.7mb of free space but the PSP and Windows say it has 1108mb. It won't let me add things to my PSP with Ubuntu (Unless there under 2.7mb I guess) But it will in Windows. I tried switching the mem stick from my 4gb to my 1gb and the 1gb says theres 404mb like there really is so it has something to do with the 4gb mem stick.
Does anyone now how to fix this? I've tried rebooting my PC and the PSP and it still won't work right.. So any ideas?

2. Whenever I hook my PSP up to Ubuntu, Music Player comes up and this just annoys the living crap out of me how can I make Ubuntu quit doing this?

---

### Post by microsoft92sucks on 2008-01-12
Can someone please help me...

---

### Post by KuriKai on 2008-01-12
I had the same problem, It happend after I deleted something from the memory stick via the psp rather via ubuntu. I fixed it by copying everything and then formating the memory stick ans copying everything back on

---

### Post by microsoft92sucks on 2008-01-12
Thanks for the help...
I'll try it later I'm sure it will work, I don't know why I didn't think of it.
But good idea and thanks.

---

### Post by bitterbug on 2008-01-13
Open a terminal and do

```
ls -al
```

on the PSP. Chances are you have a .trash folder that you can't see that has files in it.

---

### Post by microsoft92sucks on 2008-01-13
No it wasn't the trash I had already checked and emptied it...
But backing up all the files and folders then formating then replacing the files and folders fixed it... But thanks...

---

### Post by waynebruce on 2008-02-17
Hey I responded with this to another posting with the same problem.  I think you may have misunderstood what Bitterbug meant when he said empty the trash folder....

Instead of reformatting; next time just go to the root/home/whatever you call it folder and press "ctrl + h" which will hide/show all hidden folders and files. You'll notice a folder entitled OWNER-trash (where owner is your name). Just delete it or empty it and you can avoid having to reformat your memory stick every time.

That's almost for sure your problem, I'm far from being an expert but I'm almost positive (through trial and error) that it happens with most removable media (or at least with my setups and such).

---

### Post by microsoft92sucks on 2008-03-12
Again thanks for the help
But I'm not such a Noob that I thought the trash was empty when it wasn't
it WAS NOT the trash
This same problem has happened to me 2 or 3 times 
It's some sort of weird glitch

---

### Post by andraycho on 2008-03-20
I have the same problem.  

Some posters do not understand that this problem happens when the
files are deleted from PSP. In that case, there is no .trash directory left in the flash
so there is no fix other than reformatting the flash.

I'll remember to remove the files through USB not PSP from now on.

---

### Post by Dedmon on 2008-04-06
I was having the same issue with Ubuntu misreporting the free space after deleting files on the memory stick using the psp. Check out this thread - [PSP Memory Stick Free Space Error - http://ubuntuforums.org/showthread.php?t=665451&page=2]("http://ubuntuforums.org/showthread.php?t=665451&page=2")

---


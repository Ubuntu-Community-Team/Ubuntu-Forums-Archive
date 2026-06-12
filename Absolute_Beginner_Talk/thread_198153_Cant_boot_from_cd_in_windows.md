---
title: "Cant boot from cd in windows"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by RedKing on 2006-06-16
Hi

I am trying to install Ubuntu on a windows XP Desktop.
I have downloaded Dapper Drake .iso and burnt it onto a cd-r as an iso file.
I have also changed the boot order on the BIOS to boot from the Cd-rom first, but still can't get it to load, as in it only boots into windows.

I downloaded CDBurnerXP Pro 3 and added the .iso as a file to be burnt, the options to burn as were Joliet, ISO level 1, or ISO level 2 .
I burnt it as an ISO level 2. 


Any Help is appreciated.

Roger

---

### Post by rado_london on 2006-06-16
Try Nero. That is the only program I hadnt got problems with.

---

### Post by jeroen2 on 2006-06-16
Make sure you don't just burn the iso file to cd. Most burning programs have an option similar to "burn image" (nero). You need to find this option in your program. There's a big difference between burning a file to a cd and burning a cd according to an (iso) image.


~Jeroen

---

### Post by RedKing on 2006-06-16
I don't have nero and feel that the image/burner is not the real problem.

The "CDBurnerXP Pro 3" is the one reccomended by ubuntu to burn the image (its free and legal).

Is there any way that i can check the cd to see if it is burnt correctly?

---

### Post by jeroen2 on 2006-06-16
Another tip: if you're properly burning an image file, you won't have to choose a filesystem (Joliet, ISO level 1, or ISO level 2), the image file itself will indicate the proper filesystem. 


~Jeroen

---

### Post by jeroen2 on 2006-06-16
If you insert the cd in windows and look at it's contents, what do you see?

~Jeroen

---

### Post by RedKing on 2006-06-16
i see that its size is 714,594KB and its file type is ISO file

---

### Post by jeroen2 on 2006-06-16
If you see the iso file on the cd, that means you didn't properly burn it as an image. Do you understand the concept of an image? It's like an archive of an entire cd in a single file. You shouldn't burn the iso file to cd, but rather instruct the burningprogram to build a cd from the archive inside the iso file. 

If you give me an oversight, (maybe screenshot) of the program's menu's I might be able to point you in the right direction.

Also, you can reach me on irc (freenode) in #ubuntu for chat or priv msg me to get my msn...


~Jeroen

---

### Post by RedKing on 2006-06-16
Jeroen

Thank you. I looked back at the options on the burner tool and found one that lets me "Write disc from ISO file". This is currently being done.

I will try to install when its written.

Rgs
Roger

---

### Post by rado_london on 2006-06-16
[QUOTE=jeroen2]If you see the iso file on the cd, that means you didn't properly burn it as an image. Do you understand the concept of an image? It's like an archive of an entire cd in a single file. You shouldn't burn the iso file to cd, but rather instruct the burningprogram to build a cd from the archive inside the iso file. 

If you give me an oversight, (maybe screenshot) of the program's menu's I might be able to point you in the right direction.

Also, you can reach me on irc (freenode) in #ubuntu for chat or priv msg me to get my msn...


~Jeroen[/QUOTE]
Why private people? Isnt the forum the place to help people? And can you please post a screenshot with the contest of the cd?

---

### Post by rado_london on 2006-06-16
[QUOTE=RedKing]Jeroen

Thank you. I looked back at the options on the burner tool and found one that lets me "Write disc from ISO file". This is currently being done.

I will try to install when its written.

Rgs
Roger[/QUOTE]
You figered it out. SOrry for not getting the last post.

---

### Post by jeroen2 on 2006-06-16
[QUOTE=rado_london]Why private people? Isnt the forum the place to help people? And can you please post a screenshot with the contest of the cd?[/QUOTE]


Offtopic:

I thought I might be able to help better if I could answer questions directly through irc or msn. And of course I'm not going to post my msn details on a publicly accessible website like this...


~Jeroen

---

### Post by rado_london on 2006-06-16
[QUOTE=jeroen2]Offtopic:

I thought I might be able to help better if I could answer questions directly through irc or msn. And of course I'm not going to post my msn details on a publicly accessible website like this...


~Jeroen[/QUOTE]
Well I did as you can see my sig. I bet you had troubles with giving away personal info. And the forums are the best IMO to give advise.
EDIT: LOL-Beans: 500. I cant beleive it though!

---

### Post by RedKing on 2006-06-18
Thanks to all.

Instructing the burner tool to "write disc from image" did the trick.

Thanks again

---


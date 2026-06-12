---
title: "Help Kernel Panic"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Chris2169 on 2008-01-20
Hopefully this isn't as bad I think it is !  I was following some instructions to try and speed up my boot time.  Now I can't boot ubuntu at all ! I tried in rescue mode and got the follwoing as the last line;

[10.525682] Kernel Panic not syncing: VFS: unable to mount root fs on unknown-block (0.0)

I've booted the machine into XP to get online again,  any help gratefully received !  (I know, the moral of the story is don't fix it if ain't broke !!!!)

Thanks

Chris

---

### Post by Ub1476 on 2008-01-20
Do you have a link to the instructions you followed?

---

### Post by Chris2169 on 2008-01-20
Yep,

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

I guess I've typed something wrong !

---

### Post by Ub1476 on 2008-01-20
Alright, very good. Now you just need to grab a live CD, boot it up, and revert the files to their original settings. Make sure you access the installed filesystem and not the one on the CD.

BTW, if you are able to access the terminal by choosing "safe mode", then pressing ALT/ALT Gr+F? (probably F1),  you wouldn't need to boot the live CD.

*I don't remember the exact key to enter the terminal so you might do some googling about it, if no other rescue come here:p*

Next time I suggest you use *startupmanager* to configure your boot splash:)

---

### Post by Chris2169 on 2008-01-20
Ok I'm making progress,

I've found the offending file and I can open it with a text editor.  However because I"m using the CD I don't have the necessary permission to change the file contents !  I'm sure there is a very easy way to log in as 'me' through the CD but I'm so completely in the dark with Linux I haven't a clue how to !!!! (its only my 3rd day of using it and yes I will buy a book and learn to do it properly before I make any more schoolboy errors !).  Thanks again

Chris

---


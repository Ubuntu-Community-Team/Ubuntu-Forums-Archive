---
title: "Force Kill"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by purpleaffro on 2005-05-28
Hi,
How do i force a program to shutdown? cuz this one program amsn just everyonce in a while freezez but everything else is fine, and i can't close it normaly is there a way to make it quit? i tried the system monitor but i don't even see it listed there.

Thanks,

Jeremy,

---

### Post by the_clown on 2005-05-28
[QUOTE=purpleaffro]Hi,
How do i force a program to shutdown? cuz this one program amsn just everyonce in a while freezez but everything else is fine, and i can't close it normaly is there a way to make it quit? i tried the system monitor but i don't even see it listed there.

Thanks,

Jeremy,[/QUOTE]
 Right click on one of your panels, select *add to panel*, then drag *force quit* to the panel

---

### Post by bored2k on 2005-05-28
[QUOTE=the_clown]Right click on one of your panels, select *add to panel*, then drag *force quit* to the panel[/QUOTE]
 Or  pressa alt+f2 > xkill

---

### Post by Uber_Nick on 2006-04-25
[QUOTE=the_clown]Right click on one of your panels, select *add to panel*, then drag *force quit* to the panel[/QUOTE]

I froze my panel :-(
Any other suggestions?

---

### Post by muz1 on 2006-07-29
A friend of mine asked me to check out Azureus.
Anyway, I installed it and then it threw up a 'WARNING Azureus did not shut down tidily' in the bottom right hand corner. I used the kill app icon but it would not remove either of them.

Is there a way of telling it to shutdown no matter what?

Cheers
muz

---

### Post by estel2000 on 2006-08-04
Howto forcequit or kill an application:

- Press alt+F2 (press first alt, keep it holding while pressing F2)

- enter in the dialog "xkill" (without the "s) to run the program xkill.

- your mouse cursour will change into a death's head. Now click on a window of the application that's crashed to kill it.

---

### Post by Soulstorm on 2006-08-11
Aww... sweet, this worked perfectly!

Thank you!

---

### Post by A2A on 2006-08-11
You could also try this in a terminal:
```
ps aux | grep <program-name>
``` This command will list you the pid # for the program.
Then type this in the terminal:
```
kill -9 <pid # to kill>
``` 
Regards,

---


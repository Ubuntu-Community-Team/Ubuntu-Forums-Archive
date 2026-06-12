---
title: "Slow startup"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by wolf3491 on 2008-04-07
I found other posts from people with the same problem, and the reply was to  change the numbers in /etc/usplash.conf to the right resolution.  I'm missing something I guess, because when I try to save, it wont save and tells me I dont have proper authorization.  How do I save it?  And any other ways to speed up boot?

---

### Post by InfinityCircuit on 2008-04-07
You need to edit the file with the correct permissions:

```
gksu gedit /etc/usplash.conf
```

For more tips on speed check out [http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)

---

### Post by Fate Reconciled on 2008-04-07
Also, you can download Start-Up Manager. Fairly useful.

Download here: [apt://startupmanager]("apt://startupmanager")

OR

sudo apt-get install startupmanager

---

### Post by wolf3491 on 2008-04-07
I dowloaded and installed it, no difference except the color of the loading splash are no inverted =( how do i fix?

---

### Post by wolf3491 on 2008-04-08
Please help, the new splash makes me nervous for some reason =/  also, how do I change the splash to a different one?

---

### Post by wolf3491 on 2008-04-08
Bump?  Sorry, I just dont know if this is a bad thing for the splash's colors to be inverted. =/

---

### Post by Fate Reconciled on 2008-04-10
I don't know why the colors are inverted. Are you sure you have the correct resolution set? I use Ubuntu Tweak to play around with splash. But now I just leave it disabled.

---

### Post by wolf3491 on 2008-04-10
well, I chose the closest option to what I actually use, that might have made the difference.

---


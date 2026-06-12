---
title: "Losing command line prompt."
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by evildork on 2008-01-08
After I start a program from the terminal, it won't return me to the prompt.  And if I close the terminal, the program closes, too.  To continue to work in both the program and the terminal, I have to open new tabs.

Why can't I just keep going with the prompt on the same tab after I open something?  Why can't I lose the terminal and keep the program open?  Why doesn't it do this by default!?

---

### Post by hyper_ch on 2008-01-08
> **evildork said:**
> Why can't I just keep going with the prompt on the same tab after I open something?  Why can't I lose the terminal and keep the program open?  Why doesn't it do this by default!?

Because that's the defined default behaviour of the termina. What program do you run from the terminal then?

GUI programs will be in your menu

Shell programs don't need to run as GUI...

---

### Post by chuckyp on 2008-01-08
It should return you to the terminal after the program is done running.  I believe what you are looking for is the &&  symbol at the end of the executable.  ex:
```

$gedit &&
$

```

Also you can hit alt+f2 to bring up a run dialog.

---

### Post by Joeb454 on 2008-01-08
also to run a program from the terminal and keep both separate, you could do the following (using gedit as an example)
```
(gedit &)
```

I use it all the time :)

---

### Post by jordanmthomas on 2008-01-08
Note that if you use **program&** to launch a program if you use the x in the titlebar to close your terminal, the **program** will die too.  To close a terminal and keep **program** runninng, press ctrl - d in the terminal or type exit in the terminal.

---

### Post by evildork on 2008-01-08
Thanks, Joe, exactly what I wanted.

---

### Post by Joeb454 on 2008-01-08
No problem :) and **jordanmthomas** the method I described works even if you use the "x" to close the terminal, I know that for a fact (I've just tried it to make sure as well :p)

And don't forget you can mark the thread as solved **evildork** using Thread Tools (up at the top of the page)

---

### Post by jordanmthomas on 2008-01-08
> **Joeb454 said:**
> No problem :) and **jordanmthomas** the method I described works even if you use the "x" to close the terminal, I know that for a fact (I've just tried it to make sure as well :p)

I believe you, but it doesn't work for me, tried it with gedit and closing terminal closed gedit.  No big deal, and it could just be a difference in me using zsh in arch and you using bash in ubuntu.

---

### Post by Joeb454 on 2008-01-08
Yeah that'll be the difference then, lol. I've not really checked zsh out that much, looked into it briefly, but bash does all I need for now...plus it's on all the *nix machines at Uni

---


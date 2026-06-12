---
title: "openoffice.org calc"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-08-26
Can someone tell me how to make a user defined function? I have 4 cells with homework avg, quiz avg, test avg, and exam avg. I need to calculate a grade with homework and quiz worth 15%, test worth 30%, and exam worth 40%. I know how to use the predefined functions but cannot figure out how to define my own functions. Where is that option?

Thanks for the help.

---

### Post by jimrz on 2006-08-26
> **beamo said:**
> Can someone tell me how to make a user defined function? I have 4 cells with homework avg, quiz avg, test avg, and exam avg. I need to calculate a grade with homework and quiz worth 15%, test worth 30%, and exam worth 40%. I know how to use the predefined functions but cannot figure out how to define my own functions. Where is that option?

Thanks for the help.

you could always enter it in a new cell with your own formula to calulate the grade from the other 4.

something like ```
=((homework avg * .15)+(quiz avg * .15)+(test avg * .3)+(exam * .4))
```

using the cell id rather than the name of your 4 cells you want to base this on

---

### Post by beamo on 2006-08-26
Thanks, jmrz, I see how that works now. Is there any way to save that function so I can do the same thing for the next 30 kids on the list without retyping it everytime? I'm sorry, I am new at this. ](*,)

---

### Post by nanotube on 2006-08-26
yes, just click on the lower right hand corner of the cell you have the formula in (it will have a little thick box in that corner), and drag down the list, and the formula will be autofilled.

or, you could also copy that cell, then select the other cells you want it to go to, and paste.

i take it that you are generally not very familiar with spreadsheets? (since the procedure is the same for ms excel, openoffice calc, and gnumeric)...

---

### Post by beamo on 2006-08-26
Thanks. No, I'm not at all familiar with spreadsheets but am trying/need to learn how to use them. Thanks again :wink:

---


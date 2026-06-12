---
title: "Ubuntu 20.04 - screen brightness Macbook late 2008"
date: 2020-09-04
forum: Apple Hardware Users
---

### Post by akimann on 2020-09-04
Hi all,

first **"Hallo @all"** I´m new to the forum [B]:)

[/B]Now my question:
I upgraded to version 20.04 some days ago on my Macbook late 2008 and it seems there is no possibility to change the brightness of the screen.
in version 19.xx there was a slider in the settings as far as I remember and I was able to use the Fn keys oder F1/F2 keys to set the brightness.
But in 20.04 there is no slider and the keys dont work. The keys for keyboard illumination still work fine.

Did I miss the slider and it is still there or is the Macbook too old to get support in Ubuntu 20.04. 
Btw. it runs really good on the old Macbook.

Thanks in advance.
akimann



**EDIT:**
found a solution for the ones who have the same problem
[https://www.how2shout.com/how-to/how-to-change-screen-brightness-in-ubuntu-using-command-terminal.html](https://www.how2shout.com/how-to/how-to-change-screen-brightness-in-ubuntu-using-command-terminal.html)
with the MB late 2008 it is:

```
xrandr --output LVDS-0 --brightness 1
```

---


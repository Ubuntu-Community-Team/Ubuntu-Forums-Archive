---
title: "Changing System Configuration When Logging In"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Dragonlaw on 2008-04-02
Hello,

I would like to say that I have been quite impressed with Ubuntu and the community support. I hope that you'll be able to bear with my question because I'm really new to this and have not been able to find the answers after searching.

My problem is that after I login with my username, I will be prompted that the date and time seems to be inaccurate "Jan 1 2003 something". When I click on Modify, the screen will then open a window saying that I am not allowed to change the system configuration. After that the screen will go blank.

Much thanks in advance to everyone who has been working hard to make Ubuntu a success.

---

### Post by Tatty on 2008-04-02
If your system time keeps resetting itself then the CMOS battery might need replacing on your motherboard.

Im not sure what is going wrong when you click "modify".  what version of ubuntu are you currently running?

---

### Post by Dragonlaw on 2008-04-02
I'm using an Acer SA85 DESKTOP and using Ubuntu 7.10.

After that the window prompt that my date and time is wrong and asks me to either "ignore" or "Modify". If I click on Modify then it will say that I do not have permission to change the system configuration.

When I ignore it then I can change the clock settings, but after restarting the same problem will occur.

Thank you very much for your attention!

---

### Post by Tatty on 2008-04-02
Well it definately sounds like you need to change the battery on your motherboard - this is why the date keeps resetting (it needs a battery to keep the clock ticking on when your comp is off)

So to solve this problem - [replace the battery]("http://www.computerhope.net/issues/ch000239.htm")

As to why it wont let you modify as you boot in, i am not sure.  Perhaps it is a bug...

At least you can change the time after booting in, so that is a work around.  Perhaps post a bug report in launchpad if there isnt already one...

---


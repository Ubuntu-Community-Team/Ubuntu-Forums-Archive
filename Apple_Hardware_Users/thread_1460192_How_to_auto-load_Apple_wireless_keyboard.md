---
title: "How to auto-load Apple wireless keyboard?"
date: 2010-04-22
forum: Apple Hardware Users
---

### Post by kramer65 on 2010-04-22
This morning I bought an Apple wireless keyboard and I got it connected through Blueman. It works like a charm, but I have on problem;

When I log out I can log back in by typing in my password. However, when I restart the computer it seems that bluetooth is not loaded yet and I cannot enter my password. So I have to log in using my wired keyboard, and then disconnect & re-connect to my wireless keyboard using blueman before I am able to use the wireless keyboard.

Does anybody know any solution to this problem? Is there any way that I can already auto-load bluetooth and connect to my keyboard before I log in?

---

### Post by xvila on 2010-04-22
It takes a little bit to load 
Just press any key once or twice (to wake it up) and wait for approx. 5 seconds

Yes, it's annoying, but this is the way it works in my case

xavi

---

### Post by kramer65 on 2010-04-23
Hi xavi. Unfortunately that is also not the case with me. I can wait for 10 minutes and nothing happens. Even after I login and wait I cannot use the keyboard. I really have to go into blueman to manually disconnect and reconnect the keyboard, before I can use it.

Does anybody have any idea what could be the problem here?

---

### Post by picklecolor2 on 2010-05-08
One thing that's helped me with mine in the past it to add hid_apple to /etc/modules.  If I don't I get no goodness at startup.

---

### Post by kramer65 on 2010-05-08
That is great! Thank you so much!

---


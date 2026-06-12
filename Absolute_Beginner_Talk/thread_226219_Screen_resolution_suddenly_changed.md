---
title: "Screen resolution suddenly changed"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by OU812 on 2006-07-31
Hello. Ubunutu (and kubuntu) keep changing my resolution to a much lower setting. So I did

sudo dpkg-reconfigure xserver-xorg

three times, rebooting after each attempt. This had absolutely no affect on the resolution: It's still too low. I really want to keep (k)ubuntu on my machines, but if the resolution keeps changing and there's no way to fix it, ubuntu is going to be a tough sell for me. Thanks.

john

---

### Post by Dr. Nick on 2006-07-31
Did you alter what monitor you choose?

Here is a link that may help some

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

---

### Post by OU812 on 2006-07-31
Thanks. When I first installed ubuntu, the screen resolution was too low. So I edited xorg.conf (using sudo - oops) by changing the monitor's horizsync and vertrefresh settings. A few days later the resolution was low again. So I ran the command described above. As you know, nothing happened. But I did get it fixed, here's how:

At the end of the process it noticed that I changed my monitor resolution settings and asked if I wanted the new settings written to the file - I said yes. (That was the mistake.) The third time I tried to reconfigure I chose no. This meant that no settings were written to xorg.conf. So I edited (using gksudo) the file (by writing the settings in) and rebooted. Back to normal.

So your post jogged my memory. Thanks.

john

---


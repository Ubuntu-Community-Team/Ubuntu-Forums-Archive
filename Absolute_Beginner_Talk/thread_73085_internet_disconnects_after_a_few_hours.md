---
title: "internet disconnects after a few hours?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Moonstruck on 2005-10-08
Hello, complete linux newbie here and this is my first post on the forums...

Now I've done a search of posts around here and come up with absolutely no reason why my internet should simply fail after a few hours of use. I've noticed that using Linux my messengers tend to disconnect more than usual, but this problem is a little irritating.

It happens every time I reboot. Some time afterwards, my internet just stops, period. Can anyone give me some pointers on how to fix this? I know it's probably something simple. :)

Thanks.

---

### Post by adwait on 2005-10-08
It is possible that your resolv.conf is getting over after some time. Try the command
```
cat /etc/resolv.conf
```

Try it when you net is working and try when it stops working.........any difference?

---


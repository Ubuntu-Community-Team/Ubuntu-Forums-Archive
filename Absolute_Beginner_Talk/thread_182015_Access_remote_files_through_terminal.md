---
title: "Access remote files through terminal"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Titus A Duxass on 2006-05-25
Hi all,
I have 4 PCs and a Laptop all running Breezy, all with ssh installed, all with static IPs.

I can access all desktops from all PCs.

I want to edit mythtv themes in 192.168.2.51 from machine .102 through a terminal as root but I don't know how to navigate to the remote machine.

Any pointers would be appriciated.

Thanks

---

### Post by AndyCooll on 2006-05-25
From a command line type

```
ssh yourname@192.168.2.51
```

That'll log you on to the remote pc on the command line. Now you should be able to navigate around and use sudo as usual on that box.

:cool:

---

### Post by Titus A Duxass on 2006-05-25
Thanks,
That was one of the combinations I did not try.

Works a treat.

---


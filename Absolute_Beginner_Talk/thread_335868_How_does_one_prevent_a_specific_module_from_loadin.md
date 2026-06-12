---
title: "How does one prevent a specific module from loading?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by PatrickMay16 on 2007-01-10
Hey guys! 

The wireless card in my laptop works out of the box in ubuntu, using the acx driver module; however it doesn't perform very well. So I got the windows driver and have loaded it using ndiswrapper, and I find that it works better.

So, what I want to do is stop the driver module "acx" from loading. I think this is called 'blacklisting', but I have no idea on how to do it. 

If anyone can help me with this, I'd be very happy.

---

### Post by SkyNet2029 on 2007-01-10
I think what you are looking for is 'modconf'

```
$sudo modconf
```

The dialog is self-explanatory...Check the module you want to configure..If it is 
listed as loaded with kernel modules, then you will get a prompt to remove it from 
being loaded with kernel modules.

At next boot, it should not be loaded , as specified from your dialog with modconf.

---

### Post by PatrickMay16 on 2007-01-10
Thanks for the reply, but unfortunately I got a "command not found" error when trying modconf; I guess you'd need to install it seperately.

No matter, though, because I read at another forum how to do it; 

Adding to this file:
/etc/modprobe.d/blacklist

text like this:

```

blacklist nameofmodule

```

And that did the trick.

Thanks once again.

---


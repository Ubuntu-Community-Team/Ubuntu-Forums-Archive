---
title: "Login errors"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-08-07
When boot up the computer, a login screen usually comes straight on, but now I get a strange error saying that that loging screen is crashing and it is trying a different login.  It then opens up a very different login screen ( I think it's the gnome native login window).  It works just fine, but I don't want an error screen every time I turn on the computer.  Can someone help me out?  Why is it doing this?

---

### Post by rdd on 2006-08-07
could you try to post the actual error. Even if it's strange, it might point us some direction. 

Regards

rdd

---

### Post by CeeDub on 2006-08-07
Exacts words of the error window:

"The greeter application appears to be crashing.
Attemting to use a different one."

---

### Post by joypunk on 2006-08-07
I'm getting the same message. Started appearing 4 days ago. Only thing I can think of that's related is that I had switched my computer to no longer require a login on bootup (System -> Login Window -> Security tab, checked 'Enable Automatic Login').

The problems began when I changed my mind on that and unchecked that box (disabling Automatic logins).

---

### Post by rdd on 2006-08-08
Hmm, I can't really find anything on this problem. The alternative login that comes up, is it graphical as well? i.e. in your desktop resolution?

If it is not, this could point to an xorg-problem. If it is, you might try doing

```
sudo dpkg-reconfigure gdm
```

to reinstall the display manager.

Any other hints you maybe stumbled on?

Regards 

rdd

---


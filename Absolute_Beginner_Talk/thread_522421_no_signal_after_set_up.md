---
title: "no signal after set up"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by camlost on 2007-08-10
Alright. I was setting my screen resolution with
dpkg-reconfigure xserver-xorg

and when I restarted my computer the stopped receiving a signal right when I usually log in. Is it possible to recover, any ideas? Or am I going to have to reinstall unbuntu and start over.  I really just installed fiesty today, so its not a big loss. 

Thanks

---

### Post by kyphi on 2007-08-10
I would reinstall.

If you need to adjust your resolution you are better off to use this code:
```

# dpkg-reconfigure -phigh xserver-xorg
```

Use up/down arrows to find the resolution you want and press the spacebar to select.

It is always a good idea to state which version of Ubuntu you are using.

Good luck.

---


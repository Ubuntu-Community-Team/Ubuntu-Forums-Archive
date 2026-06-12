---
title: "Ubuntu starts with text mode only"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Mosaab on 2008-04-07
I have a problem that ubuntu starts ommand based only,
and when I type startx  it gives me an error message.

I want to say that the problem is that I wanted watch a movie on my TV so I missed around with graphical tool in prefrences. and I think that this is whats causing the problem. I didnt touch any thing else other that this.

I dont know if this helps... but when I type "runlevel" it outputs "N 2"

is there a way to reset the configurations?

Thanks

---

### Post by nonewmsgs on 2008-04-07
have you been running normally before?

did you just install the Ubuntu Server instead of the Ubuntu Desktop?

---

### Post by TeoBigusGeekus on 2008-04-07
Type 
```
sudo dpkg-reconfigure xserver-xorg 
```
to reconfigure your xserver.

---


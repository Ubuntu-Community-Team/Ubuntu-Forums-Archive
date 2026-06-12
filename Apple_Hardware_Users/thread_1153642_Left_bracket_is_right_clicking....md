---
title: "Left bracket is right clicking..."
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by transmition on 2009-05-09
I have a 4,1 Macbook, and for some reason, whenever I press by left bracket ---[---, it is the equivalent of right clicking.

I have setup my .xmodmap to allow my control key to right click, and I am wondering if this might be the problem.

My .Xmodmap:
```

keycode 133 = Control_L
add Control = Control_L
keycode 134 = Control_R
add Control = Control_R
keycode 37 = Pointer_Button3

```

As well, xev outputs this when I use my left bracket key:
```

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  4294967212 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

Which is the same output as that of my control key. Help.

---


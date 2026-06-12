---
title: "Installed the ATI 8.27.10 drivers and now glxgears is slow"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-28
Ok, my fault. I should have waited to see what others had to complain about first but I was impatient - I installed the new drivers as soon as I saw it. Now my glxgears score is about 200+ fps, before it was about 10,000+. 

What did I do wrong and how do I fix it? :( :confused: 

[ATTACH]13386[/ATTACH]

Yes, I acknowledge this tool is not a benchmark, but a drop that large can't be right.

---

### Post by Anduu on 2006-07-29
Are you sure they are installed correctly?

Type fglrxinfo in a console and see what it says...should be similar to this

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

Personally I stay away from ATIs driver(nothing but problems...) and just use the xorg-driver-fglrx from the repos.

---

### Post by synd7 on 2006-07-29
This happend to me as well.
from 4500 down to 150

oddly, fgl_glxgears is at 750 fps, slightly higher than with the 8.26.18 drivers.

Try benchmarking using a game, maybe glxgears just doesnt like the new drivers.

Edit:
```
ben@ben-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.5946 (8.27.10
```

Thats my results, looks like their installed right.

---

### Post by Cherry Popper on 2006-07-29
> **Anduu said:**
> Are you sure they are installed correctly?

Type fglrxinfo in a console and see what it says...should be similar to this

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

Personally I stay away from ATIs driver(nothing but problems...) and just use the xorg-driver-fglrx from the repos.
Well, I'm pretty sure I installed them correctly, my fglrxinfo is similar to yours, see the pic I posted. :)

> **synd7 said:**
> This happend to me as well.
from 4500 down to 150

oddly, fgl_glxgears is at 750 fps, slightly higher than with the 8.26.18 drivers.

Try benchmarking using a game, maybe glxgears just doesnt like the new drivers.

Edit:
```
ben@ben-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.5946 (8.27.10
```

Thats my results, looks like their installed right.

Looks like I'm not alone. :p Maybe you're right, glxgears doesn't like the new drivers. 

I don't have any games installed on Ubuntu, it's all on my Windows partition so I can't check. Sorry. :oops: 

Anyway, thanks for the replies.

---

### Post by Frank Golden on 2006-07-29
> **Cherry Popper said:**
> 
Yes, I acknowledge this tool is not a benchmark, but a drop that large can't be right. Read the following

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by Kilz on 2006-07-29
What version of the drivers did you have before? What instructions did you follow to upgrade to the 8.27.10 drivers?

---


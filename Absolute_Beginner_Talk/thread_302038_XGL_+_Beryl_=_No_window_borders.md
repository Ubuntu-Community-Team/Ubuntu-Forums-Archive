---
title: "XGL + Beryl = No window borders"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by SZorg on 2006-11-18
I just installed Beryl and XGL and, whenever I enable it, I have no window borders (no title bar, no borders to click-drag for resizing)? The other effects and everything else work fine? Anyone know what's wrong?

---

### Post by sylverwing on 2006-11-18
Hy SZorg,

I had the same problem and what worked for me is;

type

```
killall emerald
```

then in the Beryl Manager select

"Reload Window decorator"

this bug came up with version 0.1.1

I don't know how to make this permanent. Probably you can run this in a sort off script with login manager. But I'm no expert :)  

Hope this works for you ;)

EDIT:

found this also

[http://www.ubuntuforums.org/showthread.php?t=284154&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=284154&highlight=beryl)

---

### Post by Seti on 2006-11-18
I had the same problem and fixed it by installing beryl-manager and making sure it was in System > Preferences > Sessions > Startup Programs tab, add beryl-manager and then restart x.

---

### Post by mtgrocks04 on 2006-11-18
I had the same problem...beryl-manager fixed it for me too...

---

### Post by SZorg on 2006-11-18
Thanks for the help, but none of this has fixed my problem. :[.


I also noticed, now, (and this may be wrong) that my refresh rate for 1280x1024 won't go above 54hz. My monitor, though, reports that it's using 75hz. That's not a big deal though.

---

### Post by SZorg on 2006-11-18
For anyone else having the problem and not finding a fix, add this to xorg.conf:


```

Section "Screen"
   Option         "AddARGBGLXVisuals" "True"

```

---

### Post by gejr on 2006-11-20
I read that you should put this tiny script in your startup sessions:

```
 
!#/bin/bash

killall emerald 
sleep 2
emerald


```


Save the script as whatever you like, then

 ```

chmod 755 *yourscript*

```

finally, put it in your sessions startup programs.
this works fine for me.. :)

---

### Post by cvmostert on 2006-11-29
I also could not see borders...

after reading this post... 

killall emerald dit NOT work... emerald never started so by running

emerald

suddenly my borders appeard!

thanks!

how do i make a shortcut running two commands..

& beryl-xgl, emerald

cheers.

---


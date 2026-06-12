---
title: "left speaker problem macbook c2d works only after suspend"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by dustynus on 2008-05-20
Hey, I used the fix on Post 9, Thanks to Volanin.
[http://ubuntuforums.org/showthread.php?t=611345](http://ubuntuforums.org/showthread.php?t=611345)

My sound gets fixed Only when I suspend my computer, then take it out of suspend. I've been living like this when I want to play music. But I'm wondering if there's a way to make it do this whatever it isthat fixes this (if someone's done the same) on boot.

I'm on a macbook 2,1 c2d, on 8.04 (i had to use 
{  options snd-hda-intel model=macbook-v3 position_fix=2 probe_mask=1   }
to fix the problem.

---

### Post by volanin on 2008-05-20
Yeah, I also had this problem you are having. It's annoying.
But now with hardy, it's seems to be gone.
Anyway, you don't have to suspend...

You just have to unload and load the sound module again.
And doing it during boot used to solve this problem for me.
It is quite a hack, but put these lines in */etc/rc.local*

```
modprobe -r snd_hda_intel
modprobe snd_hda_intel
```

Give it a try, it *might* work! This problem is already fixed in
kernel 2.6.25, so Intrepid will come with a proper and definitive fix!
:)

---

### Post by dustynus on 2008-05-21
Nope, loading it in rc.local didn't seem to work. If i try manually I get:

FATAL: Module snd_hda_intel is in use.


Is there a way to get around this ?

Thanks :guitar:

---


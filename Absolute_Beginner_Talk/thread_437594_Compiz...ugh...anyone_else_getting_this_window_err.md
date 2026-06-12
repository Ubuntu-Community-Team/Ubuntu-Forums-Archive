---
title: "Compiz...ugh...anyone else getting this window error?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-08
Trying this since I have gotten to know Ubuntu a bit the last week.

A lot of times, read: most times, when I maximize a window, the top bar of my theme is there, but the system thinks it's gone.  What happens is I double click it to un-max or click to drag, and it acts like I am clicking my desktop.  So it thinks there is no title bar.

Anyone?

---

### Post by Martin on 2007-05-08
Are you running Desktop Effects or Beryl? I've had similar issues when using either. If you are, turn it off and see if the problem continues

---

### Post by gohanssjn on 2007-05-09
Desktop Effects.  Specifically I've installed GL Desktop - Compiz.

And when it is off, no issues.

Any fix?

---

### Post by sycorax on 2007-05-09
I can at least confirm that bug (Feisty + i810). 
It's a known bug (see [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/95011)](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/95011)). We have to wait for compiz 4.0 :-(

---

### Post by gohanssjn on 2007-05-09
Thanks for that link, I'll try the work-around tonight!

Glad something can be done, because I LOVE cube, but really HATE Wobbly windows.

Thanks again, I'll report back tonight!

---

### Post by gohanssjn on 2007-05-09
Ok, at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/102815](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/102815) is says :

> I belive that this bug is caused by the inclusion of the following patches in 0.3.6-1ubuntu13

020-move-away-from-having-client-side-positioning-of-windows.patch
021-only-update-window-position-when-no-pending-position.patch

Removing these patches (by commenting them out in debian/rules/patches/series) is a fix until an 0.4.0 package is made..

But I cannot find this file.  Anyone know how to access it?

---

### Post by jhenager on 2007-05-09
> **gohanssjn said:**
> Thanks for that link, I'll try the work-around tonight!

Glad something can be done, because I LOVE cube, but really HATE Wobbly windows.

Thanks again, I'll report back tonight!

I tried Compiz but couldn't find any controls for it, so I went back to Beryl. I think it is much nicer, has more options, and you could turn off or on whatever you wanted.
Plus, it was [SIZE="7"]2[/SIZE] steps.

---

### Post by gohanssjn on 2007-05-09
Right, but I don't need half of the stuff Beryl used, and compliz (using GL Desktop) is VERY compact and easy, save this one bug.

---

### Post by gohanssjn on 2007-05-09
Ok, guess I'll try Beryl for a little while and disable everything I don't want/need.

Really, I just want cubes and fades.

---

### Post by gohanssjn on 2007-05-09
Beryl is so much for what I need.  I can't see keeping it.

Any ideas on that file / lines to comment out?

---

### Post by gohanssjn on 2007-05-09
Last bump I guess...

---

### Post by gohanssjn on 2007-05-09
Guess I lied, I can't let this die :)

Here is where I am at since it's a new page:

Ok, at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/102815](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/102815) is says :

> 
I belive that this bug is caused by the inclusion of the following patches in 0.3.6-1ubuntu13

020-move-away-from-having-client-side-positioning-of-windows.patch
021-only-update-window-position-when-no-pending-position.patch

Removing these patches (by commenting them out in debian/rules/patches/series) is a fix until an 0.4.0 package is made..


But I cannot find this file. Anyone know how to access it?

---

### Post by gohanssjn on 2007-05-10
To the top!

---

### Post by gohanssjn on 2007-05-10
You know, I just realized there was a customization forum.  Can this be moved there?

---

### Post by gohanssjn on 2007-05-10
Again. This is really getting to me.

---

### Post by gohanssjn on 2007-05-16
And another bump.  I'd realy like to get rid of those updates if someone can tell me how.

---


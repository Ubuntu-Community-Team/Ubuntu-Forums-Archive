---
title: "New to Ubuntu/Linux, have a few problems."
date: 2007-08-03
forum: Apple PPC Users
---

### Post by namtap on 2007-08-03
Okay, I got everything installed without a hitch (that is, Feisty on a G4 Powerbook).  That part was quite simple.

However, I've been having a few annoying problems.

For one, when I type in text boxes (maybe just in Firefox, though I haven't typed much elsewhere), occasionally, a line of text I may have highlighted before, or a URL I entered, or something like that will just appear out of the blue as if I just copied and pasted it (I didn't.).  Or, maybe I will start typing, and the page will suddenly *(97328621 -- that number just found its way into this message.  It was the last thing I copied, but I certainly did not paste it)* jump up or down.

I'm not sure what could possibly be causing such an oddity.  Perhaps you do?

Secondly, I am trying to disable trackpad tapping, so I did exactly what I was told.  That is,

```
sudo aptitude install powerpc-utils
```

then

```
sudo trackpad notap
```

But, I get this message in return:
*writing /dev/adb: No such device or address*

It's quite irritating, and although I am so far enjoying running Ubuntu alongside OS X, it is proving to be (page just shot down to the bottom, taking me off the text box, here) rather annoying.

Thanks a lot.

---

### Post by Lord Shank on 2007-08-10
I have never has to enter the first command.  I always just sudo trackpad notap, and then save the session.  I have run into problems waking a unit from sleep, if you can get it to.  Its an apple thing, they are great for os x, but the firmware for ppc/linux is hit and miss, especially on the graphics.

---


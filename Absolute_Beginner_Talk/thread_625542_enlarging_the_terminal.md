---
title: "enlarging the terminal?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by tomxyz on 2007-11-28
hello all,

I'm trying to recover some jpeg's files using photorec.
When I do sudo photorec, it says, photorec needs 25 lines to work, enlarge the terminal and start again.

Anybody what it means to enlarge the terminal (it doesn't mean maximize the window because I tried that)

regards Tom

---

### Post by RomeReactor on 2007-11-28
Hi. Just a thought: have you tried to enlarge the terminal by dragging the lower edge (you'll see a box with the current size, and as you drag down the edge, the number increases by lines; if you drag the side, the number increases the column count).

EDIT: Just downloaded and installed Photorec, and encountered the same message; resizing the terminal to at least 25 lines does work).

---

### Post by Sef on 2007-11-28
> Anybody what it means to enlarge the terminal (it doesn't mean maximize the window because I tried that)

That's strange.  I used another program with the same requirement and that is what worked for me.

---

### Post by toupeiro on 2007-11-28
couple of different things you can try.

1:
 ```
setenv TERM vt100
```

or play with the following variables

```

setenv LINES 63
setenv COLUMNS 168
```

If you get the combination you want.  edit a file in your home directory called .bashrc and put the setenv lines you used at the bottom of the file and save it, so its set on every terminal session.  ONLY do this once you've determined the behavior you want.

---

### Post by RomeReactor on 2007-11-28
> **Sef said:**
> That's strange.  I used another program with the same requirement and that is what worked for me.

Good point. Maximizing the terminal worked for me also.

---

### Post by toupeiro on 2007-11-28
> **RomeReactor said:**
> Good point. Maximizing the terminal worked for me also.

  (I thought he said maximizing the terminal didn't work for him???)

alternatively, you can always use <ctrl-alt-F1> - <ctrl-alt-F6> to get full screen terminals.  ctrl-alt-F7 or F8 should bring you back to gnome when you do so.

---

### Post by RomeReactor on 2007-11-28
> **toupeiro said:**
> (I thought he said maximizing the terminal didn't work for him???)

That's correct, it doesn't work for the OP. So perhaps enlarging the terminal won't work for him either, and the problem is elsewhere. As you noted, maybe editing .bashrc can help.

As a side note, I completely forgot about switching to a tty, which also worked, so hopefully one of these options will be of help.

---

### Post by tomxyz on 2007-11-28
hi all,

thanks for the reply's!

I feel a little stupid, maximizing the window doesn't make it work neither dragging the bottom corner to a bigger window. 
It's quit simple really, you can get to maximum screen under the vieuw pulldown menu in the terminal windown itself.
I guess I'm still not completely over microsoft as I tought clicking the maximize icon makes it go as big as possible.

tanks Tom

---


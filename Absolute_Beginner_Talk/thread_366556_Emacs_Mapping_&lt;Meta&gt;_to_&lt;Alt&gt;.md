---
title: "Emacs: Mapping &lt;Meta&gt; to &lt;Alt&gt;"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by gordonsowner on 2007-02-21
Hi,

Relatively new to Linux, and new to Emacs, so I'm not sure if this is a Linux or Emacs question...

I'm trying to learn Emacs, and I think my <Alt> key should act as my <Meta> key.  It is not working.  I'd like to make it work before I continue on with the emacs21 tutorial.

Anybody quickly direct me to how to remap <Alt>?

thanks,

---

### Post by Arndt on 2007-02-21
> **gordonsowner said:**
> Hi,

Relatively new to Linux, and new to Emacs, so I'm not sure if this is a Linux or Emacs question...

I'm trying to learn Emacs, and I think my <Alt> key should act as my <Meta> key.  It is not working.  I'd like to make it work before I continue on with the emacs21 tutorial.

Anybody quickly direct me to how to remap <Alt>?

thanks,

I don't know off the top of my head, but one thing that could be wrong is if you're running Emacs in a shell window instead of in a window of its own.

---

### Post by gordonsowner on 2007-02-21
Nope... it's in it's own window, launched from the 'Applications' desktop menu.

---

### Post by Arndt on 2007-02-21
> **gordonsowner said:**
> Nope... it's in it's own window, launched from the 'Applications' desktop menu.

What does the command

```
xmodmap
```

show? For me, it shows

```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)
```

I don't know exactly what Emacs looks for, but here both Alt and Meta are on the modifier mod1.

To see what character codes are sent by various keys, and to what key symbol they are mapped, you can use the program

```
xev
```

---

### Post by gordonsowner on 2007-02-22
Hi Arndt,

Sorry for the delay... away from my computer yesterday...

My xmodmap output for mod1 is identical to yours... and I'm not sure how to interpret the xev output.

Any other ideas?

Thanks,
Matt

---

### Post by gordonsowner on 2007-02-22
One note...

I've found that my left ALT key works as meta, but not my right.  Looking at the output of xmodmap, I see that Alt_L is defined twice... I'm assuming that refers to the left ALT key... if my right key were bound, shouldn't I see Alt_R also bound in mod1?  I'm making some assumptive leaps about things I don't know, but it seems like a thought...

Matt

---

### Post by gordonsowner on 2007-02-22
One more note...

Using

xev

I see that when I press the left ALT key, it tells me I've pressed 'Alt_L'... When I press the right ALT key, it tells me I've pressed 'ISO_Level3_Shift'.

I'm so confused.

Matt

---

### Post by gordonsowner on 2007-02-22
Problem fixed!

I used desktop menu 'System > Preferences > Keyboard' to fix.

I went to 'Layout options' tab, expanded 'Alt/Win key behavior', and selected 'Alt and Meta are on the Alt keys (default)'.  Seemed to fix problem.

I'm very, very excited, even if it took a conversation thread with mostly myself to work out -- but huge thanks to Arndt for pointing out 'xev' and 'xmodmap', without which I couldn't even begin to diagnose the problem.

Thanks!

Matt

---

### Post by Arndt on 2007-02-23
> **gordonsowner said:**
> Problem fixed!

I used desktop menu 'System > Preferences > Keyboard' to fix.

I went to 'Layout options' tab, expanded 'Alt/Win key behavior', and selected 'Alt and Meta are on the Alt keys (default)'.  Seemed to fix problem.

I'm very, very excited, even if it took a conversation thread with mostly myself to work out -- but huge thanks to Arndt for pointing out 'xev' and 'xmodmap', without which I couldn't even begin to diagnose the problem.

Matt

I was prevented from looking more at your problem, but I think you went to the right solution just as fast as I could have got there. I'd probably have you try strange things in Emacs before thinking of the system settings.

Good that it worked out.

---

### Post by gordonsowner on 2007-02-24
You were a great help, Arndt... Most of my self-replies were posted within minutes of each other, and I wouldn't expect instant responses from anyone, especially when it's free... Again, thanks... I learned a bit more about the system through these two commands.

---

### Post by apolyak on 2007-03-03
I use Esc key as the Meta, this works with default keyboard mapping. Check section 'Keyboard customization' in Emacs manual if you need.

Thanks for xev and xmodmap.

---

### Post by agoodno on 2007-04-01
Thanks to both of you - this worked for me as well.

Andy

---

### Post by jmags on 2007-10-26
Hey, my alt key works when I have Emacs running in its own window, but when I try to run it in a terminal (emacs -nw), it doesn't. alt-v produces an o with umlauts over it. Has anyone run into anything like this?

---


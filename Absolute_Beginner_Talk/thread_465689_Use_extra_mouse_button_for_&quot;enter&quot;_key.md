---
title: "Use extra mouse button for &quot;enter&quot; key?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by KnowNothing on 2007-06-06
I have a MS Trackball Explorer mouse and I followed the instructions to get the extra buttons working properly.  It worked, but in Windows I used the button on the far right for "enter" instead of "forward."  I really like that set up because I almost never use "forward" and I use "enter" all the time.

I cannot find a way to do this in Ubuntu.  Is there a way?  I hope so.

Thanks very much.

---

### Post by phr0ze on 2007-06-06
I'm not familiar with those settings, but how does it let you pick button assignments? Like if you wanted the forward button to be the letter 'H'. If you can type in codes, someone may be able to privide the code for enter. Sometimes represented as Ctrl-M, 13, or ^M.

---

### Post by freakavoid on 2007-06-06
A combination of xbindkeys and xvkbd should work. Something like:

```

"/usr/bin/xvkbd -text '\[Return]'"
  b:x

```

in your .xbindkeysrc file. Where x is the number of the mouse button you want to assign the return key event.

---


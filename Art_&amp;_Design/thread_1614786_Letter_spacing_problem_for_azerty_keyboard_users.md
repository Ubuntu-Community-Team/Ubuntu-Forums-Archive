---
title: "Letter spacing problem for azerty keyboard users"
date: 2010-11-06
forum: Art &amp; Design
---

### Post by Dopameen on 2010-11-06
Recently I wanted to do some horizontal character spacing with Inkscape but it appeared impossible.

There is no menu entry to do that (you can only do line spacing). There  are only short-cuts a user need to be aware off but the ones described  in the manual don't work (CTRL+< and CTRL+>). The reason why they  didn't work is because Inkscape is only supposed to be used by querty  keyboards while I'm an azerty keyboard user.

After wading through the source code (src/text-context.cpp) I saw that  other key's can also be used. So azerty users can use ALT+SHIFT+; or  ALT+SHIFT+< and ALT+, or ALT+< which partially solved the  character spacing problem because you can kern it 10 units to the right  or 1 unit to the left.

---


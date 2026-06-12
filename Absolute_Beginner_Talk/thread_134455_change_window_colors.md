---
title: "change window colors?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by telepathetic on 2006-02-21
Specifically, I really want to change the background color in the bluefish editor window.  How do I do this?
I do not believe it's possible with the Bluefish program itself-- I've tried playing with the syntax highlighting and it seems impossible to change the background color to the right of newlines this way.
Is there a way to specify the background through some configuration files?  Is there a general solution to this problem that I could apply to other things as well?

thanks for help!!
-telepathetic

---

### Post by telepathetic on 2006-02-22
in case anyone else cares, i figured this out-- had to change the .gtkrc-2.0-- mine is this now, and now i'm happier:

style "bluefish"
{
 base[NORMAL]="#1E2B3B"
 text[NORMAL]="#75ABAD"
}
class "GtkWidget" style "bluefish"

---


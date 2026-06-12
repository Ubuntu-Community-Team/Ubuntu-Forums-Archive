---
title: "Redefining Function Keys"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Snodgrass on 2006-12-18
How could I make the 'F1' key print "foo" on the command line?

That question distills my confusion pretty well, I think, and an answer to it would help me a lot.

Thank you,

Snodgrass

---

### Post by raul_ on 2006-12-18
[http://wizah.blogspot.com/2006/11/debian-how-to-task-manager-xp-style_02.html]("http://wizah.blogspot.com/2006/11/debian-how-to-task-manager-xp-style_02.html")

Try understanding how that works :)

---

### Post by Snodgrass on 2006-12-19
Thanks, Raul_!

Here's a link that might be more "beginnerly"  (tm).

[http://linuxgazette.net/issue55/henderson.html](http://linuxgazette.net/issue55/henderson.html)

This takes me almost to my goal. One problem is that the author assumes that "F1" sends the characters Escape, [,[,A . That is, "\e[[A".  But Gnome in Edgy sends characters that call up Firefox Help. 

How do you find out what those characters are? He says Readline's quote-insert is bound to Control-V.  But when I type Control-V followed by pressing F1, I get Firefox Help, not the characters I'm looking for.  Should I be using something other than Control-V to invoke quote-insert? 

Thanks,

Snodgrass

---


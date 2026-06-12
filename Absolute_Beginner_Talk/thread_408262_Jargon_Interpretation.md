---
title: "Jargon Interpretation"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by xinoos on 2007-04-13
Hi Gurus,
 
Can anyone explain what the following path means? Are there any syntax error too?

/usr/bin:/usr/ucb:/etc:.TH=/usr/bin:/usr/ucb:/etc:/usr/local/bin:/usr/local/sbin

Thank you.

---

### Post by moshuptrail on 2007-04-13
It looks like the $PATH variable contents
the colons : are delimiters
between the delimiters are the directories that will be searched for commands you may type
the one that is ".TH=/usr/bin" looks odd to me - probably a syntax error
the others look okay but there is some redundancy

here's what mine looks like:
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by xinoos on 2007-04-13
Cool. Thanks for the tip. will do more research.

Cheers.

---

### Post by Arndt on 2007-04-13
> **xinoos said:**
> Hi Gurus,
 
Can anyone explain what the following path means? Are there any syntax error too?

/usr/bin:/usr/ucb:/etc:.TH=/usr/bin:/usr/ucb:/etc:/usr/local/bin:/usr/local/sbin

Thank you.

.TH could be something from a man page, written in nroff. But it doesn't look likely in that line anyway - such directives come at the start of lines.

---

### Post by xinoos on 2007-04-17
yeah i think it shld be a syntax error

---


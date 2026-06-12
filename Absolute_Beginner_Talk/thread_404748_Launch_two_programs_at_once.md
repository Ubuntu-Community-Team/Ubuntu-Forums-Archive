---
title: "Launch two programs at once"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by qpwoeiruty on 2007-04-08
How can I run two applications at the same time?

I've tried:
xmms | sleep 3 && bzflag
xmms | bzflag

With the first, bzflag doesn't start until after xmms exits and with the second bzflag doesn't go fullscreen since the xmms window shows up.

Is there a way to either turn the xmms window off at launch or to run both simultaneously?

---

### Post by trent dillman on 2007-04-08
...

---

### Post by qpwoeiruty on 2007-04-08
That gives me:

> bash: syntax error near unexpected token `;'

but

```
xmms & sleep 3 ; bzflag
``` works! Thanks!

---

### Post by Spyros_Gre on 2008-01-29
Hello! It's been some time from the last post but I want to ask something about two apps running simultaneously. I managed to launch mozilla thunderbird and freepopsd (a program that lets you download yashoo, hotmail etc messages through POP). They both run fine but when I close thunderbird the other program doesn't close. I can see it in system monitor with sleeping status. my launcher command is
[code]
thunderbird %u & sleep 3 ;freepopsd[\code]

I will try kill instead of sleep as a first step. If anyone knows smth please tell me!
Thank you!!!

---

### Post by philinux on 2008-01-29
I use Tb with the webmail and hotmail extensions. If this is what you need see this.

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

It does yahoo and gmail.

---

### Post by emarkd on 2008-01-29
When you launch two programs like that, they're separate from each other.  Closing one has no effect on the other.  If you really wanted to tie them together, you could put in a test loop that checks every few seconds to see if Thunderbird is still running and kills freepopsd if it isn't.

---


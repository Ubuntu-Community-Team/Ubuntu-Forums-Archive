---
title: "Set priority with command line"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-09-26
I know that the "nice" command is supposed to do this somehow, but the "man" pages don't make **any** sense!  What would be the command if I wanted to simply set the priority of <processA> to <priority>?

---

### Post by bodhi.zazen on 2007-09-26
Say you want to run a command, foo, with a nice value of 5 ...

nice foo 5

Say you want to change the value of a process that is already running,

use renice

renice 5 foo

If you want a negative nice value, use sudo

sudo nice foo -15
sudo renice -15 foo

---

### Post by ryanVickers on 2007-09-26
Thanks!  It was also because it was an odd sort of command that needed parameters to work, and I guess they have to be included :)

Now that I think about it, starting with it rather than changing would be better ;)

---

### Post by ryanVickers on 2007-09-26
Ok, actually, I'm not done here :)

Let's say I'm running a command that has a bunch of parameters, and when I put the "nice value" on the end, it gets put into the other command, and not recognized as still part of the other command.

ex: nice <program> <parameters of program> <nice value>
but it get's read like this...

ex: nice <program> <parameters of program (including nice value)>

:confused:

---

### Post by bodhi.zazen on 2007-09-26
nice -n 5 foo -options

---

### Post by ryanVickers on 2007-09-26
Doesn't seem to work.  To make things easier, here's the command/section of script that I'm trying to fix:
```

nice rar a -v$size"M" $name.rar $folder $pri

```
when it goes to make the rar, it looks for the path <$folder $pri>, instead of looking for <$folder> and running with the nice of <$pri> :(

Is there some way I can "re-word" this to make it realize they are 2 separate things!?!

---

### Post by bodhi.zazen on 2007-09-26
Try :

nice -n 5 rar a -v$size"M" $name.rar $folder $pri

change 5 to the nice value you want.

---

### Post by ryanVickers on 2007-09-26
YES!!! Thank you so much for sticking through that! :)

It actually looks something like nice -n $pri rar a -v$size"M" $name.rar $folder because the value is to be dynamically set by the user, but thanks again anyways! :p

If your interested in what this command is all about, check out my "rar maker" tread (signature)!

---

### Post by HermanAB on 2007-09-26
However, no matter what you set the priority of a process to, it likely won't make any difference!

Your system has to be horribly overloaded before changing priorities of processes will have a noticeable effect, because the Linux scheduler is really very good.

Cheers,

Herman

---

### Post by ryanVickers on 2007-09-26
I beg to differ!  I have a very high-end system, and although your right, it is WAY better than windows :), If I pin my processor to 100%, it's busy running those/that task(s), and will respond, but at a reduced pace.  However, if I set the priorities of those teak(s) to very low, they will consume all of my processing power, yes, but whenever something needs it, no matter how quick or small of a request, it will respond nearly like there is no load on it at all! :)

---


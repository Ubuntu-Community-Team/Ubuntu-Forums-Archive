---
title: "log of 'make'"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by maybeme on 2006-11-16
Hi,

I know this is a really noobish question, but I can't find the answer, because you can't find good search terms.

When you execute 'make', in my case for lirc, where can you find a log of the process?

Or is there a command to write all the console output to a file?

Thanks a lot

---

### Post by Ecthelion on 2006-11-16
To print an output to a file you can do
```
*_command_* **>** *_file you want to write to_*
```

But that should only put in a file what you normally see under your command...

---

### Post by maybeme on 2006-11-16
That's enough, I just wanted to have the information the console showed but got removed because of the other information taking it's place.

(I use freebox or just don't use x, so you can only see like about 15 lines)

Sorry for my English

Thanks!

---

### Post by bodhi.zazen on 2006-11-16
> **maybeme said:**
> Hi,

I know this is a really noobish question, but I can't find the answer, because you can't find good search terms.

When you execute 'make', in my case for lirc, where can you find a log of the process?

Or is there a command to write all the console output to a file?

Thanks a lot

Try script:

Script- Records a terminal session.
To start - type "script" at the CLI

Then type your make command (will execute make and record output)

to end- type "exit"

the session is	saved a text file "typescritp" in ~

To view: 
	cat ~/typescript

		OR

less ~/typescript

OR

"script replay" (replays at human speed)
[indent](this does not always work)[/indent]

---

### Post by po0f on 2006-11-16
maybeme,

You could also use [tee](http://www.die.net/doc/linux/man/man1/tee.1.html), to see it as it's printed to stdout, and write output to a file.  You should also be able to scroll back at least a couple of lines in a tty; just hit Shift+PgUp.

---

### Post by maybeme on 2006-11-17
I used Echtellion's solution, but now I know the Shift+Page Up trick, I'll use this one from now on!

Something so simple, but you have to know it.

Thanks for the replies!

---


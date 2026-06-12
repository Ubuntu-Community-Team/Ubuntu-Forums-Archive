---
title: "error message redirection problem"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by wog on 2006-06-18
When I see a bunch of error message gobbledygook I try to redirect it to a file so I can show it to someone else like this:

error command >> output.txt

Sometimes the error message prints out on the screen and the output.txt file is ignored. What can I do to capture the error output?

---

### Post by mlind on 2006-06-18
command > yourlog.log **2>&1**
This will redirect stderr to stdout.

If you just need output that goes on stderr, then
command 2> yourlog.log

---

### Post by wog on 2006-06-18
I'm sorry, I don't know what stderr means, I'm not a programmer. I'm just your standard id10t newbie.

Let's see...if stdout is short for standard output, meaning the screen, and stderr is the error message I see going to the screen instead of the file, then I understand enough to play with it. 

If not, you'll have to tell me. Sorry.

But thank you for the clues... :)

---

### Post by mlind on 2006-06-18
[QUOTE=wog]I'm sorry, I don't know what stderr means, I'm not a programmer. I'm just your standard id10t newbie.

Let's see...if stdout is short for standard output, meaning the screen, and stderr is the error message I see going to the screen instead of the file, then I understand enough to play with it. 

If not, you'll have to tell me. Sorry.

But thank you for the clues... :)[/QUOTE]

I think you got it. Standard output and standard error are for application to print
out it's messages. It's easier for programmer and end-user to find necessary stuff
when errors are on "different channel" than normal output messages.

---


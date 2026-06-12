---
title: "Zenity --Progress option"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-03-29
Hi,
I have looked at "MAN zenity" and everywhere else including here honest..
I have also looked at some of the multimedia scripts that add into the nautilus shell for sample help.

BUT
How do I "attach" a zenity --progress dialogue to a command ?

Tried this:-

command1
zenity --Progress bla bla

and this:
zenity --progress bla bla
Command1

and it sure looks like the samples I see use the former.
But all I get is command1 running then a dialogue opens on zero percent progress..
I'm stuck

---

### Post by jethro10 on 2006-03-30
Well I got no reply so I've searched again and found this.

I'll post it incase it helps someone else.

Its the Pipe command | 

Command1 | zenity --progress bla bla

seens to make sense, output of command into input of progress bar.

Can't try this for about another 9 hours but it looks good.

J

---

### Post by Mustard on 2006-03-30
I'm not sure how you would do it either, but I think Automatix uses zenity quite a bit.  I wonder whether you could look through the Automatix code and get some tips from that. :)

---

### Post by jethro10 on 2006-03-30
I think I might have it with the comment above.
I looked thru tons of code and missed the | sign every time.

Kept thinking to myself "what the hell has somebody put | in the code for!"

crazy world.

---


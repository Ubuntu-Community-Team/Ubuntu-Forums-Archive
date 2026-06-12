---
title: "Terminal won't let me enter passwords [Resolved]"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Ziao on 2007-01-07
Hi everyone,
I'm new to linux, and so far i really love it!
However i have a problem;
In the terminal, everything works fine, except when it asks me for my password (like when i type 'su'), it just won't let me enter anything. i can type whatever i want but nothing happens. when i press return, it tells me my password was wrong (ofcourse). 

I'm sure this is a basic thing, but i've been looking for a solution for an hour now and it's driving me nuts.

Any help would be greatly appreciated.
Regards, Nick

---

### Post by ajmorris on 2007-01-07
it is entering a password it just conceals it with know characters being shown. Try typing the password and pressing enter it should work.

---

### Post by riven0 on 2007-01-07
Just wanted to make sure: you are using *sudo* instead of *su*, right. Like when you install something:

> sudo apt-get install whatever

Because it sounded like you were using *su* :)

---

### Post by Ziao on 2007-01-07
that's the problem. NOTHING gets shown, not even stars or anything. just like you're not typing

edit: 'sudo' did work ! sorry, i'm new to this
thanks alot for the help :)  i really appreciate the fast reply's and the helpfull members

---

### Post by MkfIbK7a on 2007-01-07
yes thats normal when you type a password in the terminal it shows nothing but if you do it correctly and press enter it will work

---

### Post by aysiu on 2007-01-07
As others have stated, there's **no** visual feedback when you enter your password in the terminal. It's very confusing, but as you will see from [this thread](http://www.ubuntuforums.org/showthread.php?t=214393&highlight=terminal+feedback), it's also something that's not going to change any time soon.

---

### Post by Ziao on 2007-01-07
aaah ok, thanks again for the info :)  and i'm sorry for asking stupid questions

---

### Post by MkfIbK7a on 2007-01-07
very good thread you started there aysiu and it probably would be a good idea to put asterikses (or however you spell it) there but its such a small problem i dont think anyone cares too much...

---

### Post by aysiu on 2007-01-07
> **Ziao said:**
> aaah ok, thanks again for the info :)  and i'm sorry for asking stupid questions
It's not stupid at all. In fact, if you look at that thread, I strongly advocated putting feedback in precisely to prevent this misunderstanding. Clearly, I'm fighting a losing battle there.

---


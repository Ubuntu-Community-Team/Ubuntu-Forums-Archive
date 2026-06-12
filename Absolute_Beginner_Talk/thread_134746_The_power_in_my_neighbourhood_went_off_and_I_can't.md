---
title: "The power in my neighbourhood went off and I can't log in"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by ovidiu82 on 2006-02-22
I logged in the terminal, and opened mozilla from the terminal, in the fail-safe option...

I holla for some help, any idea on how can I repair it and enter ubuntu...

---

### Post by Brunellus on 2006-02-22
you're going to have to describe the problem a bit more completely than that, I'm afraid.  

1) can you see GDM (the graphical log in screen)?

2)  Do you have X? (the Xwindows system--the gui), or do you come to a text-mode login?

---

### Post by ovidiu82 on 2006-02-22
yes, it says something like permision to Ice file denied...or can't access the ICE file...

i am logging in the fail save terminal, and in the terminal I type mozilla and this is how I'm in touch with you..

---

### Post by ovidiu82 on 2006-02-22
It said ICE authority denied or something like this....and I said to myself..

who the F. is the Ice autorithy...so it came inevitable..

sudo rm .ICEauthority

it works..

might this bring troubles to me?

---

### Post by steve.horsley on 2006-02-22
No troubles. That file is a pain in the backside. I don't know how it gets there, but its something to do with launching graphical stuff as root from your own home directory. Sometimes it gets left owned by root, and then that causes problems because you can't write to it any more.

---


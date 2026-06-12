---
title: "How do I start aterm with unicode?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-06-11
How do I start aterm with unicode?

Currently, my aterm does not display the ' very well.  I can type the key, but should I open a file that contains a ', it would display it in weird characters and an empty square beside it.

---

### Post by moore.bryan on 2007-06-11
*according to a number of sites and personal experience, aterm can't handle unicode... sorry; i'm sure that's not the answer for which you were looking.*

---

### Post by oldcpu on 2007-06-11
Why does the ' appear as an unknown character in Ubuntu when I use aterm?  I have used aterm in other distributions and it does not have this problem.

I open xterm and eterm and the same thing happens.  Unless I use unicode xterm.

I thought it was an unicode problem.

---

### Post by moore.bryan on 2007-06-11
*you got me... they websites i checked said aterm is "incompatible" with unicode.*

---

### Post by Phrostie on 2007-07-16
this isn't a Ubuntu or Debian problem.  for some reason Aterm, no longer seems to know it's language.

in your .bashrc, add a line that reads: 

export LANG=C

save and then restart your aterm.

see if that helps.

---

### Post by oldcpu on 2007-07-17
Thank you very much, Phrostie!

Now I can read the manuals without all those weird characters.

---


---
title: "Launching a Terminal with a profile selected"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by aidanlister on 2007-06-25
How can I launch a Terminal instance and set the profile used?

I saw a --with-window-profile but this option appears to do nothing.

Is there an environment variable which holds the profile selected?

---

### Post by felicity on 2007-06-25
How were you using the option --window-with-profile when it appeared to do nothing?

If you have a profile with the name Profile2, then you use the option like this: --window-with-profile=Profile2

Like this: gnome-terminal --window-with-profile=Profile2

---

### Post by Golyadkin on 2007-06-25
I can confirm felicity's solution works, I was looking for something like that myself.


(Btw, good quote from Fyodor, he is my favourite author)

---

### Post by aidanlister on 2007-06-25
Excellent, I worked it out.

I was using "launch application in terminal", and trying to pass it that way, I see now why that won't work.

The trick is to use "launch application" with gnome-terminal --window-with-profile=IRSSI -e start-irssi

Thanks :)

---


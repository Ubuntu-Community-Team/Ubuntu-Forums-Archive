---
title: "compiz fusion/ emerald problems"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Funky91 on 2008-01-27
hi, i installed ubuntu this morning and have installed compiz fusion and emerald. when i put emerald --replace in terminal it set emerald as the window decorator however when i exited the terminal all window decorations vanished. now i have to have a terminal open with emerald --replace in or I have no window decorations at all.

please help!

---

### Post by torgrot on 2008-01-27
You could type this instead emerald --replace &

That will run it detached,  it won't run it at startup though.

torgrot

---

### Post by Funky91 on 2008-01-27
i gave that a go but it still lost window decorations when i exited terminal.

---

### Post by emarkd on 2008-01-27
Just run it from the <alt> F2 dialog.

---

### Post by Funky91 on 2008-01-27
excellent. how would i enable that at startup then?

---

### Post by ~LoKe on 2008-01-27
> **Funky91 said:**
> excellent. how would i enable that at startup then?

System -> Preferences -> Sessions

Add "emerald --replace" without the quotation marks to the startup list.

---

### Post by emarkd on 2008-01-27
Click on Preferences > Sessions.  Select Add.. and add a new entry.  The name and comment are unimportant; it's just for your reference.  Just put the command you want to run in the command box exactly like you did in the <alt>F2 box

---


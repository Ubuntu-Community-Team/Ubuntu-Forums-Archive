---
title: "Running application from menu"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2006-10-31
Hi,

I downloaded and installed a program which launches itself via a script.

I can launch the program easily enough from a terminal by cd-ing to the script's directory and typing:

```
./idea.sh
```

This works fine.

However, I would rather have a menu entry for the application for ease of use.

First of all I used the menu editor and added a new item.  In the *command* field I just browsed to the script's folder and selected it, which resulted in the following:

```
/home/simon/idea\-\5\7\8\4/bin/idea\.sh
```

But when I try and run the program, nothing happens.

Next I tried:

```
cd /home/simon/idea-5784/bin/; ./idea.sh
```

...and ticked the *Run command in terminal* checkbox.  Now when I tried to run it, a terminal flashes on the screen for a brief moment, then closes and... nothing.

Can anyone help me on this?

Regards.

---

### Post by Ben Sprinkle on 2006-10-31
Right click the panel, new entry. Do your icon etc, then type the command to execute. :)
You will see what I mean when you try it.

---

### Post by NegativeSpace on 2006-10-31
Hi synectics,

Thanks for your input, but if I just add idea.sh, I get the terminal appearing then disappearing again.

I added the folder which the script is located in to the PATH variable, and still nothing.

---

### Post by Ben Sprinkle on 2006-10-31
Not sure what your trying to do. If your script requires the Terminal then check the thing that says run in Terminal.

---


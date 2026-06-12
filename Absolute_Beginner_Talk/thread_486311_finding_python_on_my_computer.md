---
title: "finding python on my computer?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ktown on 2007-06-27
hey i run kubuntu and i went to synaptic manager and downloaded the latest version of python and i am having trouble finding it. any ideas, i'm sure this is a really easy question.

---

### Post by Malibu Illusion on 2007-06-27
Type this into a terminal:

```
python
```

That'll open an interpreter.  You can run individual Python scripts through this by using:

```
python filename.py
```

If you're looking for a graphical IDE, install IDLE:

```
sudo apt-get install idle
```

That'll then be available under your applications menu.

Take care.

---

### Post by Qrk on 2007-06-27
Python is a language, so you can do several things. You could open up an interpreted session in a terminal (using the python command) but that probably won't be very easy to learn it with.

I'd recommend installing IDLE, which is a great way to learn how to use interpreted python.

---

### Post by ktown on 2007-06-27
well i mean im sure its installed on my computer i just can't find it. ive looked through my applications menu any suggestions

---

### Post by LancerDragoon on 2007-06-27
Try looking under Applications -> Programming. Can you try this code and see if it returns a path?

```
which python
```

---

### Post by Malibu Illusion on 2007-06-27
Re-read the above posts, please.

Python is a programming language; you've installed support for that as well as the class libraries.  The only time you'll "see" it is if you try to invoke it via the terminal with the command I stated in my initial post.

If you're looking for an environment to program in Python, go ahead and install IDLE as suggested.

---

### Post by kitty500cat on 2007-06-27
Have you tried running it from the terminal like they said?

If so, and it didn't work, try this in the terminal:

```
sudo apt-get install python
```

Regards :)

---


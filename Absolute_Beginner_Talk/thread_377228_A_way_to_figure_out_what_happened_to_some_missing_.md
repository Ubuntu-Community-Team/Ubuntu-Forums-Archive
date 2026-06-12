---
title: "A way to figure out what happened to some missing files?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2007-03-05
Well Im not sure if someone else in the house was messing with my machine when I wasnt around or what.

But the entire contents of a folder have up and disappeared.

The trash is empty.

Is there a way to find out what happened?

---

### Post by ewankho on 2007-03-06
May not be as helpful but you try looking at the 'history' command.

---

### Post by poekie on 2007-04-20
> **CloudyHaze said:**
> Well Im not sure if someone else in the house was messing with my machine when I wasnt around or what.

But the entire contents of a folder have up and disappeared.

The trash is empty.

Is there a way to find out what happened?

The same thing happened to me. I upgraded to feisty today, I don't know if that has anything to do with it. But the entire 21.57GB of data in the directory has disappeared. Not a trace (only with recovery tools, but those files were mashed up and unusable.

> **ewankho said:**
> May not be as helpful but you try looking at the 'history' command.

This only showed me that I actually didn't do *anything* which is a bit odd... 
I have to ok everything that I 'throw away' or delete, so what happened to the files? CloudyHaze, did you ever recover them and how?

---

### Post by ricardisimo on 2007-04-20
Try ```
locate <filename-or-part-thereof>
```in a terminal.

---

### Post by ricardisimo on 2007-04-20
P.S. - There's also a .trash folder in /root, I believe, that may or may not respond to file searches. Navigate to /root in Nautilus and hit <CTRL> H to display hidden files and folders. You should see .trash there.

---


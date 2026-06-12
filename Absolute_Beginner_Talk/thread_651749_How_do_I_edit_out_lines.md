---
title: "How do I edit out lines?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by newnet on 2007-12-27
I am looking for a command that can be used in a pipe that would edit out a line.  Say I want to edit out line 2, 3, and 5 of the printed text.  What command can be used?  Let me know if there is more than 1 way.  I might find the other way easier to remember.

---

### Post by hardyn on 2007-12-27
what command are you piping?

|more? |less? something else?

---

### Post by newnet on 2007-12-27
What are you talking about?  Did you even read my post?

> Say I want to edit out line 2, 3, and 5 **of the printed text.**

I make a command that would print some text.  Add a pipe.  Enter the command that would be able to edit out certain lines.

---

### Post by Gen2ly on 2007-12-27
sed is the command you're looking for.   seds perfect for changing text in files. If you have to do it with numerous files, you'll have to pipe "sed" through "find".

I recently changed my username and changed all the files in my home folder that contained my old username to my new username.  This is what I researched to do that - where foo is the original username and bar is the replacement.  The g variable says to change all instances of the username in the file.  Not exactly what you're looking for but I hope its a start.

```
find . -type f | xargs sed -i '' -e 's/foo/bar/g'
```

---

### Post by bodhi.zazen on 2007-12-28
I second sed, sed is the tool you want :)

delete lines 1-10 :

```
sed -i -e '1,10d' file
```

Delete only line 2 :

```
sed -i -e '2,2d' file
```

where file is the file you want to modify. NOTE : This will obviously over write the file. If you want to preserve the original file :

```
sed '1,10d' file > new_file
```And on ...

So for multiple lines (2,3, and 5):

```
sed '2,2d; 3,3d; 5,5d'
```

You can use that in a pipe :)

---


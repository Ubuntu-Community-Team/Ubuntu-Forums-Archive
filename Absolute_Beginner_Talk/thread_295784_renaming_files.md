---
title: "renaming files"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-11-08
I am having trouble renaming files. I use breezy and whenever I use the "rename" command it fails. I get this:
```
Bareword found where operator expected at (eval 1) line 1, near "/home/mike"
        (Missing operator before ke?)
Search pattern not terminated at (eval 1) line 1.

```

Any help is greatly appreciated

---

### Post by Blutack on 2006-11-08
Not exactly a solution but the 'traditional' way to rename a file is to use mv (move).  So for example

mv /home/us/republican /home/us/democrat

would rename the file republican to democrat.
Hope this helps...

---

### Post by bsussman on 2006-11-08
the manpage for rename has examples.  Type:

```
bos@Dillon:~$ man rename
```

to read more

---

### Post by funrider on 2006-11-08
for non-terminal user, simply do it in X: right click --> Rename

remember ubuntu is built for human (regular human), there is nothing wrong to do it in the GUI way.

---

### Post by Blutack on 2006-11-08
There's no such thing as a regular human, we are all special in our own way...

---

### Post by migla on 2006-11-08
> **Blutack said:**
> There's no such thing as a regular human, we are all special in our own way...

I'm not.

---

### Post by funrider on 2006-11-08
> **Blutack said:**
> There's no such thing as a regular human, we are all special in our own way...

ok, i agree with u that we are all special in our own way...one thing to point out that we are using the same OS which is made for human beings. :-D 

[IMG]http://www.ubuntu.com/htdocs/uweb/menu/top-title.png[/IMG]

---

### Post by Blutack on 2006-11-08
Just for human beings?  I think you could teach a monkey to use ubuntu.  That would be a hell of an interesting project if anyone has an old spare comp they don't mind getting broken.  And a monkey, obviously.

---

### Post by Blutack on 2006-11-08
Migla, if you can teach the monkey then you would be very special indeed.

---

### Post by TheFourElements on 2006-11-08
> **funrider said:**
> there is nothing wrong to do it in the GUI way.

Except I use window maker

---

### Post by po0f on 2006-11-08
Please, keep the off-topicness to a minimum.

TheFourElements,

You can try renaming the files in the terminal with `mv`, but double-quote (") the filename:
```
$ mv "Some weird filename? Huh?!?" some_weird_filename_huh
```

---

### Post by Arndt on 2006-11-09
> **po0f said:**
> Please, keep the off-topicness to a minimum.

TheFourElements,

You can try renaming the files in the terminal with `mv`, but double-quote (") the filename:
```
$ mv "Some weird filename? Huh?!?" some_weird_filename_huh
```

Single quotes are better, otherwise the shell wants to interpret the ? and ! characters:

```
$ touch 'Some weird filename? Huh?!?'
$ ls *weird*
Some weird filename? Huh?!?  weird?!
$ mv "Some weird filename? Huh?!?" some_weird_filename_huh
bash: !?": event not found
$ mv 'Some weird filename? Huh?!?' some_weird_filename_huh
$
```

---


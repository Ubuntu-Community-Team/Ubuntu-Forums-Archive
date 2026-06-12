---
title: "Copying files and dirs"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by rickmans on 2006-06-17
I would like to copy directories and files that are modified or created after a certain date and that match a certain pattern (well they should not have a '~' in their name). I would also like that the parent directories of the files modified or created are copied.

I wouldn't have the foggiest idea how I should to this, probably with cp and grep, but how the command should look like... :?:

---

### Post by IYY on 2006-06-17
[QUOTE=rickmans]I would like to copy directories and files that are modified or created after a certain date and that match a certain pattern (well they should not have a '~' in their name). I would also like that the parent directories of the files modified or created are copied.

I wouldn't have the foggiest idea how I should to this, probably with cp and grep, but how the command should look like... :?:[/QUOTE]

To copy all files and directories that do not start with ~ into the directory 'destination', use the following:

```
cp -r [^~]* destination
```

I'm not quite sure what you mean by,

```
I would also like that the parent directories of the files modified or created are copied.
```

So please explain, and I'll try to figure out a way to do it.

---

### Post by rickmans on 2006-06-17
What I meant was the following:

e.g. I got the following directory structure

```

maindir
-subdir
--file in subdir
-subdir2
--file in subdir2
--another file in subdir2
--another file in subdir2~

```

Now only "another file in subdir2" has changed and "another file in subdir2~" was an automated copy of "another file in subdir2" which was also changed on the same day.

Now I would like to copy al files that were changed the last day and does not end with an "~" (only file "another file in subdir2" should therefore be copied). The result of the copy should be this:

```

maindir
-subdir2
--another file in subdir2

```

---

### Post by uzi09 on 2006-06-17
why not delete all the files with a "~" in it instead?

---

### Post by rickmans on 2006-06-17
That is also a good option imho.

Would that be something like rm *[~] (I could not imagine anyone worse than me in regular expressions).

---

### Post by IYY on 2006-06-17
Just 

```
rm *\~
```

(the slash is because ~ is a special character)

---


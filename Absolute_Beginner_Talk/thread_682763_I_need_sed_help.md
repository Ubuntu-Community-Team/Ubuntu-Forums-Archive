---
title: "I need sed help"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by newnet on 2008-01-30
```
ls -1 | sed <insert missing code>
```
What I am trying to do is have sed print the file names twice.  So it would look something like this:
```

first.foo first.foo
second.foo second.foo
third.foo third.foo

```

---

### Post by mikeyphi on 2008-01-30
You might get some answers in the Programming talk Forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by newnet on 2008-01-30
Would a moderator please move this to Programming Talk if it is more appropriate.  (I was not aware that sed was a programming language.)  Thanks.

---

### Post by mister_pink on 2008-01-30
You might be better off using awk:
```

ls -1 | awk '{print $1 " " $1}'
```

Out of curiosity, why?!

---

### Post by spiderbatdad on 2008-01-30
I'm having fun with this problem. Of course it's simple to print every line twice, but in the same pattern space is proving to be challenge for me. Please keep posting when you find the solution.

---

### Post by emarkd on 2008-01-30
Do you mean the spacing between each filename?  You can try removing the " " and replacing it with a tabspace.  Like this:

```
ls -l | awk '{print $1 "\t" $1}'
```

---

### Post by spiderbatdad on 2008-01-30
I thought the idea was to use sed to print each pattern twice on the same line

---

### Post by newnet on 2008-02-01
> Out of curiosity, why?!
I need to convert a lot of files.  The conversion requires each file name to be used twice.  So I was thinking of writing a small script.  But can not figure out how to use sed to print the file names twice.

Thanks for the awk alternative, but I wish to do it with sed since I use it for many other things.  If it can not be done with sed, then I will use your suggestion.

---


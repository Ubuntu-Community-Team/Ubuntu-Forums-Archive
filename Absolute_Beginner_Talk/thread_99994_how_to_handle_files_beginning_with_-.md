---
title: "how to handle files beginning with -"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by series on 2005-12-06
lets say I have a file called "-a", how do I rename it to "b"?

```

$ mv -a b
mv: invalid flag -- a
Try "mv --help" for more information.

```

I have tried to escape it but havn't gotten it right.

---

### Post by doitashimashite on 2005-12-06
mv "-a" b

---

### Post by series on 2005-12-06
[QUOTE=doitashimashite]mv "-a" b[/QUOTE]

Sorry, still the exact same error-message.

---

### Post by doitashimashite on 2005-12-06
I'd suggest to use the rename option in nautilus.

---

### Post by series on 2005-12-06
[QUOTE=doitashimashite]I'd suggest to use the rename option in nautilus.[/QUOTE]

Yes, that's what I'm doing because there is currently no other way.
But this fight agains the terminal is not just for practical reasons, I really WANT to know the syntax.

---

### Post by doitashimashite on 2005-12-06
I understand. It's funny though, my first idea was to put "" around that filename. I remember (from a distant past) that this worked under SCO Unix 3.2.4.2, but apparently, not in this flavor of Unix...

I tried several other options, but so far, without success.

Anyone?

---

### Post by deNoobius on 2005-12-06
I'm a newbie myself, so don't jump all over me if I'm wrong, but isn't the problem that -a appears to be an option flag, but there's no such option for the "mv" command?

For example, "ls -a" would list all the files in a directory.  I would think if you removed the dash before the "a", it would work.  Although I would say that having single letter file names is confusing in an environment where single letters are usually part of a command.

---

### Post by doitashimashite on 2005-12-06
Sure, that's exactly the problem: the mv command sees this "-" sign as the beginning of an option, instead of the beginning of a filename. So you have to neutralize that, and in order to do that, there are usually some tricks, like putting the name in parentheses, or use a leading backslash, none of which is working here.
So far, I'm clueless.

---

### Post by series on 2005-12-06
[QUOTE=deNoobius]I'm a newbie myself, so don't jump all over me if I'm wrong, but isn't the problem that -a appears to be an option flag, but there's no such option for the "mv" command?

For example, "ls -a" would list all the files in a directory.  I would think if you removed the dash before the "a", it would work.  Although I would say that having single letter file names is confusing in an environment where single letters are usually part of a command.[/QUOTE]

Still, advice to ignore files prefixed with - is not what I want ;)

---

### Post by doitashimashite on 2005-12-06
Got it!

find . -name "-a" -exec mv {} b \;

---

### Post by natalia on 2005-12-06
[QUOTE=series]lets say I have a file called "-a", how do I rename it to "b"?[/QUOTE]

I had the same problem the other day with rm. Just try:

```
mv ./-a b
```

---

### Post by doitashimashite on 2005-12-06
Yes, that's a very elegant solution!

---

### Post by cwaldbieser on 2005-12-06
[QUOTE=series]lets say I have a file called "-a", how do I rename it to "b"?

```

$ mv -a b
mv: invalid flag -- a
Try "mv --help" for more information.

```

I have tried to escape it but havn't gotten it right.[/QUOTE]
That is what the "--" option is for:
```

$ rm -- -a

```
It means that anything following the -- option on the command line is *not* an option.

---


---
title: "echo: Can it do it alphanumerically?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-06-09
Is it possible to echo something alphanumerically?

Lets say I have something like

1234
asdf
qwer
zxcv

in the file

I echo something, echo looks for a space in between, create a new line and insert whatever I echo'ed.  Is this possible?

---

### Post by meng on 2006-06-09
I completely do not understand the question, could you rephrase it?

---

### Post by tux101 on 2006-06-10
Stuff already in file:

1234
asdf
qwer
zxcv

I echo this:

echo 'foo' >> file

The above would normally give me this in the file:

foo
1234
asdf
qwer
zxcv

How do I make it so it gives me this:

1234
asdf
foo
qwer
zxcv

Notice that it is listed alphanumerically (numbers + alphabets)?

How do I do the special echo without me telling it which line or between what words to echo into?  In otherwords, it searched for where it would go all by itself, then echo into it.

More clear now?

---

### Post by meng on 2006-06-10
Yes it is clear. This is the way I would do it, using the command "sort"

sort file > tempfile
mv tempfile > file

(I tried
sort file > file
but it didn't work)

man sort for more info.

---

### Post by tux101 on 2006-06-10
Thanks!

I thought my expectation of Linux has finally hit the wall when you replied with confusion.  But I was wrong.  It seems there is almost no limit to what Linux can do!

---

### Post by gr0kzer0 on 2006-06-10
Hey, if you think "sort" is cool, then check out "man grep" and "man sed".  When it comes to sorting, searching, printing character strings, Linux/Unix is the greatest.  And the cool thing about *nix is that all files are simple text files, so they can all be manipulated with these kinds of commands.

The GUIs (gnome, kde, xfce) are great, but once you get into using the console, you're into something else entirely!  Windows doesn't even come close!

---

### Post by dcraven on 2006-06-10
You could stick it into a little shell script like this:
```

#!/usr/bin/env bash

echo $1 >> file.txt
sort file.txt > temp
mv temp file.txt

```

Then run it like:
```

% myscript foo

```
Then the word "foo" would be added to the file and the file is sorted.

Cheers,
~djc

---

### Post by meng on 2006-06-10
[QUOTE=tux101]I thought my expectation of Linux has finally hit the wall when you replied with confusion.  But I was wrong.  It seems there is almost no limit to what Linux can do![/QUOTE]
Glad it helped. I think your original post was not worded very clearly, in that I couldn't understand what you were trying to achieve. The second post was much easier to understand.

---

### Post by tux101 on 2006-06-11
[QUOTE=dcraven]You could stick it into a little shell script like this:
```

#!/usr/bin/env bash

echo $1 >> file.txt
sort file.txt > temp
mv temp file.txt

```

Then run it like:
```

% myscript foo

```
Then the word "foo" would be added to the file and the file is sorted.

Cheers,
~djc[/QUOTE]
Good idea!

I changed it slightly since the above was only limited to a file called file.txt.
```

echo $1 >> $2
sort $2 > temp
mv temp $2
```


So now it runs with this command
```
script newword filename
```
Is there a way I can make it respond to this command instead?:
```
script newword > filename
```
I like to put the '>' as part of the script command so I do not forget the original command.  But I don't know how to make the '>' be treated as a cosmetic in the script.  Anyone got any idea?

---

### Post by IYY on 2006-06-11
I like to put the '>' as part of the script command so I do not forget the original command. But I don't know how to make the '>' be treated as a cosmetic in the script. Anyone got any idea?

It's not possible, since the > symbol gets interpertated by the shell before your command even gets executed. The best you could do is:

script newword \> filename

or (maybe)

'script newword > filename'

(obviously, you'll have to change your script to ignore the middle argument)

---


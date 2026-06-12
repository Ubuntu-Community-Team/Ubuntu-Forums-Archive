---
title: "How do I cat something specific?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-24
How do I cat something specific?

Lets say I have a text file that say:

blah, blah, blah, 
blah, blah, blah, blah, blah, blah, 
blah, blah, blah, blah, 
blah, blah, blah, blah

[foo1]
I
want
to
cat
this
part
[foo2]

blah, blah, blah, blah, blah, blah, blah, blah, 
blah, blah, blah, blah, blah, blah, 
blah, blah, blah, blah

So is it possible to do something like: cat '[foo1] to [foo2]' ~/file

Can it be done?  Or some alternative way.

---

### Post by halfvolle melk on 2006-05-24
Judging by this example, gawk can do that:
```
# Print all lines between start/stop pairs:
  awk '/start/, /stop/' file
```
Taken from [http://sparky.rice.edu/~hartigan/awk.html](http://sparky.rice.edu/~hartigan/awk.html)

edit: it works :)

---

### Post by Arndt on 2006-05-24
[QUOTE=tux101]How do I cat something specific?

Lets say I have a text file that say:

blah, blah, blah, 
blah, blah, blah, blah, blah, blah, 
blah, blah, blah, blah, 
blah, blah, blah, blah

[foo1]
I
want
to
cat
this
part
[foo2]

blah, blah, blah, blah, blah, blah, blah, blah, 
blah, blah, blah, blah, blah, blah, 
blah, blah, blah, blah

So is it possible to do something like: cat '[foo1] to [foo2]' ~/file

Can it be done?  Or some alternative way.[/QUOTE]

'sed' and 'awk' are two tools that can do this:

```
sed -n '/\[foo1]/,/\[foo2]/p' ~/file
awk '/\[foo1]/,/\[foo2]/' ~/file
```

Note that the backslashes \ are needed since the brackets [] have a special meaning otherwise (grouping character classes in regular expressions).

---

### Post by tux101 on 2006-05-24
Thanks you two.

What is the difference between sed and awk?  Which one is better for newbies like me?  Looks like down the road, I will have to side with one of them.

Also, how would I know if a character has a special meaning and needed to be backslashed?

---

### Post by Arndt on 2006-05-24
[QUOTE=tux101]
What is the difference between sed and awk?  Which one is better for newbies like me?  Looks like down the road, I will have to side with one of them.
[/QUOTE]

There is no need to side with one, I think. 'awk' is more of a small programming language, and particularly useful when data comes in well-defined columns. 'sed' is powerful but very cryptic when doing complicated things in it. For simple replacements and extractions, 'sed' commands are often shorter than the corresponding 'awk' command.

If you want to learn only one tool, and are willing to spend some time doing it, Perl may be the best choice.

[QUOTE=tux101]
What is the difference between sed and awk?  Which one is better for newbies like me?  Looks like down the road, I will have to side with one of them.

Also, how would I know if a character has a special meaning and needed to be backslashed?[/QUOTE]

The answer to that is probably to learn about regular expressions (regexps). They come in some different versions, but reading "man grep" may be a good start. 'grep' is a very good command to know, too.

---


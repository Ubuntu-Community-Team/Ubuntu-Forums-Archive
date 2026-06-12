---
title: "Looping out lines."
date: 2005-06-07
forum: Absolute Beginner Talk
---

### Post by Zyko on 2005-06-07
Hi!

I have searched all day for a way to find out how to loop out each line in a document.

for example:

lines.txt:
Line 1
Line 2
Line 3

and i want a string to be set for each row in the document

 ](*,) 

So this would set

(Loop nr1)
line=Line 1
(Loop nr2)
line=Line 2


and so on...

Does anyone know?

---

### Post by lt_kije on 2005-06-07
I'm not clear on your question; do you mean...
```

lines.txt   ->   lines_new.txt
Line1       ->   myLine1
Line2       ->   myLine2
Line3       ->   myLine3

```

If so, there's lots of ways to do this; are you comfortable with BASH, Perl, Python or sed/awk? Also, does each line need to be changed to one single string (ie Line1 -> newLine, Line2 -> newLine) or each line changed to a unique new line (ie Line1 -> newLine1, Line2 -> newLine2)?

lt_kije

---

### Post by Zyko on 2005-06-07
[QUOTE=lt_kije]I'm not clear on your question; do you mean...
```

lines.txt   ->   lines_new.txt
Line1       ->   myLine1
Line2       ->   myLine2
Line3       ->   myLine3

```

If so, there's lots of ways to do this; are you comfortable with BASH, Perl, Python or sed/awk? Also, does each line need to be changed to one single string (ie Line1 -> newLine, Line2 -> newLine) or each line changed to a unique new line (ie Line1 -> newLine1, Line2 -> newLine2)?

lt_kije[/QUOTE]
 Well, i use bash. 

Its a mailsystem for a website project i'm doing. And i'm trying to learn the *nix commands, and work with them.

I just want to load the results of the line into a string. then send a mail from there.


i tried with sed.
```

cutfirst=2
cutlast=4
id=`sed -e '1,$cutfirst d' -e '$cutlast,$allmails d' < projectmails.txt`

```

but i could'nt make it work.

I hope its better explained now.

//Zyko

---


---
title: "Command line text manipulation help needed"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by wounded on 2006-11-30
ok, I have a really simple question that i am not smart enough to solve myself ><


I've messed around with sed, tr, and some toher text manipulating command line programs but cannot find one (Or cannot figure out how to) to do this very simple task -_-

I just need a program that takes input and deletes the first X characters of each line and displays the resulting lines.

Is there someway I could do that? Everything ive tried/read about deals with entire lines or things where you know specifically what the characters are. 

Thanks in advance :)

---

### Post by cronholio on 2006-11-30
sed is your friend:

```
echo "12345" | sed 's/^...//g'
```

Try this and you will see it removes the first 3 characters. Change number of dots for more or less.

---

### Post by wounded on 2006-11-30
Ah! Thank you very much, I knew sed had to have been able to do something so simple! Thanks :) Anyway to do that in the middle of a line?

---

### Post by an.echte.trilingue on 2006-11-30
the command should look like:

sed 's/.\{X\}//' <filename>

where X is the number of leading characters you wish to remove.

[This is a useful link]("http://www.grymoire.com/Unix/Sed.html"), [as is this]("http://muse.linuxmafia.org/lost+found/sed1liners.txt"), and of course sed is useless without understanding [regular expressions]("http://www.grymoire.com/Unix/Regular.html").

---

### Post by an.echte.trilingue on 2006-11-30
To do that in the middle of the line, you do this/

```
sed 's/'.'\{X\}//Y' <filename>
```

where X is the number of characters you wish to remove and Y is how many characters into the line you wish to remove them.  For example, with the line abcdefg,

```
sed 's/'.'\{2\}//2' 
```

will output abefg.

Clear?

Take care,
-mat

---

### Post by Arndt on 2006-11-30
> **an.echte.trilingue said:**
> To do that in the middle of the line, you do this/

```
sed 's/'.'\{X\}//Y' <filename>
```

where X is the number of characters you wish to remove and Y is how many characters into the line you wish to remove them.  For example, with the line abcdefg,

```
sed 's/'.'\{2\}//2' 
```

will output abefg.



It will, but that's luck. The second 2 doesn't mean "skip 2 characters first"; it means "do the replacement the 2nd time the expression matches".

There is another problem: if the line consists of less than 2 characters, say 1 character, nothing will happen to it. Maybe that's what's wanted, but I would expect the line to become empty in that case.

I think the program 'cut' is the best answer to the question:

```
$ echo 12345 | cut -c 3-
345

```

---


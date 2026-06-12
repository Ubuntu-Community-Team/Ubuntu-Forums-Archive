---
title: "stripping html tags"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-06
is there a linux terminal command to strip html tags from a file?

---

### Post by davmac on 2005-10-06
I think sed is the answer. Probably something like;

sed 's/<.*>//g' oldfile.html  > newfile.html

But I've not really got to grips with sed yet. Manual available at [http://www.gnu.org/software/sed/manual/sed.html](http://www.gnu.org/software/sed/manual/sed.html)

HTH,

Dave Mac

---

### Post by dgrafix on 2005-10-06
lol that worked great. But now i just need to find a way of deleting all the blank lines

---

### Post by davmac on 2005-10-07
The answer to question 2 is the same! Sed again.

Have a go at;

sed '/^$/d' oldfile.txt > newfile.txt

Dave Mac

---


---
title: "How can i get rid of blank lines in a file"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-06
How can i get rid of blank lines in a file, im writing a script to strip an html doc of tags (which i have managed do do now. But i need to know how to delete all the blank lines.

---

### Post by cwaldbieser on 2005-10-06
[QUOTE=dgrafix]How can i get rid of blank lines in a file, im writing a script to strip an html doc of tags (which i have managed do do now. But i need to know how to delete all the blank lines.[/QUOTE]
Assuming the file is "blanks.txt":
```

$ grep -v '^$' blanks.txt

```
Means, don't match any lines where the beginning and end of the line are the same; print the rest.  If you don't want lines with only spaces:
```

grep '[[:alnum:]]' blanks.txt 

```
Read as, match only lines with alphanumeric characters.

---

### Post by dgrafix on 2005-10-07
doesnt seem to work, do i need > otherfilename on the end?
also when analysed i think its just the carrage returns and tabs i need to delete.

---

### Post by davmac on 2005-10-07
Hi dgrafix,

I've answered this on the other thread about stripping html tags, but just for completeness, you could try using sed.

sed '/^$/d' oldfile.txt > newfile.txt

HTH,

Dave Mac

---


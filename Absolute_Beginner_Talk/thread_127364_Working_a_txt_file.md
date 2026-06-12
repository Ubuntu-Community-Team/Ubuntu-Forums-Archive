---
title: "Working a txt file"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by warleggon on 2006-02-08
I am buidling text files and would like to be able to remove the whitespace from the single column text files. I have looked at cut fmt  and tr and didn't really find what I was looking for. Are there any other programs that run from terminal that I can use?

Thanks :)

Warleggon

---

### Post by oakz on 2006-02-08
can you be a little more specific about what you're trying to do? "removing whitespace" is pretty vague....maybe include an example?

look into "awk", it is very powerful. For example:

$ awk NF <filename>

...will print the contents of <filename> to standard out with all blank lines removed.

the following:
$ awk '/./{gsub(/^[ \t]+|[ \t]+$/,"");$1=$1;;print};' <filename>

...will print the contents of <filename> to standard out with all blank lines removed, all leading and trailing whitespace removed from each line, and remove extra spaces between fields

let me know if none of this is what you're trying to do :)

---

### Post by warleggon on 2006-02-08
I have text file with over 1700 rows. Each row contains a single word made up of between 5 and 18 chars. Trailing the word are blank spaces up to column 40. How can I get rid of the blank spaces?

I was hoping to do this from the command line as I am looking to incorporate these text files into scripts being run from a Glade application.

---

### Post by warleggon on 2006-02-08
[QUOTE=oakz]
$ awk NF <filename>

...will print the contents of <filename> to standard out with all blank lines removed.

the following:
$ awk '/./{gsub(/^[ \t]+|[ \t]+$/,"");$1=$1;;print};' <filename>

...will print the contents of <filename> to standard out with all blank lines removed, all leading and trailing whitespace removed from each line, and remove extra spaces between fields

[/QUOTE]

I tried the awk line above...wow did it work perfectly :) Now...(hehehe) what the heck is: ' '/./{gsub(/^[ \t]+|[ \t]+$/,"");$1=$1;;print};' ' and where can I read about all that greek  :p ;) :-D 

Thanks  

Warleggon

---


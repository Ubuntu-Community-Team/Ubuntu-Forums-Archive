---
title: "echo to file"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by Lambert on 2005-11-11
I've seen the echo command used before where you can add a simple line of text to a file but for the last 1/2 hour I can't seem to google a good page to help me understand. Most are simple echo variable or other text to screen, nothing to file. Maybe I'm using the wrong keywords:confused:

I read the man page and see something about an -e option then using \? commands in the syntax. but I'm unclear exactly where the \? part is entered in the syntax.

Can anybody point me to a site to understand using the -e option or in general using the echo command to add simple a line to a file?

---

### Post by apjone on 2005-11-11
[QUOTE=Lambert]I've seen the echo command used before where you can add a simple line of text to a file but for the last 1/2 hour I can't seem to google a good page to help me understand. Most are simple echo variable or other text to screen, nothing to file. Maybe I'm using the wrong keywords:confused:

I read the man page and see something about an -e option then using \? commands in the syntax. but I'm unclear exactly where the \? part is entered in the syntax.

Can anybody point me to a site to understand using the -e option or in general using the echo command to add simple a line to a file?[/QUOTE]
just try echo *text* > file.txt or to append a file use double >eg cho *text* >> file.txt

AJ

---

### Post by Lambert on 2005-11-11
Playing with these two commands it looks like when using > it creates a new file and if there is an existing file it renames it.

example, I had a file called test. when using that command with > it renamed test to test~ and created the new file test with what I echoed.

When using >> it just added it to the bottom of the file

Is that the basics?

Where do the \? commands come in. Let's say I wanted to add two lines of text to a file would I use something like this?

echo -e test1\ntest2 >> file.txt

Or is there something I'm missing such as ' or " and spaces between test1 \n test2

---

### Post by apjone on 2005-11-11
[QUOTE=Lambert]Playing with these two commands it looks like when using > it creates a new file and if there is an existing file it renames it.

example, I had a file called test. when using that command with > it renamed test to test~ and created the new file test with what I echoed.

When using >> it just added it to the bottom of the file

Is that the basics?

Where do the \? commands come in. Let's say I wanted to add two lines of text to a file would I use something like this?

echo -e test1\ntest2 >> file.txt

Or is there something I'm missing such as ' or " and spaces between test1 \n test2[/QUOTE]
the test~ is a lock file , 
> over writes 
>> appends 
to get 

text
text1
use *echo -e "text\ntext1"*

AJ

---

### Post by Lambert on 2005-11-11
thanks, exactly what I was looking for.

---

### Post by apjone on 2005-11-11
[QUOTE=Lambert]thanks, exactly what I was looking for.[/QUOTE]
No problem 

AJ

---


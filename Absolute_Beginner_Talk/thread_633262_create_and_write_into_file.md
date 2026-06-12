---
title: "create and write into file"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jmknash on 2007-12-06
Hi everyone
I was scavenging through google looking for a way to create a file and insert text into it
as a command, I couldn't find anything, maybe I'm typing the wrong keywords, but any
how I am using /tmp folder which gets deleted every reboot and wish to recreate a file
every reboot. No I cannot cp as there is no where to copy from!

an example is:
date >> /tmp/geek.txt

Which will print date into a file. 

What should I type to insert a custom text into file?
key 1234567890abcdefg > /tmp/geek.txt

Jon

---

### Post by Dr Small on 2007-12-06
Using >> will add it to the bottom of the file.
Using > will completely overwrite the file, with whatever you are dumping into it.

---

### Post by jmknash on 2007-12-06
Ok, how do I add text to a file?

---

### Post by amingv on 2007-12-06
> **jmknash said:**
> Ok, how do I add text to a file?

Try

```
**echo** key 1234567890abcdefg > /tmp/geek.txt
```

Note the above will overwrite, use >> to add.

---

### Post by jmknash on 2007-12-08
Problem with echo tho..
if you put a * within any text it will print the file names within dir inside of text output.
echo abc * 123  > /tmp/test.txt

---

### Post by amingv on 2007-12-09
> **jmknash said:**
> Problem with echo tho..
if you put a * within any text it will print the file names within dir inside of text output.
echo abc * 123  > /tmp/test.txt

On all those characters that *do something* you need to use a backslash '\' as an escape character.
To achieve the result you want you would type:

```
echo abc \* 123 > /tmp/test.txt
```

I always find it funny that you must actually use a backslash to print a backslash :)

```
cout<< '\\';
```

---

### Post by santosh_gr on 2007-12-09
try

echo 'test ! " £ $ % ^ & * ( ) " \ \ \ |  :; ' >> >> mytestfile

it will print 

test ! " £ $ % ^ & * ( ) " \ \ \ |  :;  

into mytestfile

which means that whatever you need to pass to a text file just include that within single quotes '    <text here>    '

---

### Post by SOULRiDER on 2007-12-09
Some characters like * or \ need a \ before them to make them work.

For example, if you want to write a * you will have to type \* instead or just *. The same gors for the \, if you want to write a \ to a file you will have to type \\

---

### Post by santosh_gr on 2007-12-09
Not required with single quotes.

if you tried a genuine command within single quotes.  It will be displayed as is. e.g below.

echo 'cat *'
echo 'ls *'
echo 'ls \'
----------------------
if you tried the same commands without single quotes or with double quotes you will get an error or some other msg.

echo cat *
echo ls *
echo ls \
 OR 

echo "cat *"
echo "ls *"
echo "ls \"                     this is in double quotes.

---

### Post by jmknash on 2007-12-09
Great! both / and ' quotes works. Thx

---


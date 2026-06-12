---
title: "apt-get install (how do I run it now?)"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-01-03
Ran this:

```
sudo apt-get install biew
```
Seemed to work out just fine ...
Closed the terminal by typing exit and hitting enter.

Now I can't find anything called biew on my laptop ...
How do I run it? :rolleyes: 

[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto) didn't clear it up for me ...

---

### Post by Drew32 on 2006-01-03
Did you try typing biew into a terminal window?

---

### Post by estel on 2006-01-03
Open the terminal and type biew.

**Edit**: Beaten to the punch cos I was checking to see what the package was :P

---

### Post by meborc on 2006-01-03
for executing```
biew
```for checking where the **** it is in the system```
whereis biew
```good luck :D

---

### Post by Steff_DK on 2006-01-03
wrote:

```
biew
```
and got this:
```
Binary Viewer v 5.6.1-i386.Unix/Curses Build: Aug 13 2004
 Usage: biew [OPTIONS] file...

  -a    autodetect mode (default)
  -b    view file in binary mode
  -d    view file in disassembler mode
  -h    view file in hexadecimal mode
  -t    view file in text mode
  -s    change size of file to NNN bytes (create, if file does not exist)
  -i    ignore .ini file (create new)
  -?    display this screen

```
Then I typed:
```
biew -h
```
but got same reply again ???
Can't seem to open a file for viewing ... :(

---

### Post by estel on 2006-01-03
Type
```
biew path/to/file
```

The -b, -d, -h etc. will chose which mode to view it in. Use -h for viewing as text.

---

### Post by estel on 2006-01-03
. dup

---

### Post by estel on 2006-01-03
Omg! I blame Firefox, sorry, don't have a clue what happened there.
**Edit** Overreacted because I saw 10 posts :s. Sorry for double post.

---

### Post by Steff_DK on 2006-01-03
Got it working when typing the filename as well :cool: 

Good thing this is the ABSOLUTE beginners area - thanks guys! ;)

---

### Post by estel on 2006-01-03
No problem :)

---


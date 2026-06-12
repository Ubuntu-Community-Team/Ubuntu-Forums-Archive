---
title: "How do i mass edit text files?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-09-23
Hi everyone,

I downloaded many web pages and would like to mass edit them.

How do i do this in linux?

```
<SCRIPT language="Javascript">
<!--

// FILE ARCHIVED ON 20010106121700 AND RETRIEVED FROM THE
// INTERNET ARCHIVE ON 20070923114437.
...etc...

//-->
</SCRIPT>
```

would like to get rid of the above...

and change ```
<BASE HREF="http://
```to ```
<!<BASE HREF="http://
```

thanks

---

### Post by LaRoza on 2007-09-24
You could use a programming language like Python or Perl to do this easily.

---

### Post by rsambuca on 2007-09-24
> **LaRoza said:**
> You could use a programming language like Python or Perl to do this easily.

Wow!  That was helpful :rolleyes:

---

### Post by LaRoza on 2007-09-24
> **rsambuca said:**
> Wow!  That was helpful :rolleyes:

It was more helpful than that.

I know nothing of the OP, and the abilities the OP has. To do things in bulk, scripts are involved, and Python and Perl excel at this type of programming. 

Saying "Open each file and use the search and replace feature of the text editor to replace the text" will work, but probably not what was sought.

Or did you expect me to write this myself, without knowledge of the system and files involved?

---

### Post by master_kernel on 2007-09-24
I have been experimenting with python. Use something like the below quote:

> 
#!/usr/bin/env python
stext = 'SEARCH TEXT'
rtext = 'REPLACE TEXT'
input = open('INPUT FILE')
output = open('OUTPUT FILE', 'w')
for s in input:
output.write(s.replace(stext, rtext))
input.close()
output.close()


I'm not guaranteeing this will word :)

---

### Post by LaRoza on 2007-09-24
> **master_kernel said:**
> I have been experimenting with python. Use something like the below quote:


The os module has functions for viewing the contents of a directory and storing it in a tuple. A loop through the tuple, applying the above type code, will do what you want.

I am at school, without my computer and Python, so I can't do it, sorry. I would have otherwise.

---

### Post by master_kernel on 2007-09-24
> **LaRoza said:**
> The os module has functions for viewing the contents of a directory and storing it in a tuple. A loop through the tuple, applying the above type code, will do what you want.

I am at school, without my computer and Python, so I can't do it, sorry. I would have otherwise.

I don't understand. Do you mean that import os should be under the header?

---

### Post by master_kernel on 2007-09-24
For reference, here is a Python script I wrote. Mostly copy-and-paste, it took me a while, but I learned some things.

[http://kcheck.sourceforge.net/scripts/buildpool.py](http://kcheck.sourceforge.net/scripts/buildpool.py)

---

### Post by hopelessone on 2007-09-26
is pyhon already installed in ununtu 7.04?

---

### Post by stig on 2007-09-26
It depends what you mean by "mass" - 100s of files or just a few dozen? I know nothing about Python etc so when I want to edit multiple files I simply open them simultaneously in a text editor, do a search & replace on all simultaneously, then save, close all. This is fine for my web pages.

It's easy in Bluefish, for instance. Probably Gedit can do it too.

But then I'm allergic to programming! ;)

---

### Post by hopelessone on 2007-09-26
100's

---

### Post by master_kernel on 2007-09-28
> **hopelessone said:**
> is pyhon already installed in ununtu 7.04?
Yes.

---

### Post by bmeyer on 2008-03-15
I know this is an old thread, but...

Have you ever tried Meld?  It's a mass "search and replace" tool that allows the use of regular expressions.  Install it with Synaptic.

---


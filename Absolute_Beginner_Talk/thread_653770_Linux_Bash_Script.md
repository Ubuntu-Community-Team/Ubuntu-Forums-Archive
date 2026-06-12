---
title: "Linux Bash Script"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by muskan05 on 2007-12-30
Thank you very much in advance!!

---

### Post by blueridgedog on 2007-12-30
Are you looking for someone to code these things up for you or help learning scripting with these as examples?  Personally I would use Perl for these tasks and this would indeed be a good start towards learning Perl.

Why do you want the first item and what would your data source be?

Each item you ask for is not hard, but not trivial either and is a bit beyond the scope of a help forum for Ubuntu Linux.

If it is your intent to learn this, I don't mind looking at your drafts and giving pointers/suggestions/input/examples.

I have the second item you request on-hand, you would just need to modify it to get the meta data you want.

---

### Post by MrFSL on 2007-12-30
I agree ... use perl.

---

### Post by muskan05 on 2007-12-31
Thank you blueridgedog and MrFSL for responding to my post.

---

### Post by blueridgedog on 2007-12-31
I assume the numbers are fake (fictitious, made up etc).  If you post it as an attachment I can give you a suggestion ( a bit of code that will parse the file).

Now, if given this as an assignment, it must assume you have some sort of background or training.  What class is it and what has lead up to the expectation that you can do these things?  I will post my web page script as a starting point, but have to get it from a backup.

---

### Post by twiceasworn on 2007-12-31
Sigh, don't do this kid's homework.  Why do people post their homework here?  I dont get it.

---

### Post by nick_h on 2007-12-31
> Sigh, don't do this kid's homework.
Yes, I agree, but I don't see any problem with suggesting appropriate manual pages to read.

The first problem could be solved using awk.  awk is good at reading files a record at a time and splitting the data into fields.  For the manual page, type:
```
yelp man:awk
```

The second problem involves getting a list of files with their meta data and then processing this into HTML.  A colon separated list of files and meta data could be easily produced using the find command with the -printf option.  The output of this could again be processed with awk.

Have a look at:
```
man find
```

---

### Post by MrFSL on 2007-12-31
> **twiceasworn said:**
> Sigh, don't do this kid's homework.  Why do people post their homework here?  I dont get it.

Sure I agree. Homework is made to be done at home - i.e. without instruction. Either the class has already covered the needed material and you should have the tools necessary to complete it - or the home-work was assigned with a bit of home-study which (if done thoroughly) should make the answer somewhat obvious. 

In my experience homework is multi purposeful. It is not only part of your grade but also a tool by which the Instructor can gauge your understanding by seeing you execute without instruction.

Back when I was going form my B.S. in math there would be nights where I pounded away at an answer. The steps weren't obvious at all - and I felt sure that the instructor had failed to teach us some important piece to the puzzle. When I finally "hacked" out an answer it felt great. I have been "hacking" away at computers and technology ever since.

My suggestion - read the notes - read the text - read the assignment - devote some time!

If you still can't figure it out thats FINE! Show the work you did in trying to figure it out! Perhaps the whole class can't figure it out. Perhaps your instructor assigned the wrong question. Perhaps... ... ... etc. If I brought in 5 pages of scrap paper I never failed a homework assignment!

Cheers ;)

---


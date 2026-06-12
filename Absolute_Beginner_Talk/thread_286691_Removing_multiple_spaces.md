---
title: "Removing multiple spaces"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2006-10-28
How do I remove multiple spaces and just leave it as a single space?  Can this be done from console without having to open the file with a program?

Original:
```
blah    blah      blah  blah   blah
```
Result should look like this:
```
blah blah blah blah blah
```

---

### Post by davmac on 2006-10-28
I think the instream editor sed is the answer.

I've not really used it much but if you open a terminal and type:

sed 's/  */ /g' oldfilename > newfilename (the bit in quotes is s, slash, space, space, asterisk, slash, space, slash, g)

This will replace all double spaces with a single space.

Hope this helps,

Dave Mac

---

### Post by newbie22 on 2006-10-28
Thanks!

But what if I want to change two things at once, how would I do it?  Like I want to change all the double/multiple spaces and double periods into singles.

If I did this:
```
sed 's/  */ /g' oldfilename > newfilename && sed 's/..*/./g' oldfilename > newfilename
```
The last code would overwrite the first.  Writing it from oldfilename to newbilename back to oldfilename again would work, but seems illogical.  Is it possible to replace more than one thing in a single code?

---

### Post by davmac on 2006-10-29
Just gone past the level of my sed knowledge! But of you have a look at [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html) you'll see that with the "-e" option you can specify multiple search/replace strings, as follows;

sed -e 's/old1/new1/g' -e 's/old2/new2/g' oldfilename > newfilename

It really is a phenomenally powerful command, and every time I look at it I find something special. Thanks for the question - it prompted me to learn something new.

Hope this helps,

Dave Mac

---


---
title: "Comprehensive information: tar files"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-04-04
I'm looking for a comprehensive how-to on tarballs and how to unpackage them. I'm asking in absolute beginners, because unpackaging tar seems to be a subject that I've often seen asked, but only answered partially; attempts are still ineffective. I have bits and pieces: a tar command that produces this:

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

or perhaps this: bash: syntax error near unexpected token `newline

And after searching high and low, I've only discovered that I'm by no means the only person getting these.

There's talk of directory navigation, but more information is needed there. There is a mention or two of unzip which I have, but apparently there's a way to use it that I haven't slogged through yet.

Then, of course, something about archiving; I have some clue that this is somehow involved, but what is that exactly and what is the process?

Every newbie (including me) who is struggling would greatly appreciate whatever assistance is available on the complete A-Z tar unzipping process.

---

### Post by zvacet on 2007-04-04
```
tar xvfz filetar.gz
```

---

### Post by Skrynesaver on 2007-04-04
[http://www.gnu.org/software/tar/manual/html_node/tar_33.html#SEC33](http://www.gnu.org/software/tar/manual/html_node/tar_33.html#SEC33)
is the complete lowdown on tar, the problem is it's a complex command due to it's age and evolution.
> 
Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

could you paste the command used to produce this error please

---

### Post by Aurora Borealis on 2007-04-05
Thank you both for your replies. I wish I could remember what command i used; I was just cutting and pasting anything I could find off the web.

---


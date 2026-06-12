---
title: "Acrobat Reader with Dapper"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by te.ss on 2007-05-30
When I start the Acrobat Reader, only an initial window, displaing a version 7.0 and messages like "initializing acrobat ....", appears for a moment and disappears.  

I have installed Acrobat Reader from synaptic package manager to read & print a PDF file which contains Japanese characters since Evince does display Jap.lcharacters but failes to print them.

I am using Dapper. 

What did I go wrong and how can I fix this?  

Thanks

---

### Post by taurus on 2007-05-30
What happens if you run it from a terminal to see what the error message is?

Applications -> Accessories -> Terminal
```
acroread
```

---

### Post by te.ss on 2007-05-30
The initial window showing ACROREAD 7.0 appeared and very quickly disappeared.

---

### Post by BevanFindlay on 2007-05-30
Another question though: why are you needing to install Adobe Acrobat Reader?

If all you are doing is opening PDF files, there are a number of open-source PDF readers, including one included in Ubuntu "out of the box" ("Evince" in Ubuntu Feisty).  If you double-click on a PDF file, it will open it automatically.

Even in the Windows world, there are (in my opinion) better PDF readers than Adobe, which are just as functional but are a lot smaller and load faster.

That help any?

---

### Post by te.ss on 2007-05-30
BevanFindlay,

First I used Evince (0.5.2) which came in Dapper and it was ok, though the fonts are not very good, as far as looking at the document on screen.  When I tried to print the document with Japanese characters, it all came out wrong.  Since I used Acrobat Reader with WIndows XP, I installed it hoping it would solve my problem.  Obviously, it didn't.  

Sigh

---

### Post by BevanFindlay on 2007-06-12
Hmm, doh.  Problems indeed.

You could try Foxit - it's what I use under Windows (being ~9 times smaller and ~6 times faster than Adobe Acrobat) which apparently now has a Linux version:
[http://www.foxitsoftware.com/pdf/rd_linux.php]("http://www.foxitsoftware.com/pdf/rd_linux.php")

Hope this helps.

---

### Post by te.ss on 2007-06-13
BevanFindlay

I downloaded Adobe Acrobat directly from Adobe web site and installed it.  Voila.  It worked.  
But as you pointed out before, it is kind of slow.  
I tried foxit and it closed down as soon as I tried to open a PDF file.   But at least I can read and print PDFs.  Maybe I'll try foxit later when I get a bit more used to Linux things. 

Thanks

---

### Post by BevanFindlay on 2007-06-13
Cool, good to hear you got something working. :)
Yeah, from the look of the Foxit site, it seems like the Linux version might still be very beta.  Still, their Windows one is nice and small and fast.  Hopefully you manage to find something that works for you in the end.

---


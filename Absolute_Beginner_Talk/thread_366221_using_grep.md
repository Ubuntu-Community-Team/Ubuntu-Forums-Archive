---
title: "using grep"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Mariane on 2007-02-20
Hi, 

Does someone knows how to use grep or find without getting all the 
warnings, please? 
I mean, a list of
<such directory>: permission denied
<such file>: input/output error
etc... 

It makes it hard to find the result in the middle of all these warnings. 

Alternatively, would someone know how to redirect the output of 
something like
grep -r '# emacs' *
to a file? Then even with the warnings I could still search the file later. 

Cannot always search the terminal screen, first because there are very 
many warnings to read and second because sometimes you cannot even 
scroll back far enough to see all the output. 

Thank you

Mariane

---

### Post by kelbizzle on 2007-02-20
What kinds of files are you looking for? I use beagle for searching. It's really fast and it also re indexes the files as they are changed. By default it searches your home folder. you can add more locations to index if you wish.  Heres the thread [http://www.ubuntuforums.org/showthread.php?t=364054](http://www.ubuntuforums.org/showthread.php?t=364054)

---

### Post by LotsOfPhil on 2007-02-20
grep -r '#emacs' * > file 

or grep -r '#emacs' | more

You are getting the errors because grep '#emacs' * is telling grep to look in everything in the directory. If you aren't allowed to look in there, grep will get the error.

---

### Post by LotsOfPhil on 2007-02-20
> **kelbizzle said:**
> What kinds of files are you looking for? I use beagle for searching. It's really fast and it also re indexes the files as they are changed. By default it searches your home folder. you can add more locations to index if you wish.  Heres the thread [http://www.ubuntuforums.org/showthread.php?t=364054](http://www.ubuntuforums.org/showthread.php?t=364054)

Oh man, don't tell her not to use grep. No need to dumb everything down; she asked about grep. Learn grep, learn regular expressions.

---

### Post by Mariane on 2007-02-20
Thank you for your answers.

I am looking for the file containing the preprocessing directive that 
cause an error. 

I can open a failsafe session but not a proper session. When I try to 
open a proper session it tells me that # emacs something or other 
(a comment, apparently) is not a proper preprocessing directive. But 
it doesn't tell me where this # emacs comes from. So I'm trying to 
discover it. 

So I have to use grep, with -r which I hope means it's going to look 
everywhere. I run it as root to have as few warnings as possible, but 
I still get some. I know what they mean, I just wish there was a way 
to prevent them from being displayed. 

grep -r  '# emacs' > file 
doesn't work, I don't know why

grep -r  '# emacs' | more
seems to work, but how can it know where I want it to store the results? 
Or is there a special location, like a.out? 


Mariane

---

### Post by Maestro23 on 2007-02-20
Check the man page on grep for its syntax.

> man grep


---

### Post by Mariane on 2007-02-20
Done. Is it this one you mean? 

 -l, --files-with-matches
Suppress normal output; instead print the name of each input file  from  which  output would normally have been printed.  The scanning will stop on the first match. 

-l didn't work, but -s worked (with a warning in the man saying it wasn't GNU Linux, that GNU Linux called that -q). 
I suppose -s means "silence!" and -q means "quiet!", am I righ? 

Mariane

---

### Post by LotsOfPhil on 2007-02-20
> **Mariane said:**
> Thank you for your answers.

grep -r  '# emacs' > file 
doesn't work, I don't know why

grep -r  '# emacs' | more
seems to work, but how can it know where I want it to store the results? 
Or is there a special location, like a.out? 

They aren't working because you don't tell grep where to search.

grep -r '# emacs' * > file
-or-
grep -r '# emacs' * > file

---

### Post by kelbizzle on 2007-02-20
> **LotsOfPhil said:**
> Oh man, don't tell her not to use grep. No need to dumb everything down; she asked about grep. Learn grep, learn regular expressions.

oh man. I didn't tell her to not use grep. I just suggested something that I use. hm...read my post again.

---


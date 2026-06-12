---
title: "Weird problem with setting vairables in csh"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by blkhatpersian on 2007-07-27
Hey everyone, hope you are doing well. I've just started learning Linux with the "unix Shells by exmaple" by Quigley and I'm on the chapter of C Shells. When it came to setting variables, I came upon a weird problem.


Whenever I try to set a variable, it will only take the first "word" in a sense that is entered. For example:

[~/textfiles]$ csh
[ ~/textfiles]$ set name = Billy Bob
[ ~/textfiles]$ echo $name
Billy


Now when I set Billy Bob in quotation marks, it works. Now the example in the book clearly displays the same thing without entering in quotation marks and I'm stumped. The thing is that I typed the exact example from the book so it can't be that. Did I simply change a setting somewhere without noticing. 

Help would be appreciated for a Linux Newb :D

Thanks,

blkhatpersian

---

### Post by blkhatpersian on 2007-07-27
ok im sure this is a simple problem for experts out there....so how is it my thread hasn't gotten any respones but  the threads that were posted 5 minutes ago got 14 responses?  :/

---

### Post by asmoore82 on 2007-07-27
er... 
Throw away that book and get something from the O'Reilly series :KS
or just use wikipedia and wikibooks

no respectable shell should not break tokens at whitespace without quotes or \

---

### Post by blkhatpersian on 2007-07-27
I messed around with wordlists from input strings before this error came up...if that helps someone bring out a solution.

---

### Post by pmg on 2007-08-04
I've used many different version/flavors of csh over the years and I don't recall any of them ever setting variables like that.  You have to escape the white space in some way, with quotes, backslash, or you can make an array:
> 7 ~->set name = (Billy Bob)
8 ~->echo $name
Billy Bob
9 ~->echo $name[1]
Billy


I suspect it's an error/typo in your reference.

---


---
title: "How do I run .pl files?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by azharc on 2006-11-01
I have two scripts I want to run, they have an extension of .pl , how do I run them?
It's [these two.]("http://www.jobeus.net/~brian/itunesimport.html")
I searched and couldn't find an answer, maybe it's too noobish to ask :D

Thanks :)

---

### Post by whizbaby on 2006-11-01
Guess making it executable will help:
chmod +x *name_of_script*

then run it like (when in same directory with script)
./name_of_script.pl

---

### Post by azharc on 2006-11-01
I got this :
> 
Can't locate Date/Manip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./convert_itunes.pl line 37.
BEGIN failed--compilation aborted at ./convert_itunes.pl line 37.

Am i missing a dependency or something?

---

### Post by distroman on 2006-11-01
you could try,
sudo aptitude install perl

---

### Post by azharc on 2006-11-01
Nope, still no luck :(

---

### Post by jrings on 2006-11-01
Well, a Perl module Date::Manip is missing.

You can try sudo cpan install Date::Manip

CPAN may bug you when it first installs. Just answer as good as you can and press Enter a lot ;)

---

### Post by hearnden on 2006-11-01
That file has the line:
```

# You need perl (duh), the Date::Manip package, and sqlite3.

```

So you probably need to get the Date::Manip module  There is a package in the repos called libclass-date-perl, but it might not be the same one.  Googling Date::Manip tells you where you can get it, but it would be easier if there is an apt-get way to do it.  Hope you find it.

---

### Post by big dizzle on 2008-01-27
just thought i'd let you know that i would have asked how to run .pl files if you hadn't. this thread helped:)

---


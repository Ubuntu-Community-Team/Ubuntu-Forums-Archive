---
title: "[SOLVED] PERL: writing in unicode format"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-02-08
Hi All,

I need to read and update unicode files through perl script. I have try to write codes something like below:

open OUT, ">:encoding(UTF-16LE):via(File::BOM)", "$writefilepath";
print OUT "$content";
close (OUT);

but its not working successfully. I am using perl version 5.10.

Please anybody help me.

Regards,
Srikrishnan

---

### Post by gate on 2008-02-09
[http://perldoc.perl.org/perluniintro.html](http://perldoc.perl.org/perluniintro.html)
[http://perldoc.perl.org/perlunitut.html](http://perldoc.perl.org/perlunitut.html)
 That seems to have a decent little tutorial on how to do it, the second looks more succinct to me. Good Luck!

---

### Post by srikrishnan on 2008-02-11
Hi gate,

I hope it would be useful for me.

I will try and let us inform

Regards,
Srikrishnan

---


---
title: "CSV splitter?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by iluminate on 2007-01-30
Hi all,

I do not know if any of you Ubuntu or *nix guys have experienced the same problem...
But what do I do, if I have lets say a CSV file that is 100 MB large and because there is a row
limit in OpenOffice Database of 65000 row I can not import the complete list?

Any ideas what to do?
Use some kind of splitter or ?

Any hints would be great coz I am stuck right now :(

---

### Post by Jussi Kukkonen on 2007-01-30
> 
Use some kind of splitter or ?
Try *split -l 60000 <filename>* or use a real database.

---

### Post by jvc26 on 2007-01-30
I'd recommend trying porting to something like Mysql as then you have a much greater flexibility to play with and then you have a real database on your hands :)
Il

---

### Post by iluminate on 2007-01-30
Yes I know but not everyone knows Mysql...
Hmm wierd stuff indeed.
Tried to import it via phpmyadmin but the limit is set to 2MB or something.
Shall try to check php.ini settings.
Sucks to B a n00b!

---


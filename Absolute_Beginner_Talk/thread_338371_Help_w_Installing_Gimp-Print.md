---
title: "Help w/ Installing Gimp-Print"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2007-01-14
Hello and thank you for looking at this thread,

I would like to install Gimp-Print printer drivers
(gimp-print-4.2.7.tar.gz)

I downloaded the source files from it's page at sourceforge.net
[http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=32749](http://sourceforge.net/project/showfiles.php?group_id=1537&package_id=32749)

I put the extracted file into my home directory then changed the directory to that folder, doing cd /home/andrew/gimp-print-4.2.7 

The instructions say to then type  ./configure....that ran but got an error message at the end saying 
............................................
>>checking lex output file root... ./configure: line 2284: lex: command not found
configure: error: cannot find output from lex; giving up
andrew@Ubuntu-one:~/gimp-print-4.2.7$ make
make: *** No targets specified and no makefile found.  Stop.
....................................................................

As the copied command lines show,  i then followed the instructions to then type 'make'  and I was told no file was found.

Can someone tell me what went wrong and how to fix it?

I really do appreciate the help,

Andrew

---

### Post by riven0 on 2007-01-14
Well, you know Gimp-Print ver 5.0.0 is in the repositories. So why don't you just install it through there?:

> sudo apt-get install gimp-print

---

### Post by andrew222 on 2007-01-14
Thank you, I will do that.  My goal is to also access the code through CVS as well...

---

### Post by petersjm on 2007-01-14
It would be better to use 

```
sudo aptitude install gimp-print
```

instead of "apt-get".

---


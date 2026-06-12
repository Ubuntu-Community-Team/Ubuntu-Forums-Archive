---
title: "Perl compiler"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Zaid on 2006-09-09
How do I execute perl files  ? Thanks. I tried looking in google but seams ubuntu was made in perl ??? so ... Thanks.

---

### Post by Zaid on 2006-09-09
So I figure I need to run so when I access it in command prompt it just opens up text pad . So then I tried chmod

Chmod x (file ) 
And it still just opens the file.

---

### Post by jordanmthomas on 2006-09-09
```
whereis perl
```
at the top of your perl program put this
```
#!*pathtoper*l
```
I believe you can execute it then.

Or, you could just do 
```
perl filename
```

(Just for the record, I have never used perl, so don't get mad if it doesn't work)    :)

---

### Post by Zaid on 2006-09-09
This is what I get 

admin@Master:~$ perl
/home/admin/Desktop/perl.pl
Bareword found where operator expected at - line 1, near "/home/admin"
        (Missing operator before admin?)

---

### Post by jordanmthomas on 2006-09-09
You need to put perl on the same line as your file, like this
```
perl /home/admin/Desktop/perl.pl
```

---

### Post by jordanmthomas on 2006-09-09
here is how I got a perl script to run
```
nano hello.pl
```
put this in it
```

#!/usr/bin/perl
print "Hello World";

```
```
chmod +x hello.pl
./hello.pl

```

or you could do 
```
perl hello.pl
```

---

### Post by Zaid on 2006-09-10
I got it working. I didn't have the perl packs installed. Thanks guys for your help.

---


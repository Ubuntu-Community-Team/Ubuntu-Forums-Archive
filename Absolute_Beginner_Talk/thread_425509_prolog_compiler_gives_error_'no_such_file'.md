---
title: "prolog compiler gives error 'no such file'"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by nymphaeles on 2007-04-27
After installing gprolog from universe, I try to compile a database, and it gives me this error
 
```

name@u704:~$ ls
Desktop  Examples  test1.pl
name@u704:~$ gplc test1.pl
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
compilation failed
name@u704:~$ 

```

Can someone points out what wrong with my install?

It works, however, if I don't have to compile a database:

```

name@u704:~$ gprolog
GNU Prolog 1.2.18
By Daniel Diaz
Copyright (C) 1999-2004 Daniel Diaz
| ?- 

```

Thanks.

---

### Post by finer recliner on 2007-05-01
i think you have the wrong idea, let me try to explain it to you. you dont compile prolog applicatsion. you run your database of facts and rules, and then ask it questions concerning your database. its an interactive process.

i have SWI-Prolog (Multi-threaded, Version 5.2.13) installed (got it from ubuntu repos)
but your prolog application should work similarly:

```

$ prolog
Welcome to SWI-Prolog (Multi-threaded, Version 5.2.13)
Copyright (c) 1990-2003 University of Amsterdam.
SWI-Prolog comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
Please visit http://www.swi-prolog.org for details.

For help, use ?- help(Topic). or ?- apropos(Word).

?- ['ps94.prolog'].
% ps94.prolog compiled 0.00 sec, 400 bytes

Yes
?-


```.


you include external files using ['filename']. as seen above. prolog will return "yes" if succesfull. now you ask prolog questions, hence the ?- prompt. 


moral of the story is that your prolog app doesnt take in external files in as arguments (just as mine doesnt). you have to call it once prolog is running.

---


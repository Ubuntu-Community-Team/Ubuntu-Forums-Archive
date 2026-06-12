---
title: "compiling how???"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-03-26
hi all 

just a quicky. how do i go about compile all the files in a .tar.bz2. Exsample:

reconstructer_2.5_all.tar.bz

Remember im a newbie

ta,
nolander.

---

### Post by cowlip on 2007-03-26
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by Nolander on 2007-03-26
the program im trying to compile(reconstructer_2.5_all.tar.bz) has no:
config or make file

help????????

ta,
Nolander

---

### Post by AtrejuT on 2007-03-26
Did you extract it first? If you did (as mentioned in the quide) a directory should have been created that contains all the files. Can you tell me what files there are?

---

### Post by Nolander on 2007-03-26
heres the list:
/reconstrutor/glade/
/reconstrutor/lib/
/reconstrutor/modules/
/reconstrutor/lang/
/reconstrutor/credits.txt
/reconstrutor/licence.txt
/reconstrutor/read me.txt
/reconstrutor/known_issues.txt
/reconstrutor/reconstrutor.py

ta,
Nolander.

---

### Post by AtrejuT on 2007-03-26
probably all you'll need to do from a console if you are in the correct directory is 
```

./reconstructor.py

```
but you could also have a look in the read me file to see if they offer advice.

oh, and if that doesn't work do (again in the correct dir)
```

chmod +x reconstructor.py

```
and try again...

---

### Post by Nolander on 2007-03-26
i allway read read me's

thanx,
nolander

---


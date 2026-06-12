---
title: "Command not Found"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by phil79 on 2007-07-20
Have just returned to Ubuntu after 18 months.....installed fine.

I have an executable called "setup" (and associated files) that installs some software. 

But I always get "command not found". Now i realise this is a new feature, but how do I disable it ?

The software is NOT from a respository - just an executable "setup" and other support files.

In the "old" days I could just type "setup" and off it would go.

Even if I type the full path /home/phil/blah/blah/setup it does not work....

Please help going mad.

Ta

---

### Post by Mornedhel on 2007-07-20
Did you

1. check if the /home/phil/blah/blah/setup file actually exists ? (I'm guessing you did)
2. check if you had exec rights on it ?
3. Thanks for the correction, FunkyJack. Read the OP too fast.

What does the error message say ?

---

### Post by FunkyJack on 2007-07-20
```
sudo chmod a+x /home/phil/blah/blah/setup
```

That should fix the problem :)

Full path is without the dot.
Only if you are in the /home/phil/blah/blah/ folder then you must
./setup
Or in /home/phil/blah/ then
./blah/setup

---

### Post by phil79 on 2007-07-20
Thanks guys - but no luck....I had already done that ;)

I can list the file:

-rwxr-xr-x 1 pneaves phil  201771050 2007-07-20 11:12 setup


  ./setup 
bash: ./setup: No such file or directory


ls
backup_zips    setup 


But something odd, I am in:

pwd
/home/phil/MM

touch foo
touch: cannot touch `foo': Permission denied

The user account is OK as in /home/phil "touch" is OK

All very confusing.....

---

### Post by Mornedhel on 2007-07-20
What rights do you have on the MM folder ? Try and chmod 744 it.

The rights on folders behave differently :

Read : list contents
Write : create/delete files
Execute : cd to directory

(Am I correct ?...)

---

### Post by phil79 on 2007-07-20
sudo chmod 777 MM

cd MM

 ./setup 
bash: ./setup: No such file or directory


:(

---

### Post by Mornedhel on 2007-07-20
I'm at a loss.

Does bash autocomplete on setup ? (Does typing "./s" then pressing TAB complete the line to "./setup" ?) Unless there's a special character or a space in that filename, I have no idea what's causing the problem... The file is there, it's executable...

---

### Post by phil79 on 2007-07-20
Mornedhel,

Yes it does autocomplete - so Ubuntu "knows" it is there !

This is what I do not understand......  :confused:

---

### Post by Mornedhel on 2007-07-20
OK.

Can you mv it to another name, and execute that one ? (Or maybe mv will choke as well. Let's hope not.)

---

### Post by phil79 on 2007-07-23
Tried that - same problem.....approaching giving up time !

---

### Post by RomeReactor on 2007-07-23
Hi. Did you make this file yourself? is it a bash file? e.g.
```
bash setup
```

---

### Post by Mornedhel on 2007-07-23
This may be more difficult to test.

Can you read it from another operating system (live CD, dual boot...) ?

RomeReactor : I don't think it's going to work, if the parent bash cannot read the file...

---


---
title: "Why aren't my shell programs working"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-06-08
Hi,

I am trying to create a simple shell program to use with the at command.

I have created the program test :

adam@mshome:~$ more test
#!/bin/sh
date

When I run the command date, I get ....

adam@mshome:~$ date
Thu Jun  8 17:19:12 BST 2006


When I do the following :
adam@mshome:~$ vi test
adam@mshome:~$ chmod 755 test
adam@mshome:~$ test
adam@mshome:~$ 


I get nothing.....

The same happens when I put the echo command in the bash script. I also can't touch a file from within the script.

Is there a variable that I need to set to make this work? Or something else that I need to know?

Thanks in advance,

Adam.


P.S. if you leave the first line of the script blank, do you automatically default to a bash script as in some flavours of UNIX?

---

### Post by taurus on 2006-06-08
How about
```

./test

```

---

### Post by adam s on 2006-06-08
Duh.... I wish I had thought about something so simple.....

Thanks,

Adam.

---

### Post by harishg on 2006-06-08
if you want to run it with using just test put the test file in your /home/xx/bin file and then it would work.

---

### Post by ekarni on 2006-06-08
> if you want to run it with using just *test* put the test file in your /home/xx/bin file and then it would work.

Another way would be to add "." (no quotes) to your $PATH.

---


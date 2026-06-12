---
title: "shell script won't run :-(("
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2007-01-16
Hello,

I am running shell scripts from chapter 2 of 'Beginning Linux Programming' ( Matthew/Stone ).  I downloaded all of the code used for the book off of the Wrox website.  I tried running one called _if.sh and it just will not run,  i pasted the commands typed in,  the .sh is most certainly in the file, can someone tell me why this will not run?

the folder called /buddha is a replacement for the default name....a long numeric number I didn't care to keep typing at the command prompt


.....................................................................................................................
andrew@Ubuntu-one:~/buddha/chapter02$ chmod +x ./_if
andrew@Ubuntu-one:~/buddha/chapter02$ ./_if
bash: ./_if: /bin/sh^M: bad interpreter: No such file or directory
andrew@Ubuntu-one:~/buddha/chapter02$ 



ty,

andrew

---

### Post by taurus on 2007-01-16
First, it's not a good idea to name your file with the _ as the first character!

Second, you should change the first line of the file to

#!/bin/bash

Third, somehow when you downloaded the files, you used the wrong mode (should be ASCII) so each line contains an extra ^M thing.  So, you need to use dos2unix to strip off those ^M at the end of the lines.

If not sure, post a program here and will see what's wrong with it.

---

### Post by zerhacke on 2007-01-16
> **andrew222 said:**
> Hello,
bash: ./_if: /bin/sh^M: bad interpreter: No such file or directory


You don't have the sh shell installed.  If you change it to bash, you run the risk of it not being interpreted just right.  If you want that shell script to run exactly like the book wants it to run, you need to install the sh shell.

At the command prompt, type:

sudo apt-get install sh

And hit enter.  It should find, download, and install sh for you.

---

### Post by andrew222 on 2007-01-16
taurus:

actually, wrox publishing named the file '_if' and I agree it is not the best name for a shell script.  

Here is the fil'e script:
............................................................
#!/bin/sh



echo "Is it morning? Please answer yes or no"

read timeofday



if [ $timeofday = "yes" ]; then

  echo "Good morning"

else

  echo "Good afternoon"

fi



exit 0 

..............................................................


I will look for the application mentioned and try that out





zerhacke:

I typed in the command line to install sh and I ran into a curious error....

Is there a way to fix this??

andrew@Ubuntu-one:~$ sudo apt-get install sh
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sh
andrew@Ubuntu-one:~$ 






Thank you very much for your help.

---

### Post by zerhacke on 2007-01-16
> **andrew222 said:**
> taurus:

actually, wrox publishing named the file '_if' and I agree it is not the best name for a shell script.  

Here is the fil'e script:
............................................................
#!/bin/sh



echo "Is it morning? Please answer yes or no"

read timeofday



if [ $timeofday = "yes" ]; then

  echo "Good morning"

else

  echo "Good afternoon"

fi



exit 0 

This will run fine in bash.  Edit the top line to read #!/bin/bash and it'll function correctly.  This is the dirty way to do it, though, because later in the book there may be scripts that require /bin/sh due to differences in parsing of the two shells.
> andrew@Ubuntu-one:~$ sudo apt-get install sh
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sh
andrew@Ubuntu-one:~$ 

What the?  When did sh get removed from Ubuntu and the repos?  Gimmie just a second and I'll see if I can find you a .deb of the sh shell.

---

### Post by zerhacke on 2007-01-16
Couldn't find you a deb of the sh shell, but I did read a reminder note I had set on another forum that said bash is basically the son of sh.  I'm assuming bash would interpret sh scripts the same way sh would and then some.

Someone more knowledgeable than I could probably assist you better than me from here on out.

---

### Post by andrew222 on 2007-01-16
Hello zerhake,

I changed the first line to #!/bin/bash and got the same result. 

Thank you for looking for a sh to install, I do appreciate it.

Andrew

---

### Post by taurus on 2007-01-16
Well, it ran fine here...

```

#!/bin/bash

echo "Is it morning? Please answer yes or no"

read timeofday

if [ $timeofday = "yes" ]; then

echo "Good morning"

else

echo "Good afternoon"

fi

exit 0

```

---

### Post by andrew222 on 2007-01-16
I just figured it out with both the help of taurus and zerhacke combined.


#  I first ran dos2unix
andrew@Ubuntu-one:~/buddha/chapter02$ dos2unix ./_if


#here I am running this file as bin/sh,  the file I altered per our previous try was a file called 'arith'
andrew@Ubuntu-one:~/buddha/chapter02$ ./_if
bash: ./_if: Permission denied

# now what I did was change bin/sh to bin/bash for the '_if' file, but I decided for good programming practice recommended by taurus to rename, so it is renamed 'iffy'


.........................................................................................................
andrew@Ubuntu-one:~/buddha/chapter02$ ./iffy
Is it morning? Please answer yes or no
yes
Good morning
andrew@Ubuntu-one:~/buddha/chapter02$ 
............................................................................................................

Good morning bash!!

Thanks both to taurus and zerhacke...

I will think of you both when I continue to program my way through this book and I will be sure to look you up if I run into any more snags with the text book....


Andrew

---

### Post by taurus on 2007-01-16
I called it test.sh when I cut 'n paste your code to my machine so call it anything you want.  Remember, I am not a programmer; just a guy hanging out here...  ;)

---

### Post by andrew222 on 2007-01-16
Zerhacke,   can you find me a .deb file of sh?

Thank you... I really do appreciate your help....

---

### Post by taurus on 2007-01-16
```
ls -la /bin/sh
```

---

### Post by andrew222 on 2007-01-16
andrew@Ubuntu-one:~/buddha/chapter02$ ls -la /bin/sh
lrwxrwxrwx 1 root root 4 2007-01-01 09:49 /bin/sh -> bash

---

### Post by taurus on 2007-01-16
So basically, /bin/sh just points to /bin/bash anyway.  ;)

---

### Post by andrew222 on 2007-01-16
I'll have to change each file...

These authors were probably coding these on Red Hat and the /sh probably worked fine....

Thank you very much for your help, I also remember the help you gave to me on new years day...

Have a great evening,

Andrew

---

### Post by taurus on 2007-01-16
Since /bin/sh points to /bin/bash, I don't think you have to change the first line of each program.  Just make sure you stripe off the ^M at the end of each line with dos2unix command if needed be.

---

### Post by andrew222 on 2007-01-16
I just tried it out and you are correct....

Thank you again taurus.

---

### Post by taurus on 2007-01-16
> **andrew222 said:**
> I just tried it out and you are correct....

Thank you again taurus.

Lucky guess, eh!  ;)

---

### Post by andrew222 on 2007-01-16
I guess you're the Master Roaster for a reason :-)

---

### Post by taurus on 2007-01-16
> **andrew222 said:**
> I guess you're the Master Roaster for a reason :-)

And it smells good in the morning!

---


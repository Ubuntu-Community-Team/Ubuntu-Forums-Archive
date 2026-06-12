---
title: "shell script won't run"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by caughran on 2007-08-12
I have a small script which has worked in the past:

#!/bin/sh
cd /opt/Quackle/quacker
exec ./quacker

I get a confusing message:

jim@JIMJANET:~/Desktop$ ./runQuackle.sh
bash: ./runQuackle.sh: /bin/sh: bad interpreter: Permission denied

The permissions are set okay:

-rwxrwxrwx 1 jim jim 50 2007-08-12 16:46 runQuackle.sh

jim@JIMJANET:/bin$ ls -l sh
lrwxrwxrwx 1 root root 4 2007-05-27 16:15 sh -> dash

What's happening?

---

### Post by Billy_McBong on 2007-08-12
[COLOR="Blue"]you have to right click it do properties then go to permission  and check allow executing file as program[/COLOR]

---

### Post by schorsch on 2007-08-12
Have you or someone else edited the shell script with a windows editor? This would be the reason that there are some control signs inside the script file which bash=sh does not understand like carriage-return/line-feed on the same line

---

### Post by caughran on 2007-08-12
Edited with gedit, and the properties dialogue already has permission to execute checked.

---

### Post by caughran on 2007-08-26
Solved; somehow bash scripts were no longer associated with bash. I reassociated, and it works.

---

### Post by kevdog on 2007-08-26
What you changed the first line to 
#!/bin/bash
???

---

### Post by Duneatreides on 2007-08-26
Everytime I wrote a shell script I use the #!/bin/bash.  Also I went to the command line and typed 

chmod 755 my_script

./my_script

and it always worked.  Maybe you should try that.  

Hope that helps. 

Chris

---


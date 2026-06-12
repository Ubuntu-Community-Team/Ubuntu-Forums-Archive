---
title: "oracle 10g and a couple other questions"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by bavs on 2005-12-21
hi all

i need some help. i just installed ubuntu and oracle 10.2.0 and everything worked fine apart from one error
invalid value null for parameter PORT and it said i can edit emac script later. i have done everything as said in the oracle wiki but now when i type sqlplus in command prompt all i get is command not found.  someone please help

another thing i install a program by converting a rpm file to deb and installing that. now where will this program be? how do i run it?
thank you

---

### Post by KingBahamut on 2005-12-21
You missed port set. 

emca 

For jms, rmi, dbconsolehttp, and agent. 

Should be in the Docs somwhere, I cant remember the exact commandset for that. 

What RPM did you convert and install?

---

### Post by ape on 2005-12-21
You also need to ensure that $ORACLE_HOME/bin is in your path if you are just typing `sqlplus`.  Otherwise, change to the $ORACLE_HOME/bin directory and run `./sqlplus`.  Don't forget to set the ORACLE_HOME variable before running sqlplus or you will get a number of errors regarding .msb files not being found.

---

### Post by bavs on 2005-12-21
the rpm file is called
impronto-1.3-8.i386.rpm
its bluetooth support for j2se from rococo.com

can i just open the emac file in gedit and add port setting?

---

### Post by bavs on 2005-12-21
sorry again
how do you set ORACLE_HOME
THANK YOU

---

### Post by bavs on 2005-12-21
hi guys
 
its been 48 hrs non sleep learning to install oracle on ubuntu and atlast it works but everytime i restart i have to export orache_home !!! can someone help.

---

### Post by ape on 2005-12-22
If you look in the $ORACLE_HOME/bin directory, you should find some envrionment files.  In the standard release these will be called oraenv and coraenv.  If you are using csh or tcsh as your shell, just source the coraenv script as part of your .cshrc.  If you are using one of the sh variants (sh, bash, ksh, zsh, fish) you should source the oraenv script as part of your .profile or .bash_login.

This will set up the needed environment variables for you.

---


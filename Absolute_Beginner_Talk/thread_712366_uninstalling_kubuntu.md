---
title: "uninstalling kubuntu"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by bhougland on 2008-03-01
hey-

  I am having a trouble uninstalling all the programs of Kubuntu and need some help.  I have tried the command at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) but it didnt work.  It didnt even ask me for my password to make the changes, it just said :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What am i doing wrong?

---

### Post by wolfen69 on 2008-03-01
at login , boot to terminal session and  run remove commands.

---

### Post by bhougland on 2008-03-01
Stupid question, but how to I get out fo the Failsafe terminal?  Btw, the script worked in the failsafe terminal, but can not see the changes yet.  (I am on two computers)

Thanks

---

### Post by bhougland on 2008-03-01
Never mind.. To exit the Failsafe terminal you type........"exit"  (brilliant!)


Wolfen69 thank you for the help it worked like a charm!!!

You rock!

---

### Post by virtualXTC on 2008-03-01
> **bhougland said:**
> hey-

  I am having a trouble uninstalling all the programs of Kubuntu and need some help.  I have tried the command at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) but it didnt work. 


Which command? there are 2 different possible commands.  It's best not to be lazy and write out exactly what you did, what if that other page was down?


> **bhougland said:**
> 
 It didnt even ask me for my password to make the changes, it just said :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What am i doing wrong?

aptitude is a graphical front end for apt-get, and they both reference the same database when installing and uninstalling files.  What those errors mean is that aptitude or apt-get (or some other program, maybe synaptic) is already using the database and the new program isn't allowed to touch it until it's done, otherwise you might end up installing the same package 2ce or causing dependency problems.

Close all your package management programs then try running the apt-get commands again.  If this fails.  Log out, press ctrl-alt-f3 to get a terminal.  Log in as they user you were trying to execute the commands as.  Run the apt-get remove command you just tried to run (press the up arrow to recall the last command you entered).

---


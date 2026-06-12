---
title: "how i can define environmet variable in Ubuntu 7.04?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-05
Hi
thank you for reading my post

Can some one please explain how i can define environment variable in ubuntu?

For example how i can set JBOSS_HOME = /home/leg/jboss-04 ?

I read that export and env can do this but i want my variable to be permanent in my linux.

is there any file that i can add env variables to it?


thanks

---

### Post by lloyd_b on 2007-05-05
The normal place to set "permanent" environment variables is the .bash_profile file in your home directory. Just add "export JBOSS_HOME = /home/leg/jboss-04" to that file.

Note: I can't remember for certain, but you may need to log off and then back on before the change takes effect... 

This is for a specific user - if you need to change it for ALL users, then try making the same change to the file "/etc/profile".

Lloyd B.

---

### Post by legolas_w on 2007-05-18
the file is not in my home directory.
I create it myself, now: how i can add path at the end of current system path?

Thanks

---

### Post by lloyd_b on 2007-05-18
>  the file is not in my home directory.
I create it myself, now: how i can add path at the end of current system path?

The following line would add "/usr/local/other" to the PATH:
```
export PATH=$PATH:/usr/local/other
```

Lloyd B.

---

### Post by legolas_w on 2007-05-23
Thank you for all your comments
here is what i done

goto home folder
execute
 gedit .bash_profile

add following lines to it


export java_home = /development/jdk1.6.0_02
export PATH=$PATH;/development/jdk1.6.0_02/bin


close the file.


but it has no effect, what should i do?
when i execute 

env 


it does not show any of my entry in bash_profile file.


thanks

---

### Post by lloyd_b on 2007-05-23
As noted previously, changes to ~/.bash_profile do not take effect immediately - you need to log off and then back on before the file is read again.

Something I've discovered recently is that a second file "~/.bashrc" can also be used to set environment variables.  In the case of "~/.bashrc", the next time you open a terminal window, the changes will be in effect, as opposed to having to log off and then back on.

Some other things I noticed:
```
export java_home = /development/jdk1.6.0_02
export PATH=$PATH;/development/jdk1.6.0_02/bin
``` 
There appears to be a space between "java_home" and equal sign ("="), and another between the equal sign and the "/development/jdk1.6.0_02".  This is NOT allowed.  It should be as follows:
```
export java_home=/development/jdk1.6.0_02
```

Second, the "$PATH" appears to have a semicolon (";"), while it should have a colon (":").  With the forum fonts, the difference can be hard to see.  Let me try to expand things a bit:
```
[SIZE="5"]export java_home=/development/jdk1.6.0_22
export PATH=$PATH:/development/jdk1.6.0_02/bin[/SIZE]
```

Lloyd B.

---


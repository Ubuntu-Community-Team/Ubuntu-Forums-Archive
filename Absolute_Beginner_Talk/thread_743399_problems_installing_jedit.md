---
title: "problems installing jedit"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by christinak on 2008-04-02
Heyhey!

I posted this as an answer to a post a few hours ago, but i figure maybe this is better in a new post?? (because i figure people doen't read answers on solved posts??)

thanks for your help, in any case (and if i shoudn't be posting s.t. twice... sorry :(  )

cheers,
christina



heyhey

so, i just tried to download jedit using this:

Quote:
Originally Posted by tommy1987 View Post
Install jEdit (editor)
Install Java.
Add the jEdit repository to your etc/apt/sources.list file:
sudo gedit /etc/apt/sources.list
Add the following lines:
deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
Save and close the file.
Install jEdit:
sudo apt-get update
sudo apt-get install jedit
(optional) Make jEdit reuse windows when opening files to edit.
sudo gedit /usr/bin/jedit
Change:
... ${JEDIT} -jar "/usr/share/jedit/jedit.jar" $@
to:
... ${JEDIT} -jar "/usr/share/jedit/jedit.jar" -reuseview $@

from [http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

but, somehow, somewhere, there is a problem:

when i then type jedit in the console, i get lots of these

GC Warning: Out of Memory! Returning NIL!
GC Warning: Out of Memory! Returning NIL!
GC Warning: Out of Memory! Returning NIL!
GC Warning: Out of Memory! Returning NIL!
Segmentation fault (core dumped)
christina@tinkerbell:~$

and i tried what the next person recommended and then got this

christina@tinkerbell:~$ java -jar jedit.jar
Failed to load Main-Class manifest attribute from jedit.jar
christina@tinkerbell:~$

i did install java the other day, though, quite a new version... to be frank and honest, i have no idea what the problem is, newbie that i am

help?

thanks so much,
christina

---

### Post by Hospadar on 2008-04-02
what do you get from "java --version" or "java -v"

---

### Post by christinak on 2008-04-02
$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

---

### Post by Crafty Kisses on 2008-04-02
Not sure what version of Java you have, but have you tried an earlier version, then retried the installation?

---

### Post by christinak on 2008-04-02
an earlier version of.... java? or jedit? (neither in any case.... should i? how would that work?)

---

### Post by Crafty Kisses on 2008-04-02
I have Jedit, and it works fine, I don't have the newest version of Java though, so this might be the issue.

---

### Post by christinak on 2008-04-02
hm... might try that. however... how do i do that? (i know, it's terrible, but i don't know how to deinstall (do you call it that?) a program)
or could there be any one just very very obvious installation step i missed? (i changed the code with kate and not with gedit but it can't be that i figure...)

---

### Post by Crafty Kisses on 2008-04-02
If you want to remove Java, do the following:
```
sudo apt-get remove java
```
Find an older version of Java, and try installing that, and hopefully that works, again I have an older version of Java and Jedit works for me, but then again I'm not sure if this is the solution to the problem, just proposing a solution.

---

### Post by christinak on 2008-04-02
tried that... but no. and I can't go belower java version 5 i think it is

thanks though.

*feeling helpless and lost*

*but not so bad as kate works*

---

### Post by christinak on 2008-04-05
problem solved:

[http://blog.csmonkey.com/2007/06/how-to-make-sun-java-5-default-java.html](http://blog.csmonkey.com/2007/06/how-to-make-sun-java-5-default-java.html)

i don't know how this stuff is connected, but now it's working :)

thanks for all your help!

---


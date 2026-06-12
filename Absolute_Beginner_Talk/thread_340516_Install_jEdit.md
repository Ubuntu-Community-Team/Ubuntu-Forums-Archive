---
title: "Install jEdit"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-01-17
Hello,

Could you say me what I need to install jEdit, please?

Thanks,

---

### Post by tommy1987 on 2007-01-17
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

---

### Post by jordilin on 2007-01-17
You'll need the sun java virtual machine installed. There are tons of threads everywhere on how to do it. You'll most probably get the jedit as a jar file. You can execute it by doing```
java -jar jedit.jar
```
I don't know if jedit is in the repos, but you can download the jar file from sourceforge. 
First of all, install java from SUN (I recommend SUN java for compatibility and now java is opensource). :D

---

### Post by linux-beginner on 2007-01-17
With "sudo apt-get update" I get besides these:
> Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Release.gpg
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Release
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Packages
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Sources
Hit [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Packages
Hit [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Sources
Fetched 942B in 2m9s (7B/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

and if I type: "sudo apt-get install jedit" than these come:
> Reading package lists... Done
Building dependency tree... Done
jedit is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:confused: :confused:

---

### Post by linux-beginner on 2007-01-17
By typing jedit i get these:
> GC Warning: Out of Memory!  Returning NIL!
Exception in thread "main" GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
*** Catastrophic failure while handling uncaught exception.
GC Warning: Out of Memory!  Returning NIL!


---

### Post by linux-beginner on 2007-01-17
It's solved!
Thanks,:)

---

### Post by tommy1987 on 2007-01-17
out of interest, what was the problem?

---

### Post by rmd on 2007-01-19
hi...
i was install jEdit version 4.3pre6 with .deb file. but, it's made my ubuntu crash.
i've got this file from [http://sourceforge.net](http://sourceforge.net)
why this happened? is this version is'nt friendly for ubuntu?
oh..., i use dapper.
thx...

---

### Post by blackey on 2008-03-10
When installing jedit from sourceforge using apt-get, everything seems to install properly but when i startup the application the gui doesn't stretch, so i have very little room to actually type. Has anyone seen this, or have any idea what it could be?

---

### Post by christinak on 2008-04-02
heyhey

so, i just tried to download jedit using this:

> **tommy1987 said:**
> Install jEdit (editor)
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

GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
Segmentation fault (core dumped)
christina@tinkerbell:~$   

and i tried what the next person  recommended and then got this 

christina@tinkerbell:~$ java -jar jedit.jar
Failed to load Main-Class manifest attribute from jedit.jar
christina@tinkerbell:~$ 

i did install java the other day, though, quite a new version... to be frank and honest, i have no idea what the problem is, newbie that i am :(

help?

thanks so much,
christina

---

### Post by binilthomas on 2008-05-04
> **christinak said:**
> 
when i then type jedit in the console, i get lots of these

GC Warning: Out of Memory!  Returning NIL!
Are you using the Sun JDK? What does typing 'java -version' print? You might want to install the sun-java6-jdk package (with 'sudo apt-get install sun-java6-jdk' command).


> **christinak said:**
> 
christina@tinkerbell:~$   
and i tried what the next person  recommended and then got this 
christina@tinkerbell:~$ java -jar jedit.jar
Failed to load Main-Class manifest attribute from jedit.jar
christina@tinkerbell:~$ 
i did install java the other day, though, quite a new version... to be frank and honest, i have no idea what the problem is, newbie that i am :(
help?
thanks so much,
christina
You get this error when the META-INF/MANIFEST.MF entry within the jar file (which is similar to a .zip or .gz file) is incorrect. But that surprises me, because I just installed jedit and checked the file and the META-INF/MANIFEST.MF file and it looks good to me. Try the following on the terminal and post the results here.
cd /tmp
jar -xvf /usr/share/jedit/jedit.jar META-INF/MANIFEST.MF
cat META-INF/MANIFEST.MF

---


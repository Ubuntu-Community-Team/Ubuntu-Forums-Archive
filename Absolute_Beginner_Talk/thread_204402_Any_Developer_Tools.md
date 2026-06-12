---
title: "Any Developer Tools?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by crazyoldman1 on 2006-06-27
This really is my first linux system and i have mainly been programming on MS (Microsoft, for all you Uber Linux people). I was wandering whats out there to program on in linux. I figure that java has to run on linux but how can i get the java compiler on Ubuntu? Also, what else is out there i am new and i have to say ive been ignorant to the world of Linux and the idea of open source for many years. I would love to write open source programms in my spare time but i really have no idea where to start with a linux OS. 

Thanks for your help and ideas guys,

Crazyoldman

---

### Post by nanotube on 2006-06-27
well, first think is to install package build-essential, that will install a bunch of dev tools like C compilers etc.
also, ubuntu comes by default with an open source java implementation, which you can use to compile java progs.

generally, open up the synaptic package manager, and search for whatever your heart desires - chances are a package or two will come up for whatever you search for. :)

---

### Post by crazyoldman1 on 2006-06-27
well i want to update my machine but my other [post]("http://www.ubuntuforums.org/showthread.php?t=203805") will explain that for some reason my system will not update. How would i compile a java file then... in terminal? 

I thank you very much for your response. 

Also, Where can i download "build-essential".

Thanks,

Crazyoldman

---

### Post by Stromham on 2006-06-27
Look for eclipse its a java IDE.

---

### Post by nanotube on 2006-06-27
[QUOTE=crazyoldman1]well i want to update my machine but my other [post]("http://www.ubuntuforums.org/showthread.php?t=203805") will explain that for some reason my system will not update. How would i compile a java file then... in terminal? 

I thank you very much for your response. 

Also, Where can i download "build-essential".

Thanks,

Crazyoldman[/QUOTE]

hi, all this stuff is in the repositories.
please check out the link in my sig about installing software on ubuntu.

---

### Post by crazyoldman1 on 2006-06-27
[QUOTE=Stromham]Look for eclipse its a java IDE.[/QUOTE]

Humm does that come with Ubuntu because i thought that was a RedHat program.

---

### Post by nanotube on 2006-06-27
[QUOTE=crazyoldman1]Humm does that come with Ubuntu because i thought that was a RedHat program.[/QUOTE]
eclipse is also in available in the repositories. :) open up synaptic package manager and search for eclipse. (might have to enable the universe/multiverse repositories, first)

---

### Post by Jagot on 2006-06-27
[QUOTE=nanotube]eclipse is also in available in the repositories. :) open up synaptic package manager and search for eclipse. (might have to enable the universe/multiverse repositories, first)[/QUOTE]

Yep - Eclipse is in the universe repo.  If you don't know how to enable it then have a look here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by az on 2006-06-27
[QUOTE=crazyoldman1]I figure that java has to run on linux but how can i get the java compiler on Ubuntu? Also, what else is out there i am new and i have to say ive been ignorant to the world of Linux and the idea of open source for many years. [/QUOTE]
There are quite a few options other than java.  Java is not (yet) a shinig example of free-libre open source.  Although Sun now say that open-sourcing Java is just a matter of time, up until a few weeks ago, it was prohibited to ship Sun's Java along with other (free-libre) implementations of java.  That meant that the Java from Sun could not be included as part of the Ubuntu repositories and installing it was a few extra steps.

Other environments include Python and Perl.  Gambas resembles Visual Basic ( I think).  There are many other options too.  Mono is an implementation of C#.

Python is an excellent example of something you can try to  get a feel for a language that is differnet than what you are used to.  Although I cannot write code for beans, I would think that is what you had in mind when you asked the question.

---


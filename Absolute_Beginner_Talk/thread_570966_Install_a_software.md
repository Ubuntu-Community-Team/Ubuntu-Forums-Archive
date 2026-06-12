---
title: "Install a software"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by anko-dw on 2007-10-08
Hi... guys!!!! Actually, I`m a new user in kubuntu and I need some help. Everytime I need to install a software (inside the terminal/konsole) there always be written like this : error, cannot execute.


How can I solve this problem???? Thank you!!!!

---

### Post by anko-dw on 2007-10-08
Why theres no one here can help me???? Hmmm it seem I`d better using my last windows xp os...

---

### Post by rsambuca on 2007-10-08
You need to be a little more specific:  What are you trying to install, what commands are you using, and what is the exact error message?

---

### Post by dhruva023 on 2007-10-08
please be specific,   

tell us what r you trying to install and ( copy and past the error massages.)

---

### Post by llamakc on 2007-10-08
> **anko-dw said:**
> Why theres no one here can help me???? Hmmm it seem I`d better using my last windows xp os...

Is the text for your problem hidden? How about share a link to your issue if you feel the absurd need to start an entirely new thread. 

For starters, relax. THIS HELP IS FREE.

---

### Post by Dr Small on 2007-10-08
What ?
What is your problem ?

This sounds like a complaining thread moreso than a question.

Dr Small

---

### Post by 1337455 10534 on 2007-10-08
jeez anko, ask a question, and then freak out.

---

### Post by llamakc on 2007-10-08
Be specific instead of starting new threads complaining about not getting help when two people have ALREADY tried to help.

We're waiting on you to give the additional information.

---

### Post by Pumalite on 2007-10-08
Where is the problem?

---

### Post by dz0004455 on 2007-10-08
weres the problem??

---

### Post by Shazaam on 2007-10-08
> **anko-dw said:**
> Why theres no one here can help me???? Hmmm it seem I`d better using my last windows xp os...

tito, is that you?:)

---

### Post by Dr Small on 2007-10-08
> **Pumalite said:**
> Where is the problem?
[http://ubuntuforums.org/search.php?searchid=28483913](http://ubuntuforums.org/search.php?searchid=28483913)

---

### Post by llamakc on 2007-10-08
[http://ubuntuforums.org/showthread.php?t=570966](http://ubuntuforums.org/showthread.php?t=570966)

Heh.

---

### Post by dz0004455 on 2007-10-08
try using the kubuntu package manager, i dont know what its called though.

---

### Post by tubasoldier on 2007-10-08
> **anko-dw said:**
> Why theres no one here can help me???? Hmmm it seem I`d better using my last windows xp os...

With a problem like that you may be right.

---

### Post by llamakc on 2007-10-08
Adept

---

### Post by llamakc on 2007-10-08
I'm gonna go ahead and make a guess that it's an MSI Windows package, or EXE.

---

### Post by anko-dw on 2007-10-08
This is when I tried to install beryl with "./configure" command......

anko-dw@anko-dw:~/Desktop/beryl-manager-0.2.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
anko-dw@anko-dw:~/Desktop/beryl-manager-0.2.0$

but it`s not only with beryl but every software I`m trying to install

---

### Post by llamakc on 2007-10-08
Heh, I was wrong. 

1. You haven't installed the necessary tools to compile software. One thing you would need would be the meta-package called 'build-essential'. IF you follow the instructions for whatever it is you're trying to manually compile you can figure out what other dependencies/needs are going to be needed.

2. Why are you trying to compile that stuff to begin with? Perhaps it's a good idea to use the package management system to install this stuff instead?

Do you know how to search for available software packages yet?

---

### Post by anko-dw on 2007-10-08
I dont....  Then what should I do...??? My home pc`s not connect internet

---

### Post by llamakc on 2007-10-08
What do you WANT to do? You realize I have no way to read your mind.

---

### Post by anko-dw on 2007-10-08
How can I install something like.... compile software
?????

---

### Post by llamakc on 2007-10-08
Better question. You can search keywords for help at [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

Here.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

PS: Beryl and Compiz-Fusion ALREADY work without compiling them but you seem headstrong on trying to figure it out. Good luck & good night.

---

### Post by anko-dw on 2007-10-08
is Build essential inside the live cd??????

---

### Post by anko-dw on 2007-10-08
Ok... thank you.... I hope it work for me.......

---

### Post by aktiwers on 2007-10-08
llamakc why are you being so harsh?

Anko:
It really be a lot easier if you could get internet on your Ubuntu PC.
Then you could follow a guide like:
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Maybe you can find a Compiz-fusion deb package.. it will install by double click

---

### Post by llamakc on 2007-10-08
> **aktiwers said:**
> llamakc why are you being so harsh?

Anko:
It really be a lot easier if you could get internet on your Ubuntu PC.
Then you could follow a guide like:
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Maybe you can find a Compiz-fusion deb package.. it will install by double click

I guess you didn't see the other post.

---

### Post by Blah3 on 2007-10-08
The configure program said no gawk but that doesn't look like a traditional missing package error that you hear about, Heres a question (ahem) "Is the software your trying to install build-able on you OS?" clap clap clap..

---


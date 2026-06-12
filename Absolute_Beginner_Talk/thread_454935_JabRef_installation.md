---
title: "JabRef installation"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2007-05-26
For those who arent aware, JabRef is a bibtex editor with a nice graphical user interface. I need it for generating and storing bibliographic information for my PhD.
It works very well and is easy to use in windows and can even be made to interface with endnote.

However, in Ubuntu, it needs to be run as a jar file all the time. This measn for me that it neds to be run from the command line with

java -jar JabRef-2.2.jar

As far as I know Jabref is not actually installed with this command and you need ti use it every time you want to run it.

I want to be able to install JabRef definitively so that I can access it from the applications menu on the desktop. How can I do this?

Cheers

---

### Post by AAM on 2007-05-26
I have used it also. I also tried to install EndNote 9 under WINE and that actually worked well. Like you I ran JabRef from the JAR file all the time. Also tried Bibus & Pybliographer. Of these JabRef was superior. Trialled Zotera also which is very useful while browsing.

None worked as well as the EndNote/MS-Word pairing for reference work - but this wasn't free or open either! It's a shame that OOo hasn't really got their process up and running yet, as tight linking of the bibliographic software  should be a killer for academia.

---

### Post by dwisianto on 2008-03-09
create a script in your ~/bin


#!/bin/bash
#
# starts jabref program 
#     
# Last Modification 
# 07-12-10 "JabRef-2.3.1.jar"
#      

jabref_lst=( "JabRef-2.2.jar" "JabRef-2.3.1.jar" )

if [ -e /home/ds/bin/${jabref_lst[1]} ]; then
    java -jar /home/ds/bin/${jabref_lst[1]} &
fi

if [ -e /home/dsm/bin/${jabref_lst[1]} ]; then
    java -jar /home/dsm/bin/${jabref_lst[1]} &
fi

---

### Post by Ryozanpaku Tiger on 2008-03-12
I have installed JabRef using Synaptic Package Manager, now it is in the Office folder in the Applications menu.

---


---
title: "Openmad installation  help"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-02-19
OK this is what I get when I try to install this game, I did a Google search for  tech_general with no luck any help would be appreciated 


joe203@joe203-desktop:~$  python '/home/joe203/openmad/openmad.py' 
Traceback (most recent call last):
  File "/home/joe203/openmad/openmad.py", line 18, in ?
    import tech_general
ImportError: No module named tech_general
joe203@joe203-desktop:~$ 


Thanks.

---

### Post by Repent on 2007-02-19
Bump.

---

### Post by Repent on 2007-02-19
Come on guys please.

---

### Post by Maestro23 on 2007-02-19
Got a link to where you d/l the program?

---

### Post by Sklasko on 2007-02-19
Have you tried cd'ing to the directory and running it as "./openmad.py"?

I don't know much about Python but adesklets used scripts with a .py extension and thats how I ran those.

---

### Post by Repent on 2007-02-19
Thes is where I downloaded it from  [http://directory.fsf.org/openMAD.html](http://directory.fsf.org/openMAD.html) and below is the read me file.

OpenMAD: Mutual Assured Destruction


* INSTALLATION

Once you have untarred the archive into a directory, you need to run the
openmad.py program using the Python interpreter.  On a UNIX system, this should
be as simple as typing at a shell:
# python openmad.pysimply
On Windows systems, the Python interpreter should already be associated with .py
files, and clicking on the openmad.py icon should run OpenMAD.

* REGISTRATION

If you sucesfully install and use this release of OpenMAD, please 'register'
the copy by letting us know.  We would simply like to receive information from
users so we have some idea of our userbase's size, and also what kind of systems
OpenMAD is being run on.  A quick email to <thenine@trinity.sa.edu.au> letting
us know where you are, what kind of machine you are running, which operating
system is installed, and any problems you may have had and overcome.  If the 
userbase of dedicated users remains small (as we expect), an online member
list may be established.  Please take the time to inform us of your use of
OpenMAD.

* CODE CONTRIBUTION

The OpenMAD project has an online CVS facility for code contribution set up.
See [http://open-mad.sourceforge.net/contrib.php](http://open-mad.sourceforge.net/contrib.php) for details

* DISCLAIMER, WARRANTY, ETC

OpenMAD is made available under the Free Software Foundation's GNU Public
License (GPL).  A copy of this license is included in the file "COPYING".
Please be aware of the licensing issues before using, modifying or distributing
the software.  This is YOUR responsibility.

---

### Post by Repent on 2007-02-19
Bump

---

### Post by Repent on 2007-02-20
OK I guess I don't need it anyway.

---

### Post by hannaman on 2007-02-20
more the '/home/joe203/openmad/openmad.py' file and see what version of python it is using.  The first line of the file should tell you.

Cd to that directory and see if the tech_general module is installed there or linked in that directory.

---


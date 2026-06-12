---
title: "Re: Installing programs not working"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by danbar on 2007-12-08
I did something in the terminal and Installing programs is NOT working.  Even my synaptic manager is NOT working. I'm copying what the PC is telling me....

UPDATE MANAGER'S MESSAGE
A unresolvable problem occurred while initializing the package information.



Please report this bug against the 'update-manager' package and include the following error message:



'E:Type '--09:02:53--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

ADD REMOVE PROGRAMS' MESSAGE: This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

SYNAPTIC MANAGER'S MESSAGE 
E: Type '--09:02:53--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

E: The list of sources could not be read.

Go to the repository dialog to correct the problem.

E: _cache->open() failed, please report.

---

### Post by taurus on 2007-12-08
There is something wrong with your /etc/apt/sources.list.d/medibuntu.list.  Edit /etc/apt/sources.list.d/medibuntu.list

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and place a # in front of all the lines.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nsilva on 2007-12-08
Are you sure you are running the command with **sudo** infront of it?

---

### Post by danbar on 2007-12-09
This is what I got when i wrote the command 
 
gksudo gedit /etc/apt/sources.list.d/medibuntu.list  ....

--09:02:53--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

    0K                                                       100%   21.16 MB/s

09:02:53 (21.16 MB/s) - `gutsy.list' saved [223/223]

Is it the right response ?  Cause normally I'm used to see something totally different in the file. 

Shall I put # now in front of each line ?

Thanks for your help!

---


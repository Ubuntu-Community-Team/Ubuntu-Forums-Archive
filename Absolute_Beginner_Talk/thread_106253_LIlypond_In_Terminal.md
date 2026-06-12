---
title: "LIlypond In Terminal"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-20
Oh God,


Please help me. Whenever i try to install anything it tries to install lillypond and it says:

E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1

The thing is that i want to install Lilypond but i can't get it to work.


Please Help Me.

---

### Post by bscbrit on 2005-12-20
How are you trying to install it - with synaptic?  With dpkg?  What command are you using?  What is drive E:/ - that is a windows annotation and nothing to do with linux?

---

### Post by Dr Von Bon Bon on 2005-12-20
I'm trying to install is using synaptic and I have no idea what the E:/ is as synaptic is doing the installing.

When i tried it again and looked in terminal it said the same thing with the errors but without the E:/ thingy.

Any idea what's up?

---

### Post by bscbrit on 2005-12-20
To be honest, no I don't know what is going on either.  

My suggestion would be to delete the offending file and then try to download and install again using synaptic.  The error messages (I think!) suggest that either the package is corrupted or it has the wrong permissions.  I cannot imagine how synaptic could have done this but re-downloading might solve the problem.  If you get the same or a similar error then we can try installing it using dpkg.  This will probably work but it means the package is not specifically tailored for Ubuntu - it might work perfectly but there might also be problems.

So my suggestion is

sudo rm -f  /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb

on the command line. Start synaptic and reload. Search for your program, mark it and reinstall.

---

### Post by Dr Von Bon Bon on 2005-12-20
I just tried doing that and it didn't recognise the command 

rm -f 

or

rm-f

---

### Post by bscbrit on 2005-12-20
did you prefix the command with sudo?

EDIT:  What was the full error message please?

---

### Post by Dr Von Bon Bon on 2005-12-20
Yeah, i typed:

sudo rm -f /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb

and it said:

sudo: rm -f: command not found

EDIT:

When i try and remove all the data through a complete uninstallation in synaptic it comes up with these errors:

E: lilypond-data: Package is in a very bad inconsistent state - you should

(It does just cut off after the should)

and then


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


What's going on please?

---

### Post by bscbrit on 2005-12-20
Ok. please type 

sudo

on its own and let me know what the response is please.

---

### Post by Dr Von Bon Bon on 2005-12-20
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
                    { -e file [...] | -i | -s | <command> }

---

### Post by Dr Von Bon Bon on 2005-12-22
I managed to remove the package but now when I try and uninstall LIlypond it says that it's in a inconsistent state and i should reinstall it.
At this point it also says that I need to go 

dpkg --configure -a 

Which I then do and reinstall Lilypond and my problems start all over again.

Please help

---

### Post by dragonfyre13 on 2006-02-06
[http://ubuntuforums.org/showthread.php?p=680286#post680286](http://ubuntuforums.org/showthread.php?p=680286#post680286)

I fixed it. you should be able to follow it pretty well.

---

### Post by unfear on 2006-02-07
I remove the deb pakage of lilypond-data and this not solve, the next intall from Synaptic or terminal goes reload de package lilypond-data, I trying all solution from here and have nothing effect

---


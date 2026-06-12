---
title: "Bin files"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2007-05-17
I just downloaded google eart for linux.
It's downloaded as  bin file.
I;ve tried double clicking on it, but I get the error msg "could not open the file, make sure your not runing a bin file".
So far (not) so good.
I just don;t know how to work with bin files and looking around hasn't given me any answers so far.
Anybody got a manual or a website to direct me to?

---

### Post by heimo on 2007-05-17
Try this:
[http://ubuntuforums.org/showpost.php?p=2618301&postcount=2](http://ubuntuforums.org/showpost.php?p=2618301&postcount=2)

---

### Post by ajmorris on 2007-05-17
> **quinnten83 said:**
> I just downloaded google eart for linux.
It's downloaded as  bin file.
I;ve tried double clicking on it, but I get the error msg "could not open the file, make sure your not runing a bin file".
So far (not) so good.
I just don;t know how to work with bin files and looking around hasn't given me any answers so far.
Anybody got a manual or a website to direct me to?

we will have to use the CLI. Go to Start Ment >> Accessories >> Terminal.

navigate to the directory: 
```
cd 'directory'

Note 'ls' shows the folders in the folder you are browsing
```

find the bin file, then : 
```
sudo chmod a+x
``` to make it executable

then :
 ```
sudo ./'your.bin'
```

Hope you can follow that :)

---

### Post by overdrank on 2007-05-17
> **quinnten83 said:**
> I just downloaded google eart for linux.
It's downloaded as  bin file.
I;ve tried double clicking on it, but I get the error msg "could not open the file, make sure your not runing a bin file".
So far (not) so good.
I just don;t know how to work with bin files and looking around hasn't given me any answers so far.
Anybody got a manual or a website to direct me to?

Hi this link may help you out 
[http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually](http://cutlersoftware.com/ubuntuinstall/#installing_a_package_manually)
Good luck !

---

### Post by ironfistchamp on 2007-05-17
On a side note you can install Google Earth via Automatix. You can get automatix from [www.getautomatix.com/](www.getautomatix.com/)

HTH

Ironfistchamp

EDIT: Gah repeatedly beaten to it :p

---

### Post by quinnten83 on 2007-05-17
tnx for the quick replies, 
I finally found the answer in this link that i got somewhere on the forum

[http://earth.google.com/support/bin/answer.py?answer=44713&ctx=sibling]("http://earth.google.com/support/bin/answer.py?answer=44713&ctx=sibling")

could it be my drivers for the videocard? I have a ATI radeon.
and of course the question still stands, where can i find the best information on working with bin.

---

### Post by Terl on 2007-05-17
> **quinnten83 said:**
> tnx for the quick replies, 
I finally found the answer in this link that i got somewhere on the forum

[http://earth.google.com/support/bin/answer.py?answer=44713&ctx=sibling]("http://earth.google.com/support/bin/answer.py?answer=44713&ctx=sibling")

could it be my drivers for the videocard? I have a ATI radeon.
and of course the question still stands, where can i find the best information on working with bin.

The best information for working with bin files is usually the read-me that came with the files or the main site where you got the program.  Sometimes they have some special guidance or commands they want you to follow.  Most of the basics have been covered in this thread.  Also search out some basic linux command tutorials.

Here is a most excellent resource:  [Linux Documentation Project]("http://tldp.org/guides.html")

---

### Post by Tomosaur on 2007-05-17
> **ajmorris said:**
> we will have to use the CLI. Go to Start Ment >> Accessories >> Terminal.

navigate to the directory: 
```
cd 'directory'

Note 'ls' shows the folders in the folder you are browsing
```

find the bin file, then : 
```
sudo chmod a+x
``` to make it executable

then :
 ```
sudo ./'your.bin'
```

Hope you can follow that :)

Just a quick note - if the file is in some subdirectory of your home directory (eg, your desktop) then you do NOT need to use sudo to change the permissions of the file.

You can also change file permissions by right clicking them, clicking properties, and then selecting the 'permissions' tab.

---

### Post by quinnten83 on 2007-06-03
Thanks for your replies guys...

---


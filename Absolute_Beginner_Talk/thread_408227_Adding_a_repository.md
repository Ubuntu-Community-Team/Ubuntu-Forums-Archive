---
title: "Adding a repository"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-13
I'm understanding what repositories are but not certain how to add them. I'm mainly interested in installing ntfs-g3 to Ubuntu 6.06. One link said: 

First you will need to add one of the following [WWW] repositories:

For Ubuntu 6.06 LTS (a.k.a. Dapper Drake):

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all 

deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all 

deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all 


Would going to System/Administration/Software Properties do the same thing? If not how would I do this using the command line? Thanks.

---

### Post by justleen on 2007-04-13
the list of repositories are located in /etc/apt/sources.list

you can edit them by typing this in a terminal ```
 sudo gedit /etc/apt/sources.list 
```
make a backup before you add anything though
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.org 
```

edit: in System/Administration/Software  you cant add any repositories, you can only select the default ones : security/universe/multiverse.

---

### Post by nsleiman on 2007-04-13
from the konsole/terminal  type:

sudo nano /etc/apt/sources.list

and add the lines there.

after that do: sudo apt-get update

et voila :)

---

### Post by nudnik on 2007-04-13
> **jacatone said:**
> I'm understanding what repositories are but not certain how to add them. I'm mainly interested in installing ntfs-g3 to Ubuntu 6.06. One link said: 

First you will need to add one of the following [WWW] repositories:

For Ubuntu 6.06 LTS (a.k.a. Dapper Drake):

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all 

deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all 

deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all 


Would going to System/Administration/Software Properties do the same thing? If not how would I do this using the command line? Thanks.

Those look like custom repositories, so you will have to manually edit your sources list thusly:

sudo -s
(password)

sudo gedit /etc/apt/sources.list

Add the repositories you wish, save and close.

then:

sudo apt-get update

---


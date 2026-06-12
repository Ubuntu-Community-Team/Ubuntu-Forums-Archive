---
title: "where is local repository ?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by m.h.shams on 2006-07-02
dear friends,

im new in ubuntu, and i don't know where is my local repository in ubuntu and
how can i add a package in this repository and update packages.gz file.


please help me to find my answers.


regards.
shams

---

### Post by nickpaton on 2006-07-02
Hi Shams and welcome to Ubuntu!

Have a look at this post for a couple of good repository lists and how to install etc:

[http://http://www.ubuntuforums.org/showthread.php?p=1205944#post1205944]("http://http://www.ubuntuforums.org/showthread.php?p=1205944#post1205944")

Also to get you going, have a look at the Psychocats website which as well as having an excellent repositories list also has a number of great HowTo's including a repositories update:

[http://http://www.psychocats.net/ubuntu/sources]("http://http://www.psychocats.net/ubuntu/sources")

Adding a package is simply a question of having a look at the examples, especially the first one which is very comprehensive, and you should get the idea.

This should also help you specifically with the packages.gz file you want to update - if not someone less noob than me will help!

Good luck and enjoy!

(spellings)

---

### Post by darkenedday on 2006-07-02
for the local repositories simply use Synaptic(system > administration >syaptic) and select what files you want, there are also MANY posts on this forums as to how to add more sources, and there is a wiki, you can also use the terminal if you know the name of the package you want, simply type "sudo apt-get install package-name"


to install from a .gz file (provided its a tar.gz file) the code is 

1.) navigate to the directory cd "directory-name"
3.) tar xzvf "file-name-here"

this should give you a list of the files within it, reading the README or the INSTALL or HELP files within the newly unpacked directory may help but most of the time the code to install is either navigate to new directoy (cd "directory") ./configure or ./install

to install from a debian package
1.)navigate to the directory via cd
3.) sudo dpkg -i "package-name-here"

---


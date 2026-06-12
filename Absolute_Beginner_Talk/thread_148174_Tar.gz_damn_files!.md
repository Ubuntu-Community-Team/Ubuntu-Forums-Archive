---
title: "Tar.gz damn files!"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Arrhenius on 2006-03-21
Could someone explain hoe to install a program that is downloaded with this extension, i.e, tar.gz ?

---

### Post by KingBahamut on 2006-03-21
Source installation. This can be a little tricky. 

what are you installing?

---

### Post by klahjn on 2006-03-21
[QUOTE=Arrhenius]Could someone explain hoe to install a program that is downloaded with this extension, i.e, tar.gz ?[/QUOTE]

99% of the time that i get a .tar.gz file what i do is right click on the file and click "Extract Here" then a folder comes up with the name of the package.  At that point i drop down to a terminal, and go into that folder and type:
./configure
If that does not produce an error, then i would type 
sudo make
followed by:
sudo make install
that should install the package for you, hope it helps.

---

### Post by KingBahamut on 2006-03-21
Klahjn, but in this case it could be something as easy as an existing rpm, or something that lives out on the repositories. 

Arrhenius, did you search the Repositories via Synaptic to see if the package your trying to install is out there?

---

### Post by Arrhenius on 2006-03-21
No, I don't have the package in the Repositiories.

klahjn, I followed your suggestion but I came across this:

pedro@ubuntu:~/Desktop/gchempaint-0.7.1$ ./configure
./configure: line 1221: config.log: Permission denied

What is the problem?

---

### Post by Adrian on 2006-03-21
You will probably find this guide useful:
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by klahjn on 2006-03-21
[QUOTE=Arrhenius]No, I don't have the package in the Repositiories.

klahjn, I followed your suggestion but I came across this:

pedro@ubuntu:~/Desktop/gchempaint-0.7.1$ ./configure
./configure: line 1221: config.log: Permission denied

What is the problem?[/QUOTE]

"permission denied".  sudo ./configure
hopefully that works for you.

Just got another piece of information for you.  Was recommend to me that you also try the following command on the folder before you try the ./configure again.
sudo chmod 777 (name of folder)

that would allow the files to be edited.

---

### Post by KansasJoe on 2006-03-21
You shouldn't have to be root to configure a package because this may cause probs with permissions later down the road....may think of changing permissions on extracted folder of program....chown username:username folder....typical steps

./configure
make
sudo make install
make clean

if you haven't already you will need to get build beforehand

sudo apt-get install build-essential

---

### Post by mlind on 2006-03-21
even better is to use ./configure --prefix=$HOME and not doing that sudo
stuff at all. This way you'll install software locally and wont't break anything
if you misconfigure somehow. Removing applications is also easier if configure
script doesn't implement 'clean' rule.

---


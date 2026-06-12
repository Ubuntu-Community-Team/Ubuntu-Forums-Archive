---
title: "need help installing something thats not in repos"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by at0mic on 2006-11-13
HI!,

wondering if you could tell me the steps needed to install b5i2iso... not sure where to begin other than extract the tar :)

[http://freshmeat.net/projects/b5i2iso/](http://freshmeat.net/projects/b5i2iso/)

---

### Post by dbbolton on 2006-11-13
maybe you need to sudo mv the directory to the apps folder

---

### Post by b_martinez on 2006-11-13
> **at0mic said:**
> HI!,

wondering if you could tell me the steps needed to install b5i2iso... not sure where to begin other than extract the tar :)

[http://freshmeat.net/projects/b5i2iso/](http://freshmeat.net/projects/b5i2iso/)

Which kind of tar file is it? gz or bz
Been a while since I installed a .tar file.
The lines with a # in front are terminal commands
open a terminal then 

#sudo tar -xvzf /(path to file)       <--- for gz files

OR 

#sudo tar -xvjf /(path to file)        <----- for bz files


this is what the command would look like if it's been downloaded to your /home 

#sudo tar -xvzf /home/(your name here)/b5i2iso.tar.gz

#sudo cd /home/(your name here)/b5i2iso.tar

#sudo ./config && make && make install

the above 3 commands are for .gz files.

As I wrote, it's been a while, so if someone else writes a different set of commands, you'll likely do right to follow their advice
hth
Bill

---

### Post by gnama on 2006-11-13
You could download a package manager from an existing repository.

---

### Post by CatKiller on 2006-11-13
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

This is pretty similar to the instructions b_martinez has given you, but with pictures.

Don't forget to install the **build-essential** package, and don't forget to read the instructions on the site and in the download.

---

### Post by at0mic on 2006-11-14
thanks for the advice guys. they all worked to some extent but get caught up in the make process due to an error. any ideas?

at0m@buntu:~/b5i2iso-0.2-src$ dir
CHANGELOG  description-pak  doc-pak  gpl.txt  Makefile  Makefile.win  src
at0m@buntu:~/b5i2iso-0.2-src$ sudo make install
make: *** No rule to make target `install'.  Stop.

---

### Post by Sef on 2006-11-14
Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install build-essential

To compile, you need build-essential


Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu

---

### Post by at0mic on 2006-11-14
i read that one in the nice website from cat killer. build-essential is and was listed as installed.

---

### Post by CatKiller on 2006-11-14
schrombot's answer is better than mine anyway

---

### Post by schrombot on 2006-11-14
So long as you have build-essential installed, this should do the trick for compiling..```
sudo ./configure
sudo make
sudo make install
```
Just do it in that order and you will be good to go. Sometimes compiling can take a long time so don't get worried if it seems like the computer is hung up, just kick back and get a drink.

Well I guess this package is built differently from the norm, so ignore everything I said I guess.

Ok, another edit. I ran make on the tarball and it makes a file called b5i2iso and that is the executable for the program. So just run make in the directory and then run "sudo mv b5i2iso /usr/bin" and you will be able to run it from the command prompt.

---

### Post by at0mic on 2006-11-15
thanks alot guys. especially schrombot :))))

---


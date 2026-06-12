---
title: "A Little Help Please"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by tazmanmn on 2008-03-17
Heys guys this might sound kinda funny but I am still learning my Terminal commands and am having trouble trying to get a game installed for my son. The game is called Construo I have been using linux for almost 6 months now and really like it just takes awhile to learn it  all when you have to deal with window crap at work every day lol. Thanks alot.
Dereck

---

### Post by wolfen69 on 2008-03-17
how to install anything in ubuntu [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by weezy8802 on 2008-03-17
hope this helps 

[http://www.freshports.org/games/construo/]("http://www.freshports.org/games/construo/")

---

### Post by tazmanmn on 2008-03-17
Well it isn't in synaptic...and the other website got me even more lost...I think I am going to just tell him to stick with his windows computer for now...

---

### Post by Nythain on 2008-03-17
seems easy enough if you have a source.tar.gz... i would recommend
first, install build-essential
sudo apt-get install build-essential
that will get you to tools needed to compile something from source

it doesnt look like the program has any special dependancies, so...
next, extract the tar.gz to somewhere... probably /home/user/... i would spit out a command line for this, but i use ark :(

and then, cd into the extracted directory
cd /path/to/where/you/extracted

next, look for a README file... usually contains instructions... following the freshports site as best i could, it looks like a simple
./configure
make
make install
might just do the trick, not even sure if it needs the ./configure on this one... worth a shot though... if you get any errors during make install, try sudo make install

hope that helps a bit

---

### Post by coolbrook on 2008-03-17
Seems pretty straight forward.

[http://www.nongnu.org/construo/](http://www.nongnu.org/construo/)

I downloaded the .gz to my home folder and double clicked on it.  I extracted the Construo folder (construo-0.2.2) to my home folder.  Opened the folder and went to the README.  The README says to look at the file INSTALL.

In terminal you have to navigate to the Construo folder you created

```
cd ~/construo-0.2.2
```

and run the commands listed in the INSTALL file.

```
,/configure
make
make install
```

---


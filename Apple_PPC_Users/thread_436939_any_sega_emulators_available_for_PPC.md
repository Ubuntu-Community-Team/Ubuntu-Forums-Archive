---
title: "any sega emulators available for PPC?"
date: 2007-05-08
forum: Apple PPC Users
---

### Post by zoexii on 2007-05-08
I was feeling like playing some sega genesis the other day, but was super disappointed to find that Generator, Gens, and Dgen cannot be found in the repositories.  

I tried downloading sourcecode and compiling, but I really don't know much about it.  Anyway doing 
./configure
make
sudo make install

failed for all three during 'make'.  I'm pretty sure I had all the required dependencies installed, but as I was unable to find any ppc specific howtos I can't be to sure.

Has anyone else made any of the genesis emulators work?  if so could you point me in the right direction?

---

### Post by indica on 2007-05-09
bump!
i'm curious too

---

### Post by stmiller on 2007-05-09
[http://packages.ubuntu.com/feisty/otherosfs/dgen](http://packages.ubuntu.com/feisty/otherosfs/dgen)

sudo apt-get install dgen

Are you running feisty? If not you can just download the .deb from the above link.

I don't now anything about this program, but just ran across the name recently.

---

### Post by zoexii on 2007-05-10
hello, thanks for the reply.

I'm running dapper,
(I originally tried to install feisty, but the installer failed halfway through.  Then I tried edgy, same deal.  Dapper installed without problems, but haven't tried a dist-upgrade for fear that it might break the system.)

anyway, I tried to install the .deb for dgen, but my version of libc6 isn't compatible and can't be upgraded.

btw, is it possible to maybe reformat my os9 hsf partition to ext3, copy my root directory, edit yaboot, and have two working installs so that I can safely try dist-upgrade?

also, do ram requirements increase between dapper and feisty?

thanks,
zoe

---

### Post by stmiller on 2007-05-10
Hey alternatively, you can look for an older package of dgen. That may work with your older libraries.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=dgen](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=dgen)

Btw, can't you just 

sudo apt-get install dgen 

???

Even with Dapper that should work. What is your /etc/apt/sources.lst ?

---

### Post by Biz_reporter on 2007-07-02
Just curious, what consoles do have Linux PPC emus?

---

### Post by rye_ on 2007-07-08
hi,

remember that [http://www.getdeb.net/](http://www.getdeb.net/) is a good place to look for apps either not in the repositories or that gets updated regularly.

you'll find a megadrive/genesis emu called gens.  also zsnes is a very good snes emulator.

ryan

---


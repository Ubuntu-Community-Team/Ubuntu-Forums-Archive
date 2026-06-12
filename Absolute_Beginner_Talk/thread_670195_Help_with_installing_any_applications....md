---
title: "Help with installing any applications..."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Zackie on 2008-01-17
Hey guys... Sorry bout the post.. but... I'm extremely new to Ubuntu. I installed everything find... connected to the internet... updated all i could.. and am set... One thing...What is the process to installing anything? Or are there different ways to install things... I have downloaded Pedgin 2.3.1 and get all the way to the "make" part or the "gmake" or the "sudo make" I don't know exactly what i'm doing any way but i get an error:


zackie@zackie:~/pidgin-2.3.1$ make
make: *** No targets specified and no makefile found.  Stop.
zackie@zackie:~/pidgin-2.3.1$ gmake
bash: gmake: command not found
zackie@zackie:~/pidgin-2.3.1$ sudomake
bash: sudomake: command not found
zackie@zackie:~/pidgin-2.3.1$ sudo make
make: *** No targets specified and no makefile found.  Stop.
zackie@zackie:~/pidgin-2.3.1$ 
         Can't seem to get past this part.... what am i doing wrong?

Thanks in advance!

---

### Post by philinux on 2008-01-17
Pidgin is already installed as a default app under Apps>Internet.

Its version 2.2.1

---

### Post by mcduck on 2008-01-17
Most of the time you don't need to download anything from the net yourself. Just use Ubuntu's package manager and it will download & install everything automatically.

Check out both Add/Remove (in Applications-menu) and Synaptic (in System/Adminstration).

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by philinux on 2008-01-17
Just bear in mind that some apps are not listed under add/remove but will be listed in synaptic.

Also if you haven't done so already click the medibuntu link below and follow the instruction there.

---

### Post by Joeb454 on 2008-01-17
Also, to avoid the compiling ( ./configure | make install etc.) try [http://www.getdeb.net/]("http://www.getdeb.net/") you just download and double click :)

Synaptic and Add/Remove are also very good as you just choose what you want and click ok :)

---

### Post by Zackie on 2008-01-17
Rock on guys thanks... Fast too :)

---

### Post by Zackie on 2008-01-17
still running into this problem of finding other software that i want to use but can't install... I installed wine... not i'm trying to get IEs 4 but said i need a cabextract thing first... so i extracted the package went to the terminal typed the cd (what ever that is) and then the directory ./configure worked this time.. but when i do "make" nothing happends.... since the files are in the directory... how to i apply them to my machine?


thanks... 


Zackie...

---

### Post by Linuxratty on 2008-01-17
The "search" function in synaptic is your friend.

---

### Post by Zackie on 2008-01-17
okay sweet didn't even know i could do it like that.. that worked got them both installed and running... Codecs.. I'm having problems getting decent codecs to play videos such as the ones on youtube/myspace/anything else that streams... is there a good package or site i can go for ... for these? sorry i'm only 8 hours old coming to ubuntu and i installed it with out letting my self know.... long story... heh... anywayz



thanks


Zackie...

---

### Post by hyper_ch on 2008-01-17
well, add medibuntu repos:

Howto at [http://www.medibuntu.org](http://www.medibuntu.org)

and then run:

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2

```

That should install most codecs as well as the library to "decss" dvds.

---

### Post by Zackie on 2008-01-17
rock on thanks guys! Figured mostof the codec thangy out heh..

---


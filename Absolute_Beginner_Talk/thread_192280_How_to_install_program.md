---
title: "How to install program?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by notwist on 2006-06-08
So far I've only installed via the packet handler, which worked fine. Now I'd like to install a DC hub, this one more exactly:

[http://opendchub.sourceforge.net/](http://opendchub.sourceforge.net/)

I've got the tar.gz file, but what now? I've tried running "make install" in the prompt when in the directory but apparently there's no command like that. What should I do? :confused:

---

### Post by Jagot on 2006-06-08
Make sure you've followed everything here:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Especially installing build-essential.

---

### Post by meng on 2006-06-08
Ok first you need to have build-essential installed:
sudo apt-get build-install {whoops this is wrong}
(you only need to do this once no matter how many programs you install in future)

Then you need to unpack the archive
tar zxvf <whatever the name of the tar.gz>

Then change into that directory
cd <whatever the name of the new folder>

And three more steps:
./configure
make
sudo make install

(The last three steps are where the real chaos begins. In my limited experience of compiling from source, something goes off the rails at this point. If so, then by all means post the output and ask someone clever for help.)

EDIT:
typo:
sudo apt-get install build-essential

---

### Post by philipgm on 2006-06-08
make install needs to be run using sudo

sudo make install

it will ask for your password.

Phil

EDIT: OK there's other stuff to do too!

---

### Post by aysiu on 2006-06-08
Any reason you don't want to just [enable the Universe repositories](http://www.psychocats.net/ubuntu/sources) and then paste these two commands into the terminal? ```
sudo aptitude update
sudo aptitude install opendchub
```

---

### Post by notwist on 2006-06-08
I managed to get the essential package, but now I get this

make: Nothing to be done for `INSTALL'.

lowercase gives me

make: *** No rule to make target `install'.  Stop.

hm?

---

### Post by meng on 2006-06-08
So just clarify for me:
Did you extract files from the archive?
Did you configure? (sometimes this is unnecessary)

---

### Post by aysiu on 2006-06-08
Is there any reason you're installing from source instead of using the package manager?

Is there a special feature in 0.7.15 that's not in 0.7.14?

Are you just trying to learn how to compile from source out of curiosity?

---

### Post by notwist on 2006-06-08
[QUOTE=meng]So just clarify for me:
Did you extract files from the archive?
Did you configure? (sometimes this is unnecessary)[/QUOTE]

Yeah im running the commands from inside the extracted folder.

Anyway it works now, I forgot to run ./configure. Thanks!

---

### Post by yy1124 on 2006-06-19
Hi guys,
regrading to the installations...

I downloaded Avast Linux Home Edition in a tar.gz format, i follow the steps in its "INSTALL" and README file and eventually it appeared in the menu.

The thing is initially I unpacked it on desktop, but I dun wan it to be there so I removed it, and now the AVast shortcut in the menu won't work anymore. (I never try earlier, only discovered it is there after i deleted the directory)

Questions is the folder still have to be there even after I install it?
And is there any other directory that acts like Program Files and can be shared by any user? (I mean out of the box directory)

I understand that /usr might act as that, but it has limited access (and if posible i dun wanna change that) and there are plenty of directories inside where I am not sure which one to put into)

thx

---


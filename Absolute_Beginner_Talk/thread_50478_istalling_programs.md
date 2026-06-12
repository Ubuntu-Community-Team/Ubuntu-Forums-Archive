---
title: "istalling programs"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-07-20
how do i install programs???
i have download programs and i dont know how to install them.

---

### Post by jasonpeinko on 2005-07-20
i have cine paint 
lives 
nvu
to install 
they are in gz and bz2 format. 
how do i do it?
thx for the help.

---

### Post by rmjokers on 2005-07-20
In general, if you have a .tar.gz or .tgz file, you want to decompress/untar the file and then look at the README/INSTALL directions in the directory that is created.  You can do this from the command line as follows:

cd (directory where .tgz file is)
tar xvzf ?
where ? is the filename

Usually, there are steps such as running confingure

./configure

Running make to build the software

make

And running make install to install the software

sudo make install

Whenever possible, it is better to use the ubuntu software repositories to install software.  The cine paint software you mentioned can be installed this way.  Start up synaptic

sudo synaptic

And make sure you have the Universe repository enabled.  Then, you can search for cine and the application should appear.

---

### Post by rmjokers on 2005-07-20
Note:

If you have a .bz2 file rather than a .gz file, you can use tar xvjf rather than xvzf to untar/decompress it.

---

### Post by jasonpeinko on 2005-07-20
ok i tryed that but it did not work. 
i have the packages in a folder should i take them out?

---

### Post by Phixion on 2005-07-20
[QUOTE=jasonpeinko]ok i tryed that but it did not work. 
i have the packages in a folder should i take them out?[/QUOTE]

always try 'sudo apt-get install <program name>' before downloading / installing yourself.

---

### Post by jasonpeinko on 2005-07-20
[QUOTE=Phixion]always try 'sudo apt-get install <program name>' before downloading / installing yourself.[/QUOTE]
 i tyed it  and it said syntax error 'newline'

here is what i typed in the terminal.

sudo apt-get install <gbuilder>

---

### Post by Phixion on 2005-07-20
[QUOTE=jasonpeinko]i tyed it  and it said syntax error 'newline'

here is what i typed in the terminal.

sudo apt-get install <gbuilder>[/QUOTE]

without the < > :P

---

### Post by jasonpeinko on 2005-07-20
k thx im a newb
but now it says password.
i put in both my password and the admin pass word nothing works

---

### Post by jasonpeinko on 2005-07-20
i did not find it

how do i install it manually and where can i find programs i installed in synaptic?

---

### Post by jasonpeinko on 2005-07-20
when i do the instructions the software tells me 2 do then i get an error no file in directory. where do i put the package?

---

### Post by jasonpeinko on 2005-07-20
[QUOTE=rmjokers]In general, if you have a .tar.gz or .tgz file, you want to decompress/untar the file and then look at the README/INSTALL directions in the directory that is created.  You can do this from the command line as follows:

cd (directory where .tgz file is)
tar xvzf ?
where ? is the filename

Usually, there are steps such as running confingure

./configure

Running make to build the software

make

And running make install to install the software

sudo make install

Whenever possible, it is better to use the ubuntu software repositories to install software.  The cine paint software you mentioned can be installed this way.  Start up synaptic

sudo synaptic

And make sure you have the Universe repository enabled.  Then, you can search for cine and the application should appear.[/QUOTE]
 sry bout all the questions but in your post could you give me an example.
say i wanted to run Lives
the file is on the desktop and its name is LiVES-0.9.5-pre3.tar.bz2
what would i type?

o yea and how do i enable universe repository

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=jasonpeinko]
o yea and how do i enable universe repository[/QUOTE]

I can't help you with compiling things, I avoid that like the plague. If you want synaptic to be full featured, do this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

and let synaptic reload itself.

---

### Post by poofyhairguy on 2005-07-20
Look at this howto:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

Thats how you install programs in Ubuntu. The compiling from source is when its not in synaptic after doing what the guide says. I usually just don't use the program then...compiling from source sucks...

---

### Post by rmjokers on 2005-07-21
In order to extract LiVES, you could do as follows:

Open a terminal

cd Desktop

tar xvjf LiVES-0.9.5-pre3.tar.bz2

You should now have a directory called LiVES-0.9.5 or something similiar.  Go into the directory

cd LiVES-0.9.5

and look for a file named README or INSTALL.  There should be instructions in there on how to proceed with install.

In order to add universe to repository, go to Settings->Repository->Add and make sure all the components are checked.

[QUOTE=jasonpeinko]sry bout all the questions but in your post could you give me an example.
say i wanted to run Lives
the file is on the desktop and its name is LiVES-0.9.5-pre3.tar.bz2
what would i type?

o yea and how do i enable universe repository[/QUOTE]

---


---
title: "Trying to install .tar files from gnomefiles.org"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by JGMN on 2006-05-06
I've basically looked at different tutorials and nothing has really helped me.
I know that I can't use the synaptic package manager. I've tried following the indications for the terminal installing process but I can't get it to work either.

 after I extract to the desktop

this is to the point I get to

juan@FRED:~$ cd /home/juan/Desktop/pymp
juan@FRED:~/Desktop/pymp$ ./configure
bash: ./configure: No such file or directory
juan@FRED:~/Desktop/pymp$ make
bash: make: command not found
juan@FRED:~/Desktop/pymp$ sudo make install
sudo: make: command not found
juan@FRED:~/Desktop/pymp$


this is just following tutorials on the net. I've tried another method where I get 
to a point where it asks my password, I'm not sure if I was trying to install this same one but even then it does nothing after I put my password and follow to the next steps. 

I'm about to give up. This is pretty confusing for an end user.

I've tried to install like 3 .tar files. none of them work

---

### Post by linear on 2006-05-06
Read this: [CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware").

Then start by installing the **build-essential** package.

---

### Post by Sef on 2006-05-06
To compile (build from source), you need to download build-essential.

Open the Terminal

then type

sudo apt-get update

sudo apt-get install build-essential

---

### Post by JGMN on 2006-05-06
thanks 

this is what I got 

Setting up build-essential (11.1) ...
juan@FRED:~$ cd /home/juan/Desktop/pymp
juan@FRED:~/Desktop/pymp$ ./configure
bash: ./configure: No such file or directory
juan@FRED:~/Desktop/pymp$ ./configure
bash: ./configure: No such file or directory
juan@FRED:~/Desktop/pymp$ cd /home/juan/Desktop/pymp
juan@FRED:~/Desktop/pymp$ make
`which python` ./build.py; rm -f ./build.pyc
Listing . ...
Compiling ./build.py ...
Compiling ./control.py ...
Compiling ./menu.py ...
Compiling ./mplayer.py ...
Compiling ./playlist.py ...
Compiling ./prefs.py ...
Compiling ./pymp.py ...
Compiling ./remote.py ...
juan@FRED:~/Desktop/pymp$ sudo make install
`which python` ./build.py; rm -f ./build.pyc
Listing . ...
Compiling ./build.py ...
install -d //usr/local/lib/pymp
install *.pyc //usr/local/lib/pymp
install -d //usr/local/share/pixmaps
install -m 644 pymp.png //usr/local/share/pixmaps
install -d //usr/local/bin
install pymp //usr/local/bin
sed -i "s|PREFIX|/usr/local|g" \
        //usr/local/bin/pymp
juan@FRED:~/Desktop/pymp$ sudo make install
`which python` ./build.py; rm -f ./build.pyc
Listing . ...
Compiling ./build.py ...
install -d //usr/local/lib/pymp
install *.pyc //usr/local/lib/pymp
install -d //usr/local/share/pixmaps
install -m 644 pymp.png //usr/local/share/pixmaps
install -d //usr/local/bin
install pymp //usr/local/bin
sed -i "s|PREFIX|/usr/local|g" \
        //usr/local/bin/pymp
juan@FRED:~/Desktop/pymp$
juan@FRED:~/Desktop/pymp$

---

### Post by Qrk on 2006-05-07
pymp is written in python, not C. Gcc won't work.

Fnd the program that installs the software.  If they were nice, they might even have named it make_something, or at least similar. You can display it in gedit if your not sure what it is. Thats what makes python great... you can read it. 

You should only need to run that program, (give it executable permissions) and the software should install to the current directory.

Then you can run pymp.py to start the program.

---


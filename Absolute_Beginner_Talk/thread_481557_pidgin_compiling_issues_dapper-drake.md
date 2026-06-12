---
title: "pidgin compiling issues dapper-drake"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by computerjunkie on 2007-06-22
I installed the build essential package through synaptic and the instructions clearly state to install pidgin: 

". `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation."

./configure worked liek always, but when I typed make, terminal responded with :

name@dragonfire:~/downloads/pidgin-2.0.2$ sudo make
make: *** No targets specified and no makefile found.  Stop.
name@dragonfire:~/downloads/pidgin-2.0.2$ make
make: *** No targets specified and no makefile found.  Stop.

why is this happening, there ARE makefiles in the directory...

---

### Post by ethanubutnumaker on 2007-06-22
I had that same problem in Feisty. i havent figured it out yet either. is there a component we are missing?

---

### Post by computerjunkie on 2007-06-22
HAHA FOUND OUT WHY!!!! 

sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev

ok then go to synaptic package manager and install libxml-parser-perl (it will install a grand total of around 17 packages, but they are small and quick,no worries ^__^)

cd into the directory that contains the pidgin source (2.0.2)

./configure
make
sudo make install

in terminal type pidgin and it will run

---


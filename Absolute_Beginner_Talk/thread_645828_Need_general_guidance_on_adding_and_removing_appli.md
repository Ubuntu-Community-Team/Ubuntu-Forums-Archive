---
title: "Need general guidance on adding and removing applications"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2007-12-20
Ok i am starting to get the hang of this

the Add/Remove option and the Synaptic Package** (should i ever remove anything permanently??????????)** are easy enough to deal with

now starting to play with the command lines

Could someone offer guidance on the procedure for installing and removing programs you download from web sites?

So you download it and it ends up on the desktop...

You then extract it (so far ive seen Xubuntu use archive manager) -**are there not installer programs i can use?**

You then go to the terminal and find the executable file and type what??? I've seen some say **exec** or **.** followed by the file name, both do the same thing i assume

this hopefully installs the product... if not it is beyond my understanding at this point

after installation you can then **rm -r** the dir and **rm** the downloaded files

**now if you dont like the new application how do you go abouts removing it from your system?**... for example i have a failed installation of ristretto.. how do i get rid of whatever files got installed somewhere

Do i have the right idea about this?
appreciate anyone who can make life a bit easier

---

### Post by mmb1 on 2007-12-20
You want to uninstall from terminal, or synaptic?

---

### Post by thelatinist on 2007-12-20
Are you asking how to build from source?

If so, assuming you've downloaded a .tar.gz archive to your desktop (modify as necessary).

```
sudo mkdir ~/src/program_name 
cd ~/src/program_name
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
make install
make clean
```

To explain these commands:

**sudo mkdir temp-install** creates a temporary directory which you can delete after you're done installing.
**cd temp-install **switches to the directory you just created
**tar xvfz ~/Desktop/something.tar.gz** unzips the file from your desktop to the folder you are currently in. Replace something.tar.gz with your file's name
**./configure** configures the make file for compilation.
**make** makes the package for installation.
**make install** intalls the package you just created using the make command.
**make clean **removes configuration files from the current directory.

It has been suggested to me that one always keep the source files, so I have edited this post to reflect that practice.

---

### Post by asmiller-ke6seh on 2007-12-20
Also, you should always check to see if the program is in the Ubuntu repositories, first - because installing and uninstalling these programs through Synaptic or APT-GET (command line) is always easier.

Next easier is installing any other DEBIAN repository.

Next easier is taking an RPM distribution and using ALIEN to make it into a DEBIAN .DEB and then installing it.

---

### Post by thelatinist on 2007-12-20
> **asmiller-ke6seh said:**
> Also, you should always check to see if the program is in the Ubuntu repositories, first - because installing and uninstalling these programs through Synaptic or APT-GET (command line) is always easier.

Next easier is installing any other DEBIAN repository.

Next easier is taking an RPM distribution and using ALIEN to make it into a DEBIAN .DEB and then installing it.

+1

---

### Post by iamclueless on 2007-12-20
> **mmb1 said:**
> You want to uninstall from terminal, or synaptic?

whatever is easier.... i assume its in synaptic

but willing to learn how to do it in terminal

---

### Post by iamclueless on 2007-12-20
> **thelatinist said:**
> Are you asking how to build from source?

If so, assuming you've downloaded a .tar.gz archive to your desktop (modify as necessary).

```
sudo mkdir ~/src/program_name 
cd ~/src/program_name
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
make install
make clean
```

To explain these commands:

**sudo mkdir temp-install** creates a temporary directory which you can delete after you're done installing.
**cd temp-install **switches to the directory you just created
**tar xvfz ~/Desktop/something.tar.gz** unzips the file from your desktop to the folder you are currently in. Replace something.tar.gz with your file's name
**./configure** configures the make file for compilation.
**make** makes the package for installation.
**make install** intalls the package you just created using the make command.
**make clean **removes configuration files from the current directory.

It has been suggested to me that one always keep the source files, so I have edited this post to reflect that practice.

thanks! this can be a general guide for dealing with these kinds of files in the terminal

---

### Post by iamclueless on 2007-12-20
> **asmiller-ke6seh said:**
> Also, you should always check to see if the program is in the Ubuntu repositories, first - because installing and uninstalling these programs through Synaptic or APT-GET (command line) is always easier.

Next easier is installing any other DEBIAN repository.

Next easier is taking an RPM distribution and using ALIEN to make it into a DEBIAN .DEB and then installing it.

ok thank you

so at this stage of my limited knowledge of commands,,, stay away from the terminal then

wouldnt even know where to start with DEBIAN or ALIEN.

withl APT-GET i assume i need to know what i want. i will play with it now

thanks

---

### Post by rsambuca on 2007-12-20
You'll probably need to use 

**sudo** make install

---


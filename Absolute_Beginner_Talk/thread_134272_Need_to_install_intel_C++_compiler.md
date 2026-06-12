---
title: "Need to install intel C++ compiler"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-21
I downloaded the following file from intel.. Supposively its a compiler..

l_cc_c_9.0.030.tar.gz

The instructions say to..  
"2.Â  Run the downloaded file and proceed through the installation process
(requires the above serial number)."

How do i run that downloaded file.. Doesnt make sense.. it seems like that downloaded file is a compression pack like a zip.. You cant run a zip.. What do i run?

---

### Post by kaamos on 2006-02-21
If you have a graphical enviroment just right click on the file and choose "extract". Hopefully there will be some README with the files.

If you are on a no-gui system you can extract the package with
```
tar xfvz l_cc_c_9.0.030.tar.gz
```

---

### Post by systemintheglitch on 2006-02-21
I can extract it just fine.. Its just what do i do with the files once theyre extracted how do i RUN the main compiler?

---

### Post by tadashi on 2006-02-21
Did you look for a readme or install text file?  Usually that will be in there to give you the commands like
./configure
make
make install
make clean

Then you should have the doc files to explain how to use it, whether it is a GUI program or command line.

If it is an rpm or deb file then you will have different commands.

---

### Post by carlosqueso on 2006-02-21
you need to cd into the directory to which you extracted the files.  There should be a file that says something along the lines of install, just type ```
./name-of-file
``` and it should take care of the rest.

---

### Post by benguin on 2006-02-21
Hi,
The installation instructions for icc-9.0 are on the intel compilers website. Basically you have to untar into a directory where you have write access, cd into the directory that is created after the untarring, and run ./install or ./install_something. The link at the Intel site is this:

[http://www.intel.com/software/products/compilers/clin/docs/INSTALL.htm]("http://www.intel.com/software/products/compilers/clin/docs/INSTALL.htm")

Cheers,
-J-

---

### Post by abhaysahai on 2006-02-22
OOPs,
or you can simply install the g++ compiler in synaptic

terminal :
sudo apt-get install g++

That is if you do not have specific reason to use intell compiler. 
Well considering that you are unable to install from a tra.gz file, I do not believe that you are looking for specific compiler, any compiler should work fine for you.

---


---
title: "How to? install .tar.bz2 (tarball)"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-01-20
I have a .tar.bz2 I want to install.....How?

---

### Post by melancholeric on 2007-01-20
that depends entirely on what's inside the tarball. I'd probably start from extracting it.

---

### Post by PurplePenguin on 2007-01-20
> **Hamm said:**
> I have a .tar.bz2 I want to install.....How?

Once you do extract it (through the command line or by clicking on the package in nautilus), you'll see what's inside.  Usually there's an INSTALL file telling you exactly how to get the program installed.  It's good to read this each time, because there are often specific things that you'll need to do.  

It also might list dependencies (other programs that it relies on) that you'll need to hunt down and install as well.

Sometimes it'll be a binary file that is ready to be unpacked to some directory and it's all ready to run.

Usually, though, it'll be the source code for a program of some sort.  It's useless to you until you compile it.  There are three main commands you'll need to write in the terminal (in the directory where you unpacked the tarball) to install something from source: 

```
./configure
make
sudo make install
```

These commands don't come installed in ubuntu, though!  You've got to install a package called build-essential first:

```
sudo apt-get install build-essential
```

Keep in mind, if you have problems with dependencies, you'll know because you won't get past the ./configure step!  Take care to read the final lines of this and the other steps to see if they were successful or not.

---

### Post by MrKlean on 2007-01-20
Just my two cents worth.  Once I got the Windows way of doing stuff outa my head... This make install thing is way easier !!  It Tells you where ya went wrong and what you need ans forum help is great!!   If an install in windows doesn't go right, you're SOL  ( short on luck) LOL!!  ND.. you will learn more in 1 evening then you did in a year with windows ; )  Just my humble opinion ; )
Thanks ; )

---

### Post by bodhi.zazen on 2007-01-20
Just two comments:

1. What are you trying to install ? Are you sure there is not a package in the Ubuntu repositories ?

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

2. Take a look at checkinstall

[indent]Checkinstall sometimes fails, but if it works it makes a .deb package which is easire to track and uninstall[/indent]

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

	[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)

---

### Post by PurplePenguin on 2007-01-20
> **MrKlean said:**
> Just my two cents worth.  Once I got the Windows way of doing stuff outa my head... This make install thing is way easier !!  It Tells you where ya went wrong and what you need ans forum help is great!!   If an install in windows doesn't go right, you're SOL  ( short on luck) LOL!!  ND.. you will learn more in 1 evening then you did in a year with windows ; )  Just my humble opinion ; )
Thanks ; )

To add to this (I agree completely), if something does happen to be in the respositories, it's RIDICULOUSLY easy to install! =D> 

So with Ubuntu, you get a bit of both... constant learning and ease of use! :D

---

### Post by RealG187 on 2007-08-06
Is tar.gz the standard for Linux install, I know in Ubuntu deb is but I dont think DEB works in distors like Fedora Core, DSL, Red Hat, or any ohter non-Ubuntu distors. I also have a .bin file too, how come these files are so hard to install?

---

### Post by Frak on 2007-08-06
Right click, extract the contents of the file into a folder (make sure the files that are put in the folder are files and folders, not just one folder. If it is just one folder, double click it, there should then be a bunch of files, extract them all to that folder.). Rename that folder to program. Goto Places->Home Folder, place the folder called program (keep the name exactly like that, Linux is case sensitive!!!) into the Home folder.
now run this in the terminal (Applications->Accessories->Terminal)
```
sudo aptitude install build-essential
```
This will install the stuff necissary to install sources.
Now, enter
```
./configure
make
sudo make install
```
If it didn't succeed (Which it might not)
Goto your home directory, rightclick, create document. Now name this document script
Double click this file and a text editor will appear, enter
```
       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done
```
Save it
Then run in the terminal
```
chmod +x script
sh ./script
```
And paste the output to us and well help.

---

### Post by Zilphanael on 2007-08-10
I'm trying to do the same thing as the original poster...After following all the instructions, this is what I got:
strace: ./configure: command not found

---

### Post by Tyke91 on 2007-08-10
> **RealG187 said:**
> Is tar.gz the standard for Linux install, I know in Ubuntu deb is but I dont think DEB works in distors like Fedora Core, DSL, Red Hat, or any ohter non-Ubuntu distors. I also have a .bin file too, how come these files are so hard to install?

actually, .deb files will work for damn small linux because it is debian based

Red Hat and Fedora core both use .rpm files instead, but you can easily change the two around using a program called alien. 

.deb files for debian and .rpm files for fedora are my favorite way of installing things "the long way" because they are just click and go. ofc, the easiest way to do anything is the repos and you should always try those first.

---

### Post by Frak on 2007-08-10
> **Zilphanael said:**
> I'm trying to do the same thing as the original poster...After following all the instructions, this is what I got:
strace: ./configure: command not found
run in the terminal
```
cd **/path/to/folder/**
```
then run
```
chmod +x configure
```
then run
```
./configure
```
again.

---

### Post by Zilphanael on 2007-08-10
Whenever I try the "chmod +x configure", I get "no such file or directory".  Yes, I installed build-essential.

---

### Post by Frak on 2007-08-10
then skip ./configure and just run
```
make
sudo make install
```

---

### Post by Zilphanael on 2007-08-10
make: *** No rule to make target `install'.  Stop.

Is the new error message.

---

### Post by bwtranch on 2007-08-10
#9 Not all source files have the configure script:(  ./configure will not work

That doesn't necessarily mean that it won't install because configure doesn't install anything. It mostly checks for dependancies and other things on your computer.

After extraction make sure that the files go into the right directories. Just letting the files hang out will lead to bad installs and is a sloppy file manaegent system. (sorry, I can't spell anything today, I think writing programs screws up your spelling)

You can use /home/username/Desktop to download the file into and that is what Firefox likes. I really don't like it that much, but it is easier. You can right click and extract it there also (that really sucks). I have even seen people recommend putting the files under root. /  Beat them with a spoon!:(

Look, if we want to keep our life (on the computer) organized, we have to think about the file structure or pretty soon our stuff will look like windoze. And you know what that leads to? chaos, of course.

So, create a directory for your downloaded tar files " mkdir /home/debian/filename
Put the tar.gz in there and it will create it's own sub-directory called <filename>. Now, you can look at the install and readme files and figure out what to do. 

./configure
make
make install

Now we don't have a bunch of files hanging around in the Desktop or the (god forbid) top of the root folder. If your little package didn't come with a configure script, then, shame on them. Programmers are some lazy individuals sometimes (just like cops) and thought that all the work that they put in was good enough for the lower forms of life. 

How to do a configure script isn't all that hard, but it does take some research and some tools. Get a copy of build-essential " sudo apt-get build-essential  " and it will have most of what we need.

I'm sorry folks, I am so tired, I am having a hard time concentrating. I think I pretty much got across what I wanted to.:)

---

### Post by Frak on 2007-08-10
Moreover, ./configure creates the make script that is specifically built for your system.

---

### Post by bodhi.zazen on 2007-08-10
*.tar.bz2 is just an archive, like a zip file if you come from a windows background. Inside there can be most anything from source code to a python script to a binary.

There should be a README, that is often the best place to start.

Otherwise you need to tell us exactly what you are trying to install with a link to the  home and download pages.

> **Tyke91 said:**
> actually, .deb files will work for damn small linux because it is debian based

Red Hat and Fedora core both use .rpm files instead, but you can easily change the two around using a program called alien. 

.deb files for debian and .rpm files for fedora are my favorite way of installing things "the long way" because they are just click and go. ofc, the easiest way to do anything is the repos and you should always try those first.

Just wanted to point out that that is a gross over simplification. Just because it is a .deb does NOT mean it will install on DSL. for example DSL is running a 2.4 kernel. In fact I would bet most Debian or Ubutu .deb will not install on DSL (DSL has their own packaging standards, for example it uses apt although apt-get can be configured after a hard drive install).

Closer to home, and more important, .deb. from Ubuntu and Debian (or Mepis/Freespire, etc) are NOT interchangeable and mixing and matching can cause package, or worse system breakage.

Same goes for .rpm You are not free to mic and match SUSE/Fedora/Mandriva just because the file is a .rpm

---

### Post by bwtranch on 2007-08-10
Re: #17 That is exactly right. Tarballs are like a box of chocolates. Another thing that I wanted to mention is  while you can use alien to convert from rpm to deb, it does not always work and can lead to unstable programs. Best to compile from source and create a true deb package. See the Debian Maintainers Guide for how to do this.:)

---

### Post by Frak on 2007-08-10
> **bwtranch said:**
> Re: #17 That is exactly right. Tarballs are like a box of chocolates. Another thing that I wanted to mention is  while you can use alien to convert from rpm to deb, it does not always work and can lead to unstable programs. Best to compile from source and create a true deb package. See the Debian Maintainers Guide for how to do this.:)
+1, I totally agree.

---

### Post by RealG187 on 2007-08-12
> **Frak said:**
> Right click, extract the contents of the file into a folder (make sure the files that are put in the folder are files and folders, not just one folder. If it is just one folder, double click it, there should then be a bunch of files, extract them all to that folder.). Rename that folder to program. Goto Places->Home Folder, place the folder called program (keep the name exactly like that, Linux is case sensitive!!!) into the Home folder.
now run this in the terminal (Applications->Accessories->Terminal)
```
sudo aptitude install build-essential
```
This will install the stuff necissary to install sources.
Now, enter
```
./configure
make
sudo make install
```
If it didn't succeed (Which it might not)
Goto your home directory, rightclick, create document. Now name this document script
Double click this file and a text editor will appear, enter
```
       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done
```
Save it
Then run in the terminal
```
chmod +x script
sh ./script
```
And paste the output to us and well help.

```
mpg@--Removed--:~$ mpg@--Removed--:~$ ./configure
bash: mpg@--Removed--:~$: command not found
mpg@--Removed--:~$ bash: ./configure: No such file or directory
bash: bash:: command not found
mpg@--Removed--:~$ mpg@--Removed--:~$ make
bash: mpg@--Removed--:~$: command not found
mpg@--Removed--:~$ make: *** No targets specified and no makefile found.  Stop.
bash: make:: command not found
mpg@--Removed--:~$        

```

Thats what I get

---


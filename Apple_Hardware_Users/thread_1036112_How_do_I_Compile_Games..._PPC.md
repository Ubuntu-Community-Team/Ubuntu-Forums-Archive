---
title: "How do I Compile Games... PPC"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by McFrostey on 2009-01-10
I heard that 3-D games on PPC ubuntu dont work at all except for the games that use the Quake3 Game Engine... well my favorite game ever is Called Urban Terror. and its Based on the Quake 3 Game Engine. so im new to linux and im just learning whats compile and how do i do it?:confused:

---

### Post by jonnycom on 2009-01-10
[http://stargate.mgm.com/specialops/link.php?urlid=46&id=6544](http://stargate.mgm.com/specialops/link.php?urlid=46&id=6544)

---

### Post by aftershave0013 on 2010-10-05
good question.

i need to compile urban terror for ppc. yet have no idea how to compile. is there a how to compile for dummies?

any help would be awesome

---

### Post by trj021782 on 2010-10-05
Hi guys

Here is one way to compile that *may* work for you:

first you will need to download the file, it will most likely be in a .tr.bz or .tr.bz2 format. these are just compressed containers like .zip or .rar files. 

next you will need to extract the files from this container to a directory, I would reccomend making a new folder in the /user/local directory call it something you will remember

then you will need to open a terminal and and navigate there with the command 

(presuming you used the instructions I recommended) 

cd /user/local/[insert created folder here]

then you will type in 

sudo ./configure

if this reports any errors you will need to bring them to me or research them online

if it does not report any errors type

sudo make

if this does not report any errors then type 

sudo make install

and if this does not report any errors the game has installed successfully and *should* be accessible from your applications menu 

if any part of this does not work for you come back and tell me and I will try to help.

Here are some side notes to help you better understand what you are doing

sudo - is a command that I believe stands for "super user do" it will allow you to do high level modifications to your system and will most of the time prompt you for a password to continue - your normal ubuntu login password will work

./configure - many programs that come as source code contain a configure file that will have various options just typing "sudo ./configure" will usually set the install to default - if this file does not exist then you may want to check for a readme although i have found readme files to be less than helpful with compiling

make - is the command that actually compiles the software - if successful it will output a variety of files that it has created

make install - installs the file that the make command created

 if you guys would like you can link me to the game you want to install and i can try to compile it myself and report my findings to you, however there are two things to keep in mind if you do it this way:

1: I am using a PS3 (which is based on the PPC architecture) so it may work differently for me

2: give a man a fish or teach a man to fish - If I do it for you, you will never learn how to do it yourselves and that may be worse for you down the road

No matter what make sure to let me know what happens i am very interested in you results

ALSO IF YOU NEED LIVE SUPPORT I AM AVAILABLE AS [email]TRJ021782@yahoo.com[/email]

---

### Post by zeroti on 2010-10-06
trj021782 gives pretty good advice. one thing I would change is that I would unpack the archive in a folder that lives in the home directory, not the system path /usr/local/. So the following instructions would work for a .tgz file, other commands or variations would work for .zip files or .bz2.

first open up a terminal window from the Applications > Accessories menu.
```

sudo apt-get install wget
mkdir src
cd src
wget http://www.somesiteurl.com/whatever/somesource.tgz
tar zxf somesource.tgz
ls
cd <name of directory that now shows up>
ls
less <name of readme file> (use arrows to scroll, q to quit less)
./configure
make
sudo make install
exit

```keep on the lookout for errors at the end of the output before typing next commands. to know more about any of these commands or their options, type "man <command name> <enter>". you can skip the commands with wget and tar, just download the source archive with your browser and double click the archive icon. then extract it to a folder in your home directory. :)

If you have time and/or are curious, this introduction to the command line could be useful: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

---

### Post by trj021782 on 2010-10-06
Zeroti gives great advice, however I have done some research and I have been unable to find a PPC compatible copy of "Urban Terror"

So, Aftershave, If you would like to run this game on your PPC system you will need to install Qemu and if you can successfully compile Qemu I would like to hear about it because I have been trying for weeks and my copy ALWAYS hangs on the translate.o file

none the less, after you have downloaded and unpacked the Qemu files - navigate to the directory in a terminal and do this

sudo apt-get build-dep qemu

this should set up all of your dependencies for you

The ./configure command for compiling qemu has A LOT of options but the one that is most important for you will be the target-list option. I am assuming you will want to emulate a standard PC so you should use the command 

sudo ./configure --target-list=i386-softmmu,x86_64-softmmu

then do

make 
make install

and see what happens, you will have to do the foot work yourself on how to use qemu but it will allow you to run windows apps

---


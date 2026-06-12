---
title: "ndiswrapper"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by James0044 on 2006-08-26
I'm totally new to Linux, but thought i'd give Ubuntu Dapper a try.

I'm trying to install ndiswrapper. I have unpacked the downloaded file into my userspace, but the instructions are not telling me to go to the source director and run a make install. 

What does that mean?

i know it is me being a bit simple, but i have only been running Ubuntu for 3 days, and i'm not all that computer literate.

any help on this or the install in general would be a grewat help. 

Thanks
James

---

### Post by James0044 on 2006-08-26
Sorry, that should read, the instructions are NOW telling me. 

Sorry.

---

### Post by lynxus on 2006-08-26
It meand change dir to the folder you installed to and ruina Make Install ( A command )

Open a terminal and type something like.

blaa@blaa# cd /home/username/ndiswrapper
blaa@blaa# make install

Or open teh synaptec manager and search for ndiswrapper to install from there..

FYI: im hungover so my spelling is off lol..

---

### Post by benfindlay on 2006-08-26
So you've downloaded the source code I take it, with a file name similar to ndiswrapper-1.23.tar.gz

Once it's downloaded you need to open terminal and change to the relevant directory, say /home/downloads

Open terminal (Applications>>Accessories>>Terminal)

type the following:

```
cd /home/downloads
```
This changes to the relevant directory where you saved the file

```
tar -xfvz ndiswrapper-1.23.tar.gz
```
This extracts the file into a folder called 123 (whatever the bit before the tar.gz is called for you)

```
cd ndiswrapper-1.23
```
This changes you into the relevant directory for your extracted files

```
./configure
```
configures it for install

```
make
make install
```
makes it ready, and installs it

You can also use synaptic package manager to simply do everything for you. Then you don't have any hassle!

---

### Post by James0044 on 2006-08-26
I'm going to give this synaptic thing a try i think.

it didn't work last time because i tried to install it before i unpacked it.

i'll give it a go.

Thanks again guys

---

### Post by Paul133 on 2006-08-26
So, you need to compile tar's drom source? And shouldn't you use checkinstall?

---

### Post by James0044 on 2006-08-26
hmmm, having a few problems. I've tried to use synaptic package manager, but it can't find anything to install (all the contents of the ndiswrapper directory are in grey, i can't select any of them).

also the make command does not work neither does the make install command (i'm typing these in terminal, in the ndiswrapper1.23 directory).

the only thing i can find in the instructions, which i have not doen is this: 

You need a recent kernel at least 2.6.6 or 2.4.26 with source. Under Red Hat or Mandrake, the sources can be installed using the package kernel-source<kernel-version>.rpm command. Make sure there is a link to the kernel source from the modules directory. /lib/modules/VERSION/build should be a link to the kernel source, where VERSION is the version of the kernel you are running. If there is no link, you'll get an error at the make install step. To create a link, assuming the kernel sources are present, use the command 

ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
Make sure you have started compiling the kernel sources, so needed header files are present. Some vendors ship ndiswrapper in their distributions. Either use it or make sure you remove it before installing ndiswrapper by yourself. Make sure you have the Wireless Tools installed. Again, there is a package that comes along with Red Hat and Mandrake distributions. If you are using Debian you can install the wireless-tools package from the mirror, here. 

because i didn't have a clue what it meant.

any ideas?

Thanks

---

### Post by Sabakunoneji on 2006-08-28
> **benfindlay said:**
> 

```
./configure
```
configures it for install


when i type ./configure it says something like there is no such directory.

and then when i try make and make install, it says that it doesnt recognize the make command

is there something i have to do before all of this?

thanks

---

### Post by benfindlay on 2006-08-28
First you have to extract the file from its tarball source. Do this as follows:

Say the file is saved in a folder called downloads on the desktop. Launch the terminal from the applications>>accessories tab and type:
```
cd Desktop
``` (CASE SENSITIVE)
This puts you in the relevant directory within the terminal

Then type:
```
tar -xfvz [filename].tar.gz
``` [filename] is whatever you have before .tar.gz

THen type ```
cd [filename]
``` to change to the directory it just extracted the stuff to

From there you type your ./configure, make and make install

---

### Post by Sabakunoneji on 2006-08-28
when i try tar -xfvz ndiswrapper-1.23.tar.gz it says something about how there is no directory vz or something

---

### Post by benfindlay on 2006-08-28
If ndiswrapper-1.23.tar.gz is definitely the right file name, try:

tar xfvz ndiswrapper-1.23.tar.gz

Note, no hyphen this time, can't quite remember whether its meant to be there or not!

---

### Post by Ragazzo on 2006-08-28
You need to have build-essential package installed before you can use make. In terminal: "sudo apt-get install build-essential"

---

### Post by benfindlay on 2006-08-29
> when i try tar -xfvz ndiswrapper-1.23.tar.gz it says something about how there is no directory vz or something

I just found that exact problem! All you do to solve it is leave out the letters it complains about from teh -xfvz part of the command line!

---


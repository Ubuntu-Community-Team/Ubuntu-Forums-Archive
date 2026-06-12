---
title: "Extremely Noob Question..How to Compile"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-07
I need to compile a kernel module for my ethernet card rtl8139D
I got a 8139too.c thingy...
I have no idea on how to compile that damn thing..coz thats
a kernel module.

I am attaching the file here.

Please help me guys.
If possible can I have the .ko output file please??
Else...just lemme know the procedure.
I'll try to do it myself


P.S::Please temme the proc. even if u have compiled it for me.
I need to learn , u know

---

### Post by Sef on 2006-05-07
To compile, read these two sites:

1) [http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

2) [http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

---

### Post by mostwanted on 2006-05-07
A slight correction on no. 2 :)

2) [http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)

---

### Post by hellmet on 2006-05-07
ppl ppl ..
I need to COMPILE the .C file ...as a Kernel Module.
The ouput shud be .ko
That will be later loaded as a driver for
my Eth Card.
Please help ppl.

---

### Post by Sef on 2006-05-07
go to this wiki and see if you can find what you are looking for.

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=kernel&titlesearch=Titles]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=kernel&titlesearch=Titles")

---

### Post by hellmet on 2006-05-07
No

---

### Post by jasay on 2006-05-07
hellemt, 

First of all, I don't know anything about kernel modules, but . . . 
I have a 8139too.ko in /lib/modules/2.6.12-10-686-smp/kernel/drivers/net

Would this work, or are the sources you found different (new, patched, etc.)?

---

### Post by patrick295767 on 2006-05-07
```

apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 
apt-get -f -y install  

cd /root/myfoldercontainingthesource
./configure
make 
make install
```

---

### Post by zerhacke on 2006-05-07
[QUOTE=hellemt]I need to compile a kernel module for my ethernet card rtl8139D
I got a 8139too.c thingy...
I have no idea on how to compile that damn thing..coz thats
a kernel module.

I am attaching the file here.

Please help me guys.
If possible can I have the .ko output file please??
Else...just lemme know the procedure.
I'll try to do it myself


P.S::Please temme the proc. even if u have compiled it for me.
I need to learn , u know[/QUOTE]
It is not the Linux way to compile it for you.  I'm not even sure that if they compiled it on their machine if it would work on your machine due to library differences, kernel differences, configure options, that kind of thing.

Point is, nobody's going to compile it for you.  So far plenty of people have given you the tools to do it yourself.  Go read now.

---

### Post by skippy81 on 2006-05-07
OK this is the problem Helmutt. Because the driver code you have has been part of the linux kernel for years, it is very hard to find a makefile for it.  There is no point in asking someone to compile that driver for you, since if they have a different kernel to you it won't work.  It is also pointless because you allready have a COMPILED version of that module on your system - you have allready tried to load it using the > modprobe 8139too command and it didnt work.

Your only hope would seem to be to add a line of code to the modules source code (8139too.c) and compile it as a kernel module as per the link you found earlier. 

If you really want to do this, then download the complete kernel tree for your version of the kernel.  You will have to manually edit the raw c file to add the 'magic' line, and then compile a new kernel as per [http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel.org]("http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel.org").

To be honest it is pointless.  The value of your time is far more than the value of teh network card you need to replace.  You have tried your 8139 network card with ndiswrapper, 8139too and 8139cp drivers now.  Why not just buy another model?  Trying an even older driver than the one that comes pre compiled with the kernel is not going to help things.

---

### Post by hellmet on 2006-05-07
Seems like I have come to a dead end .
Okay guys I'll have to wait for my new NIC,
ot I'll try some friends NIC first and then  see  .
Thanks guys for all your help.

---

### Post by skippy81 on 2006-05-08
Probably for the best.  You were just unlucky mate, most of the 8139 series do seem to be supported well, the D type seems to be the 'black sheep' of the family.  All is not lost of course, you can always use the 8139 in a Windows PC.  Once you have a compatible network card you will find the whole linux expierience far more fun - no more manually unpacking packages etc :)

This link may be of use > [http://hardwaredb.suse.de/productSearch.php?page=1&LANG=en_UK&searchtype=extended&PHPSESSID=0324e7ec12827da6dfcdae5b639f2901](http://hardwaredb.suse.de/productSearch.php?page=1&LANG=en_UK&searchtype=extended&PHPSESSID=0324e7ec12827da6dfcdae5b639f2901)

The SMS EZ-card and the Realtek 8129 tend to be the best supported budget cards.  

As an amusing note to you, I was looking through my hardware drawer for a spare network card so I could test its compatability.  Guess what I found?  A dreaded 8139D :p I got it from a hardware shop about a year ago for £5, I got quite a lot of disconnects while gaming in windows with it so I had removed it - I think it's next destination is the dustbin.

---

### Post by hellmet on 2006-05-09
he he...
skippy, i got myself a new D-Link 520TX..and guess what
I am connected.
I am writing this from Ubuntu.
I am excited.
Thanks a lot for all the support u gave...
Will catchya later

---


---
title: "cant get myself connected"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by di22y on 2007-11-22
I've been having problems getting connected to the internet whilst running Ubuntu I have a BeWan ADSL PCI modem in my computer and have downloaded the linux drivers for it from the manufacturers website whilst running in windows then restarted in Ubuntu. I have also checked the device manager (in Ubuntu) and the modem is detected there. I cannot figure out how to install the drivers for the modem as it is not like windows where you open the the setup.exe. Im not sure if I even need the drivers for the modem to work. After going through the help within ubuntu and searching the forums I am still unable to connect to the internet I would appreciate any help and advace you have to give me.

PS Have been into network and entered IPs and DNSs etc
also one quick question in the phone number dialogue can you enter multiple numbers seperated by commas like in windows.

---

### Post by tyggna1 on 2007-11-22
there are a number of different ways to "install" drivers.

The first, and most likely to work in your case, is to go to the directory that the drivers are in, and from the terminal type in:
```
sudo ./configure
sudo make
sudo make install
```

This will take a bit of time between each command--but that will compile your driver and put it into a format that Linux can use.

The next option is to install it by typing in
```
sudo modprobe -i driverName
```

Let me know how it works

---

### Post by di22y on 2007-11-22
I have tried what you suggested to no avail, can I just check I am doing everything right. In Terminal I typed:-

            sudo /home/dizzy/desktop/unicorn/adsl_status/configure

I tried different variations incase the driver was located elsewhere but just kept getting the message 'command not found'. When I tried the second suggested method I get the message module '' not found. I typed:-

            sudo modprobe -i unicorn_pcidrv.c

I even tried typing exactly 'sudo modprobe -i driverName' and got the same mesage.

The file unicorn_pcidr.c is located deeper within the files however in a different folder there is a file name 'configure' it is described as a shellscript when I run it in Terminal it creates another file named condefs.h which appears to be a blanc document described as a C header and opens in a program called gedit. Dont know how much of this is relevant but I hope this helps you help me.

---

### Post by StubbsPKS on 2007-11-22
> **di22y said:**
> 
            sudo /home/dizzy/desktop/unicorn/adsl_status/configure


Hmmm... try going to the directory and calling the configure from within the directory.

cd /home/dizzy/desktop/unicorn/adsl_status
sudo ./configure

Let us know how that works out for ya.

---

### Post by annda on 2007-11-22
first of all, make sure you can actually compile source code (this is what you need to do and it is more difficult than installing but necessary for not so popular pieces of software).

copy and paste this in the terminal to install all the tools you need for compilation: 
```

sudo apt-get install build-essential
```

---

### Post by annda on 2007-11-22
> **StubbsPKS said:**
> Hmmm... try going to the directory and calling the configure from within the directory.

cd /home/dizzy/desktop/unicorn/adsl_status
sudo ./configure


also use TAB-completion for your commands in the terminal. i'm sure it's **D**esktop with a capital D, not desktop - that way you will avoid typos. simply type the first few letters of the command or filename and hit the TAB key. if it does not complete, hit TAB again to see possible options. if you get none, there is something wrong.

so i'd do it like that:

```
cd /home/d[TAB]
```

so you get to see:

```
cd /home/dizzy/
```

now 

```
cd /home/dizzy/De[TAB]
```

and so on.

when you get to the directory with your files, use that configure command.

---

### Post by di22y on 2007-11-22
> **StubbsPKS said:**
> Hmmm... try going to the directory and calling the configure from within the directory.

cd /home/dizzy/desktop/unicorn/adsl_status
sudo ./configure

Im not sure what you mean by calling the configure from within the directory. I have copied some of the command text I have tried from within Terminal below to to try help with the matter. There is also a screen shot of some of the files within the driver package I download just to try and give some kind of clue as to what I need to do. By the way that tab-completion was a really handy tip, thanks alot. Oh yea I have installed that build essential aswell.

dizzy@Dizzy:~$ sudo /home/dizzy/Desktop/unicorn/adsl_status./configure
[sudo] password for dizzy:
sudo: /home/dizzy/Desktop/unicorn/adsl_status./configure: command not found
dizzy@Dizzy:~$ sudo /home/dizzy/Desktop/unicorn/unicorn_pci./configure
sudo: /home/dizzy/Desktop/unicorn/unicorn_pci./configure: command not found
dizzy@Dizzy:~$ sudo modprobe -i driverName
FATAL: Module driverName not found.
dizzy@Dizzy:~$
*(This is the text from the terminal)*

[ATTACH]51059[/ATTACH]

---

### Post by di22y on 2007-11-22
I think that I have to Kinda make my own driver from the stuff I dloaded. The makefile files provided by the manufacturer contain all different bits of scrips of which i am supposed to compile(I think) the relevant bits depending on different variables such internet protocol and such. I hope this isnt the case.


I just tried the following:-
sudo /home/dizzy/Desktop/unicorn/adsl_status/configure
*(When I pressed enter I got the following)*

loading cache ./config.cache
checking for non-GNU ld... /usr/X11R6/bin/ld
checking if the linker (/usr/X11R6/ld) is GNU ld... yes
configure: error: can not find install-sh or install.sh in /home/dizzy/Desktop/unicorn/adsl_status /home/dizzy/Desktop/unicorn/adsl_status/.. / home/dizzy/Desktop/unicorn/adsl_status/../..

Talk about jumping in at the deep end. The thing is I'm not going to be able to access the internet without switching back and forth between windows and Ubuntu which I'll probably need to do if I'm every going to sort this out. I am going to beg now for some serios help, not that I dont appreciate the help I've been given so far. I have uploaded a copy of the drivers I have so anybody who wants to take a look can gain a better understanding of what I'm waffling about. they are available here   [http://uk.geocities.com/di22y@btinternet.com/A1012-A1006-A904-A888-A983-0.9.3.tgz]("http://uk.geocities.com/di22y@btinternet.com/A1012-A1006-A904-A888-A983-0.9.3.tgz") 1.3meg

Here is part of the readme file I got with the drivers, I think I have to fill in certain parts of some 'makefile' files and then do some other stuff(duh) to get this thing working.

COMPILATION:

To compile the drivers, unzip and untar the file. In the unicorn directory you 
will find the two subdirectories unicorn_atm and unicorn_bus.
You may compile the drivers based on the include files in the kernel source
or standard kernel include files. Set the variable KERNELDIR in the Makefile's
to point to your kernel sources if the first option in chosen. 
If you choose the latter, you may need to copy the contents of the kernel 
source "include/net" directory into "/usr/include/net/".
Go into these subdirectories and do a "make" and a "make install".
If the compile option "USE_HW_TIMER" is set, the performance is increased, 
but the CPU load increased. 
Use the same compiler as you use when compiling the linux kernel. The driver has
been tested using gcc-2.96, gcc-2.95.2, gcc-2.91.66, gcc 3.0.3 gcc 3.4, gcc 4.

I have had look through some of the makefiles and the parts which need filling are clearly highlighted but I'm just way out of my depth the full readme file is available from the link above if anybody is willing to take a look. The thing is aswell I have been trying to install this now for a couple of days and I may have installed bits and bobs which shouldnt have. oh well let me know.

---

### Post by www.rzr.online.fr on 2008-07-10
> **di22y said:**
> I've been having problems getting connected to the internet whilst running Ubuntu I have a BeWan ADSL PCI modem in my computer and have downloaded the linux drivers 

Maybe you can test the precompiled  one , I built for dapper

[http://rzr.online.fr/q/unicorn](http://rzr.online.fr/q/unicorn)

---


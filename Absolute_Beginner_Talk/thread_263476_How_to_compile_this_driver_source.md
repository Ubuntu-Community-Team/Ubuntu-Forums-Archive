---
title: "How to compile this driver source?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2006-09-23
Hi,

I've been referred to this URL to get the source for the drivers I need to install from scanModem:

> [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

First, there are ten files here, which one do I want to compile?

Secondly, The one I picked and tried to compile wouldn't. I used the command one of the readme's said to use "make all" and it didn't seem to do anything and among the text printed were messages such as "Entering unknown directory" which appeared to be errors.

---

### Post by podunk on 2006-09-23
Take into consideration I'm new at this! Before you can install you need to use Synaptic Package Manager to install the package:
build-essential

I'd suggest getting the package:
checkinstall 
at the same time. If where you see an instruction to type:
```
make install
```
you type
```
checkinstall
``` 
instead it will make it very easy to remove stuff when it turns out not to be right. :-D By typing "checkinstall" it puts a package in Synaptic package manager - you get to name the package so chances are very good you'll be able to remember it.

I can't help you with which version to get, depends on your machine. i have a pretty plain jane AMD. 

In the read me in the web site directory  it seems to say there are packages already compiled here:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

did I read that right? In that directory there is directory 
Ubuntu
and there are .deb files there with various Ubuntu kernel names.

You can find which kernel you have by typing
```
uname -r
```
in terminal. download which ever one matchs the numbers from "uname -r"

Once it downloads just right click it and chose to install it with the package installer. If there is a dependency (a missing file or program) that you need it will list it at the top. So far every time it's listed a dependency for me I was able to find what I needed in Synaptic.

---

### Post by macdo on 2006-09-23
I'm presuming that you have already installed the build essentials package. If not ```
sudo apt-get install build-essentials
```

At a guess, you want martian-full-20060727.tar.gz

Download it, then extract it to a folder somewhere - /home/user/martian, in this example.
In the terminal: ```
cd /home/user/martian
make all
sudo make install
```

---

### Post by someonedumb on 2006-09-24
Thanks for the replies... I'm going one step at a time and did already have the build-essentials package installed, and its working.

When I execute the "make all" and "make install" commands I get errors. Here is a log of what happens in the terminal window.

> someone@someone-desktop:~/Martian/164x$ sudo make all
make -C kmodule/ modules
make[1]: Entering directory `/home/someone/Martian/164x/kmodule'
make -C /lib/modules/2.6.15-26-386/build M="/home/someone/Martian/164x/kmodule"  modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/someone/Martian/164x/kmodule'
make: *** [all] Error 2
someone@someone-desktop:~/Martian/164x$ sudo make install
make -C kmodule/ install
make[1]: Entering directory `/home/someone/Martian/164x/kmodule'
make -C /lib/modules/2.6.15-26-386/build M="/home/someone/Martian/164x/kmodule" modules_install
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/someone/Martian/164x/kmodule'
make: *** [install] Error 2

To clarify some things. The /Martian/ directory contains the tar file and the directory /164x/ which contains the unzipped source files (lots of .c, .h, files, clearly it was unzipped properly)

> In the read me in the web site directory it seems to say there are packages already compiled here:
[http://linmodems.technion.ac.il/pack...em/kernel-2.6/](http://linmodems.technion.ac.il/pack...em/kernel-2.6/)

did I read that right? In that directory there is directory 
Ubuntu
and there are .deb files there with various Ubuntu kernel names.



I have kernel version 2.6.15, the deb packages you find from directories other than [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/) do not work past kernel version 2.6.12. 

According to scanModem I need to use the drivers in the exact directory I originally mentioned. scanModem however does not say which package I need to use, and they are not named in a way that would allow one to determine what type of system or kernel they are intended.

---

### Post by maaronB on 2006-09-24
Ok it seems to me what you are missing is the /build part of this file
/lib/modules/2.6.15-26-386/build

I could not find any thing to help you with this, but while looking I came across a pacakge called 

linux-restricted-modules-2.6.15-26-386 
it says that it installs WinModems 

That doesn't answer your question at all, but I thought you might like to know.
(It says that it will install the driver for ltmodems)

---

### Post by someonedumb on 2006-09-24
I know about the linux-restricted-modules. It comes installed by default on my linux distro. And also, by default, the modem does not work. According to linmodems.org (and the scanModem tool) the 2.6.15 kernel will not have drivers written for it which will be compiled into a .deb package. Instead, the only drivers linmodems.org will support for 2.6.15 come from the martian package and must be compiled from source.

I'll uninstall and reinstall the build-essential package, maybe that will fix the "/lib/modules/2.6.15-26-386/build" file

If anyone thinks that there is a flaw in what I just said please say so. Is the linux-restricted-modules-2.6.15-26-386 written by someone other than linmodems.org? Is this package known to work?

---

### Post by _duncan_ on 2006-09-24
Did you install linux-headers-386?

I don't remember if it came with the default install of ubuntu dapper. But you'll definitely need them to compile kernel drivers. Try this if you don't have it:

```
sudo apt-get install linux-headers-386
```

If this doesn't work, you may have to manually download the package from the ubuntu repository. Look for the package **linux-headers-2.6.15-26-386**.

---

### Post by maaronB on 2006-09-24
Ok I figured out how to solve the /lib/modules/2.6... /build error
You need to install your linux-header-2.6.15-26 and linux-header-2.6.15-26-386 packages

---

### Post by someonedumb on 2006-09-24
Ok, I just logged back into Windows from linux, I was dinking around and installed the linux-header-2.6.16-26-386 package and that did not give me the "lib/modules/2.6.../build", but did not notice the linux-header-2.6.16-26 package

(did a search for "2.6.15-26-386")

I'll go install that second package :P

---

### Post by maaronB on 2006-09-24
I have gotten it to compile on my computer.
At first I was getting the same "unkown directory" Errors that you are, but after I installed the linux-header files I got past that.
Then I had problems that were caused by the 
```
martian-20060727.tar.bz2
``` from the website.  The  ma...tar.bz2 does not include all of the necesary files, so I tried the martian-20060727.tar.gz and everything compiled correctly.

You need to 
1. install the linux-header-2.6.<whatever yours is> & the linux-header-2.6.<whatever>-386 packages.

2. Make sure that you have the tar.gz NOT the tar.bz2 file from the website.

3. Type "Make all" per the instructions.

Those where the steps I needed to make it compile.

---

### Post by someonedumb on 2006-09-24
I just got back from linux again, and long story short the kernel headers are all in place now :) I compiled things and it appeared to work fine (I was using the martian-full-20060727.tar.gz file to begin with)

So the commands I used were:
sudo make all
sudo make install

Both returned no errors, but now I am confronted with my lack of understanding of what the second command is for... is the "make install" command actually installing the compiled driver into my system? Or is it just a second part to the build process?

---

### Post by maaronB on 2006-09-24
Make install installs it on to your computer, but you still have to load it  into the kernel to be able to use the driver. 
Incase you haven't notice their is a INSTALL text file in the file you downloaded.  It gives instructions on how to load the modules.

I am sorry, I don't know enough about modems, modules, or the kernel to tell you what your options should be.

---

### Post by someonedumb on 2006-09-24
Ok I think I have a pretty good handle on what I have left to do. Getting it compiled was the giant hurdle I was most worried about. Your help has been invaluable :D

---

### Post by someonedumb on 2006-09-24
Oh darn, it wasn't working as well as I thought it was.

So after downloading the source and executing the commands

make all
make install

I should have a file called "martian_drv" installed on the system and a file called "martian_helper" installed in /sbin/

But instead I have these(martian_helper is in the correct place)
> 
/lib/modules/2.6.15-26-386/extra/martian_drv.ko
/usr/sbin/martian_helper

the driver is the wrong filename and in the wrong place.
I'm supposed to be able to install the driver now with the modprobe command, however this is what happens when I try to do that:

> someone@someone-desktop:/lib/modules/2.6.15-26-386$ cd extra
someone@someone-desktop:/lib/modules/2.6.15-26-386/extra$ ls
martian_drv.ko
someone@someone-desktop:/lib/modules/2.6.15-26-386/extra$ sudo modprobe ./martian_drv.ko
FATAL: Module ./martian_drv.ko not found.

Why isn't the source compiling into the file "martian_drv" like it claims it will? Its not just a mis-named file because I cannot use modprobe on it, so it must not be compiled properly.

---

### Post by maaronB on 2006-09-24
It is working correctly.  Just type ```
sudo modprobe martian_drv
```
if it looks like nothing happens that is a good thing.
Then type ```
lsmod
```
martian_drv should be in the list of modules.

Just an FYI: the .ko is the extension for modules but you should not include it when you use modprobe.

---

### Post by someonedumb on 2006-09-24
> someone@someone-desktop:~$ sudo modprobe martian_drv
FATAL: Module martian_drv not found.
someone@someone-desktop:~$

Whoops, I forgot to post this log before.

I jumped ahead a little bit. Had this command worked I woudln't have spent so much time trying to figure out exactly what files "make install" added to my system and where they were stored.

So I guess my question is... Why did the module correctly get stored in the system but not "registered" as a module?(quotes because I know this is not the correct terminology)

---

### Post by someonedumb on 2006-09-24
Is there a way to check that the file "/lib/modules/2.6.15-26-386/extra/martian_drv.ko" is a proper module? And if so, how do I make linux recognize it as a module (so that I can type in "modprobe martian_drv" and have linux find it)?

---

### Post by someonedumb on 2006-09-24
I'm reading a tutorial on Linux 2.4x loadable kernel modules and its pretty awesome, but does anyone know a good source of info for 2.6x modules?

---

### Post by maaronB on 2006-09-24
I tried to to a modprobe martian_drv and had the same problem you did.  But, I have gotten it to work.  I went back to the website where you got the martian-full-20060727.tar.gz and instead downloaded an earlier version of it and redid all of the steps.  That worked.
So I have been looking around and it seems like the only difference between the two is that the old version added a line to /lib/modules/2.6<whatever>/modules.dep
So you should be able to cd to 
that location and put a line in with the location to martian_drv.ko

cd /lib/modules/2.6.15-26-386/ 

sudo pico modules.dep

add 
/lib/modules/2.6.15-26-386/extra/martian_drv.ko:  

make sure to include the :
that should enable modprobe to see your modules

---

### Post by someonedumb on 2006-09-25
Awesome! I'm able to load and unload the driver module now, and its pretty cool :) Thanks again for all your help.

Too bad this driver acts the same way as the original one that comes preinstalled on ubuntu... But at least now I know the problem has nothing to do with a driver, so time to start messing with pppd config files even though they all looked correct before.

---


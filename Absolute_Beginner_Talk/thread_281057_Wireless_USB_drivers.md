---
title: "Wireless USB drivers"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-20
I have a safecom USB wireless network adapter. It cam with drivers on a cd, and there is a /linux dir on the cd, and a pic of the linux logo, tuc on the packaging of the box, so im guessing it does work on linux... some how!

In the /linux dir on the cd there is a .tar.gz file.  I have copied this off the cd, and extracted it which just shows a few files and dir's such as "/menudbg, /src, and apdbg.c and other files with cog icons.

Can someone please tell me how to install these drivers? Once the drivers are installed, will it show the device in system>administration>networking? or is extra work needed, and if what?

thanks :)

---

### Post by SendDerek on 2006-10-20
Is there a README.txt file?  Or any other .txt file?  They usually have the instructions for installing.

Usually to install a 'tarball' you need to do these steps:

open terminal and navigate to the directory you have the configure file
./configure
sudo make
sudo make install

This should install it, but I don't know if it will show up in the networking menu.  That may require some extra work.

---

### Post by Tobywuk on 2006-10-20
i cant see a readme, or a file called "configre" file

When i did that sudo make, and sudo make install i get lots of things up. towards the end of all the lines it says

```

make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/toby/software/drivers/ZD1211LnxDrv_2_2_0_0 modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[2]: *** [all] Error 2
make[2]: Leaving directory `/home/toby/software/drivers/ZD1211LnxDrv_2_2_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/toby/software/drivers/ZD1211LnxDrv_2_2_0_0'
make: *** [all] Error 2

```

---

### Post by SendDerek on 2006-10-21
Okay, so no file called configure.  

make and make install won't work until the configuration file has been run.

So, I don't know how else to do it if there isn't a readme or an install.txt file.  Ummm, what's the file list?  Is there anyway you can get that posted here?

In the terminal, type "ls -a -C" while you are in the proper directory.  Maybe we can find something that looks like a configuration file.

---

### Post by SendDerek on 2006-10-21
Hey!  Look what I found!

A linux installation guide on Safecom's Products website.

This is the manual for the SWMULZ-5400 ([http://safecom.cn/code/sub/category.asp?prdid=321&subcatid=41#](http://safecom.cn/code/sub/category.asp?prdid=321&subcatid=41#))

[The Link to Manual]("http://safecom.cn/code/support/DMF.aspx?pid=321&pos=2#")

> 
2.2 Build and install the package:
The package contains drivers for ZD1211 and ZD1211B. If you doesn&#8217;t have specified
request, both of them will be installed.
Under the extracted directory, there is a Makefile in it. Because our driver can support for
kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify
the Makefile according to the path of &#8220;kernel source tree&#8221; and the version of the kernel
in your system. In the Makefile, you may see the following statements,
# if the kernel is 2.6.x, turn on this
#KERN_26=y
#KERNEL_SOURCE=/usr/src/linux-2.6.7
# if the kernel is 2.4.x, turn on this
KERN_24=y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8
If you want to build the kernel under the kernel of 2.4.x, one has to let the variable
KERN_24=y and comment the KERN_26=y like that as the example above and modify
the variable KERNEL_SOURCE to the path which you install the kernel source. After
doing these things, one just need to type the &#8220;make&#8221;, and the driver module will be
generated and installed.
2.3 Install individual driver:
If you only need driver of ZD1211 or ZD1211B, you can issue :
  make clean
  make ZD1211REV_B=0 (0 for ZD1211, 1 for ZD1211B)
  make ZD1211REV_B=0 install (0 for ZD1211, 1 for ZD1211B)
to install the driver.
2.4 Build the debugging tool:
There are two debugging tools in this package, &#8220;apdbg&#8221; and &#8220;menudbg&#8221;. Run &#8220;make
debug&#8221; to compile them both. If you don&#8217;t have the ncurse library, you may get some
error messages while compiling menudbg. You can ignore it and get apdbg only
3. Getting Start:
3.1 Load the driver:
One can use the modprobe &#8211;v zd1211(or zd1211b) to load our driver. In order to check
whether our driver is loaded successfully, one can use the &#8220;lsmod&#8221; for this check. If our
driver is loaded successfully, the following messages should be seen
...
zd1211 183576 0 (unused)
...
Please note that the 183576 may not be the same as that in your system.
3.2 Open the network interface:
In our driver, we will stop all the commands until the network interface assigned to us is
opened. One can open the network interface by the following command
]$ ifconfig ethX up
or
]$ ifconfig ethX <IP address>
3.3 Configure the Wireless settings
In our driver, we support the wireless extension commands to control our driver.



Try what it says there.  There are more tips for the installation on the manual (it's a pdf file).

Hope this helps more...

---

### Post by Tobywuk on 2006-10-21
Thank so :)

Iv been looking at that and..

It says i have to edit the makefile file. does editing this mean i only change =Y thats in the file to =N if i dont want that driver installed? and can i just leave it as it is? as it looks as if i just leave it then it installes both, which i dont mind. also i dont know what kernal vershion i have.

Also on the 2nd bit, it talks about debugging tools. It says i need to run "make debug". which /dir do i need to be in to do this, and what is the command i need to type in? 

it also says "you may get some
error messages while compiling menudbg. You can ignore it and get apdbg only" What does apdbg only mean?

i tried opening the network interface by typing "ifconfig ethX" btu i get:

ethX: error fetching interface information: Device not found
toby@linuxlap:~/software/drivers/ZD1211LnxDrv_2_2_0_0$


Thanks :)

---

### Post by SendDerek on 2006-10-22
Sorry man, but this is where my knowledge just falls off a cliff.

This is where the veterans will have to jump in and help out.

The only other thing that I can think of is using ndiswrapper to install the windows version drivers.  It might be easier?  I have no clue.

I did, however, find out how to check your kernal version:
```

uname -r 

```

---

### Post by kewldude606 on 2006-10-22
First, do the uname -r.  The first 3 characters are the kernel number (2.4 or 2.6)

Now, check in the src/ directory, see if there is a file called makefile.ini or makefile.in.  edit this file (copy everything off the CD first) and uncomment the right lines by adding or removing #'s from the beginning of the line.  If you have 2.4 kernel, it should look like this:
```
# if the kernel is 2.6.x, turn on this
#KERN_26=y
#KERNEL_SOURCE=/usr/src/linux-2.6.7
# if the kernel is 2.4.x, turn on this
KERN_24=y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8
```
If you have 2.6, it should look like this:
```
# if the kernel is 2.6.x, turn on this
KERN_26=y
KERNEL_SOURCE=/usr/src/linux-2.6.7
# if the kernel is 2.4.x, turn on this
# KERN_24=y
# KERNEL_SOURCE=/usr/src/linux-2.4.20-8
```

Now, for the KERNEL_SOURCE.  You want to run uname -r again, let's say you get the result 2.6.15-27-386.  Change the line KERNEL_SOURCE=/usr... to this:
[code]
KERNEL_SOURCE=/usr/src/linux-headers-2.6.15-27-386

Then, run ./configure in the /src/ directory.

---


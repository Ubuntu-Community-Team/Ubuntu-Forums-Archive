---
title: "Trying to install VMWare"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Cursetheman on 2007-01-24
Ok i'm trying to installl VMWare sever, my main gole is to get XP on my UBUNTU w/o useing dual-boot....

so i'm going along and doing just fin untill...

> Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Setup is unable to find the "gcc" program on your machine.  Please make sure it
is installed.  Do you want to specify the location of this program by hand?
[yes] no

Using compiler "". Use environment variable CC to override.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

witch is right after i type the code > sudo ./vmware-install.pl


i also can get the line of code....

> sudo apt-get install linux-headers-`uname -r` build-essential xinetd

to work... (From the start of the install) I've been useing [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) as my guide so if i'm doign some thing wrong please help.... and if u knwo what i can do to make it work PLEASE PLEASE!!! help


Thxx

---

### Post by mandrakethepenguin on 2007-01-24
Seems like it can't find the C compiler (GCC).  Run this command to see if it is there. ```
$ whereis gcc
``` If and when the vmware-install script says >  Setup is unable to find the "gcc" program on your machine.  Please make sure it
is installed.  Do you want to specify the location of this program by hand?
[yes] type yes, and enter the output of the whereis command. It should be in /usr/bin/gcc.

---

### Post by Cursetheman on 2007-01-24
i get 
> /usr/lib/gcc
plug that in....
> What is the location of the "gcc" program on your machine? usr/lib/gcc

The answer "usr/lib/gcc" is invalid.  It must be the complete name of a binary
file.

What is the location of the "gcc" program on your machine?

what more do i need to add????

---

### Post by dimeotane on 2007-01-24
dude, don't waste your time with VMware...  it's commercial and difficult to set up.   I had windows 2000 running on ubuntu really fast with virtualbox.    No more dual boot!

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by hscottyh on 2007-01-24
If I went with Vmware... I would use player.
With multiverse enabled:

sudo apt-get install vmware-player

It won't create an image for you to install into but you can get get a custom blank image to your specs form here:
[http://www.easyvmx.com](http://www.easyvmx.com)

I haven't tried Virtualbox yet, but from what I've read. It sounds worth checking out.

---

### Post by Cursetheman on 2007-01-25
Ok so tyring it the VirtualBox way.....

go to the site, go to downloads....

> VirtualBox 1.3.2 for Linux Hosts:

    * Ubuntu 6.10 ("Edgy Eft") (BitTorrent*)
    * Ubuntu 6.06 LTS ("Dapper Drake") (BitTorrent*)
    * Debian 4.0 ("Etch") (BitTorrent*)
    * All distributions (BitTorrent*) 

gogin w/ "all distrbutions" beacuse i tryed all the other's and no luck......

login as root....

run.... 

> # /home/ctm/Desktop# /home/ctm/Desktop/VirtualBox_1.3.2_Linux_x86.run install

and get this....

> root@CTM-UBUNTU:/home/ctm/Desktop# /home/ctm/Desktop/VirtualBox_1.3.2_Linux_x86.run install
Verifying archive integrity... All good.
Uncompressing VirtualBox for Linux installation.....
VirtualBox Version 1.3.2 (Sun Jan 14 15:25:08 CET 2007) installation
The VirtualBox installer needs GNU make to be installed.
Please install the header files for your current Linux kernel.
The VirtualBox installer needs the GNU compiler to be installed.
Problems were found which would prevent VirtualBox from installing.
Please correct these problems and try again.

thx for the help thus far plaese what do i do now

---

### Post by Bachstelze on 2007-01-25
Those programs need specific kernel modules to run. To build those modules, they require a C compiler and the C headers matching your current running kernel. To install this, run

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

VMware server also requires *xinetd*, *libdb2* and *libgnome2-perl*, which you can install the same way.

---

### Post by lamego on 2007-01-25
> dude, don't waste your time with VMware... it's commercial and difficult to set up. I had windows 2000 running on ubuntu really fast with virtualbox. No more dual boot!
The virtualbox version which is available to install as .deb is also comercial...

Does virtualbox performs as good as vmware ?

---

### Post by webdr on 2007-01-25
I haven't had time to create consise howto, however, I have been able to install virtualbox for both edgy and dapper. With Dapper make sure that uname -r ends in 686 and if not in synaptic install linux-686 (if appropriate for your processor).

I have to run for now, but will try to make time today to put a clear written set of steps for bot h edgy and dapper.
:D

---

### Post by hscottyh on 2007-01-25
The one good thing about vmware-player is that when you get a new kernel update you get an updated kernel module for vmware as well, since it's maintained in the repository.

---

### Post by hyper_ch on 2007-01-25
But with the player you can't create images right?

Here's what you need as dependencies for vmware server:

```

sudo apt-get install linux-headers-`uname -r` build-essential xinetd gcc-3.4

```

Once you have that, run the vmware install perl script:

```

sudo perl vmware-install.pl

```

and you are set

---

### Post by hscottyh on 2007-01-25
> **sjau said:**
> But with the player you can't create images right?


You can't with the player, but this website will create one for you.
[http://easyvmx.com/](http://easyvmx.com/)

---

### Post by Jussi01 on 2007-01-25
> **lamego said:**
> The virtualbox version which is available to install as .deb is also comercial...

Does virtualbox performs as good as vmware ?

IMHO, virtualbox performs much faster than vmware. TO ME, it seems a far superior product, it is also easier to use and install. (it has a deb available.) The only thing I had with it was it only worked the first time after restarting my system... usually I dont have to do that when installing stuff on ubuntu.

HTH

---

### Post by hyper_ch on 2007-01-25
Just tried virtualbox... didn't work... even after restart... some strange error... and the deb is gone again

---

### Post by Cursetheman on 2007-01-25
ok now i get VirtualBox installed... i make a VM ... i start it up and get....

> 
VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}




ok i'm soooooooo close i can tastet it... and i hope there's a ezy way to fix it sp o please help

---

### Post by hyper_ch on 2007-01-25
that's the error I also got... so I'm back to vmware

---

### Post by Cursetheman on 2007-01-26
ok i got it to work if u have the same problem go to this page ([http://ubuntuforums.org/showthread.php?p=2067812#post2067812](http://ubuntuforums.org/showthread.php?p=2067812#post2067812)) 
and read what Moulton had to say about it....
(This is for VirtualBox)
this is what he posted

Moulton:

> 

Try this...

```
sudo depmod 
sudo /etc/init.d/virtualbox start 
sudo chmod 666 /dev/vboxdrv
```

Then launch VirtualBox.

---

### Post by gentlemanmasher on 2007-01-26
The only way I could get VMWARE to work was with the generic Kernal are you using that?

---

### Post by saadakhtar on 2007-01-26
i ran into the same problem and then figured out the solution to my problem after some investigation. Actually i did a kernel update on my server recently but did not update the kernel headers. Actually i messed with the vmware config and then every time i wanted to start vmware i got a message that i needed to reconfigure vmware.
the simple solution:

Command to update kernel headers

sudo apt-get install linux-headers-`uname -r`

additionally you need to make sure that the kernel headers update everytime you run a update. for this you will need to run a program called linux-headers-***.
*** is the package flavor that you are using.
please run uname -r to find out what flavor you are using.
It will give you something like 2.6.15-26-k7 or 2.6.15-26-686

Now that you know your linux flavor please run this command:
sudo apt-get install linux-headers-***
Replace the *** with 386, 686, k7 or server.

Hope this helps.


If you need to install VMWARE from scratch then please check [this link ]("http://www.howtoforge.com/ubuntu_vmware_server")out.

Please post if you have any questions. i think i have done enough research on this topic to answer some basic questions. Here to HELP.

---


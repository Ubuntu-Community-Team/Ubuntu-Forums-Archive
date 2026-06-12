---
title: "Help with USB wireless adapter install"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by noMS4me on 2008-02-23
Greetings All!

I have been trying to install drivers on a desktop running Ubuntu 7.10 for a Pluscom WU-ZD1211B Wireless USB Adapter with no success but with quite a bit of education.

Can someone please lead me by the hand on this one because at this point I am pretty much lost... Thanks!!! Steve

These are the instuctions (which might as well be in another language) and I have the drivers on a cd: (I have not been able to figure out how to access to even begin to extract file) :confused:

Driver Installation Guide for ZD1211 wireless adapter in Linux
It needs only a few steps to build and install the driver we provided. Before you begin tobuild the driver, make sure (1) Kernel Source Tree is installed in your Linux system;(2) Kernel wireless function (IEEE 802.11) is available.

Step 1: Package Extraction
Type this command: tar zxvf ZD1211LnxDrv_2_21_0_0.tar.gz
The purpose of this step is to extract this package by tar. After extracting this package,
you can see the source files. You should change directory into this directory for
proceeding the next step.

Step 2: Compile the driver
You just need to type the command “make”, and the driver module will be generated and
installed.

Step 3: Load the driver
Use the command “modprobe –i zd1211b” to load the driver. In order to check whether
the driver is loaded successfully, you can use the command “lsmod” for this check. If the
driver is loaded successfully, the following messages should be seen
...
zd1211 183576 0 (unused)
...
Please note that the number 183576 may vary in different systems.

Step 4: Configure the Wireless settings
Use the command “ifconfig” command to check the configurations, you can find ethX(If there is already an Ethernet adapter exits it may be eth0,and the adapteryou just installed may be eth1 ,and so on). Then type in the command “iwconfig eth1 essid xxx” where “xxx” is the SSID of your router. The adapter will connect the router automatically. Of course, make sure the router’s DHCP is enabled, Otherwise,
you should set the IP address of the adapter manually.

---

### Post by dcstar on 2008-02-23
> **noMS4me said:**
> Greetings All!

I have been trying to install drivers on a desktop running Ubuntu 7.10 for a Pluscom WU-ZD1211B Wireless USB Adapter with no success but with quite a bit of education.

Can someone please lead me by the hand on this one because at this point I am pretty much lost... Thanks!!! Steve

These are the instuctions (which might as well be in another language) and I have the drivers on a cd: (I have not been able to figure out how to access to even begin to extract file) :confused:
.........

There are two options (probably) available to you, the Linux compile option where you will need to install the **build-essential** and the** linux-headers** packages for your system, then those instructions should work.

The second option is to install the **ndisgtk** package and use it to install Windows drivers for your device.

You should be able to find detailed instructions on both these options by doing a forum search with the appropriate terms.

---

### Post by bwhite82 on 2008-02-23
1) Open a terminal and type:
> 
uname -r


2) Open Synaptic (System>Administration>Synaptic Package Manager). Click search button, type in 'linux-headers' (minus quotes). Install the corresponding package referring to your currently installed kernel version -- see the terminal window you opened. Do the same for 'linux-source'.

3) Find out where you downloaded the driver package to. (Usually either desktop or your home folder). Once located, go back to the terminal window and cd to the directory, example:
> 
cd ~/Desktop

> ls

You should be see your downloaded package after typing 'ls'.

4) Untar the package. You can either type out the full name (lame) or you can use a shortcut such as TAB completion or a wildcard, example:
> 
tar zxvf ZD12*

TAB completion works by simply beginning to type the package's name, then hitting TAB, and the rest will automagically complete. Give it a try.

5) After you have extracted the compressed file, it will have created a new directory, usually with the same name as the downloaded package. Do another:

> ls

...to see it there. Then CD to it:

> cd ZD12*

6) Once in the correct directory, type the command:
> 
make

7) Your instructions didn't say to do so, but generally, that command is followed by this command:

> sudo make install

It may or may not work, either way, proceed to the next step.

8 ) Load the driver:

> sudo modprobe &#8211;i zd1211b

To verify that it is loaded:

> lsmod | grep zd12

9) Use the command-line method to connect to your network, as given with your instructions, or use Network Manager.

-Cheers

---

### Post by noMS4me on 2008-02-24
Thank you for your time. it is people like yourself that will make Ubuntu.

Steve

---

### Post by neilblue on 2008-04-21
Hi,

Did you get this to work in the end? I have compiled and loaded the mod, but wiconfig shows no wifi devices?

Cheers
Neil

---


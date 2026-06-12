---
title: "help with dell truemobile 1300"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by PNP on 2007-05-18
I know this has been covered, asked, and addressed a million times, but everything I've found about it can't walk a completely Linux-ignorant person through.

I am completely a beginner when it comes to Linux, but I was super excited to install Ubuntu today on my laptop.  I had winxp on it and just decided to take the plunge.
I have a Dell latitude D600, Pentium M 1.6

After my install, I discovered the problem with the Broadcom wireless cards.
In fact, my computer also has a broadcom ethernet card that is not working.

On my desktop (win2k) i downloaded the driver for the truemobile and transferred it to my Ubuntu desktop (both .inf and .sys files)

I downloaded ndiswrapper-1.44 and transferred it to my Ubuntu desktop and extracted it to the desktop as well.

I cannot get it to install ndiswrapper though.

I type: cd /Desktop/ndiswrapper-1.44 and get the directory
then:
make distclean

it does a bunch of stuff
then:
make

it does more stuff (but everything it does seems to end in error) .
Bottom line is that I have no idea how to install anything in linux and I am super frustrated.

I've read wikis and tutorials and instructions... i've tried to install ndisgtk (but cant get it to work)

At this point I don't know what to do, everything i've seen seems to assume that I have some linux experience.

Can anyone really walk me step by step through a total dummies explaination on how I can get my wireless (and my wired) connection working?

I really tinkered alot today and hope that I didn't mess anything up.  If necessary I can reinstall Ubuntu though.

**I should note that part of the reason that I chose now to install is because all of a sudden my wired connection stopped working... while Windows could see the device, it could no longer operate... like perhaps the driver wasn't there or something... maybe I have a bad ethernet card, but I know that my wireless is good**

Thanks in advance.

---

### Post by dstew on 2007-05-18
Let's help you install ndiswrapper first, since it sounds like you got stuck there.  Apparently you are trying to install the ndiswrapper utility by compiling from source code. That is hard to do for new users, but it can be done. Another way to install ndiswrapper is through the Synaptic package manager, but if you don't have internet on your Linux install, you might not be able to do it that way.

Probably the easiest way for you is to download a Debian package of ndiswrapper, and install that. A Debian package contains the already compiled, binary version of the ndiswrapper code, and the Linux installation has the **dpkg** program that will automatically install the program for you. However, the latest Debian package I could find for ndiswrapper was version 1.1. It is [here]("http://packages.debian.org/testing/misc/ndiswrapper-utils-1.1") if you want to take a look at it. So you have to decide if you want to compile your ndiswrapper version 1.44 from the source code which you already have, or get the Debian package of version 1.1. Either way, there are difficulties that you will need to overcome. You will have to install the proper compiling tools for the 1.44 way, and you will have to install programs on which ndiswrapper depends in either way. Once you have internet access, Synaptic will take care of all of these for you.

So, which way do you want to go? Cheers.

---

### Post by PNP on 2007-05-18
First... thank you for your help.

Either way works for me... I want to do what is easiest.
I don't mind using 1.1 if it supports my wireless card.

Do I still need Synaptic?
What about the Debian?
Can I download to a jumpdrive and then transfer?

---

### Post by dstew on 2007-05-18
I think going with Debian packages is a good way to start. You would probably have to install some packages to get your compiling-from-source to work anyway. (Usually you need to install the packages build-essential, kernel-headers for your particular kernel, and maybe module-assistant in order to compile from source).

First, download the ubuntu ndiswrapper debian package from [here]("http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9"). This is a more up-to-date package I found on the list of Ubuntu Debian packages for Feisty. (You do have Feisty installed, right? If it's another version, there are packages for those as well). Notice on the download page that the packages on which ndiswrapper depends are also listed, with links for down loading. They are libc6, ndiswrapper-common, and perl. I think perl may already be installed, but go ahead and download the other packages anyway to have them ready in case you need them. Put the downloaded files on your desktop. They should all end with the .deb extension.

To install a .deb package from the graphical user interface, I believe you can right-click it. Or, from the terminal, enter the command:```
sudo dpkg -i ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
```or whatever the file name of the package is. Copy the output from the terminal command if there are any errors, and post it to the forum. Once you think you have ndiswrapper installed, we can try to use it to install the wireless card drivers.

---

### Post by PNP on 2007-05-18
Ok...
so I had a group meeting with a friend that uses PC linux this morning.
He helped me get the diswrapper 1.1 installed.
but couldn't get the driver to work.

I just downloaded the 1.38 and installed it.

Do I need to uninstall the 1.1 or is it ok?

Now for the driver...

---

### Post by dstew on 2007-05-18
I think the Debian installer will remove the previous version. Now you have to install the drivers. You have the driver .inf and .sys files, right? If so, change to the directory containing the driver files, and do```
sudo ndiswrapper -i *driver_file*.inf
```Of course, substitute the correct name for driver_file. If you get no error messages, make sure that ndiswrapper installed the drivers by entering```
sudo ndiswrapper -l
```You should get the answer something like "driver installed, hardware present". Finally, enter```
sudo modprobe ndiswrapper
```to add ndiswrapper to the modules that will be run at startup. If all this goes ok, we will then have to configure the wireless LAN card.

One more thing: if you had a driver for the card installed previously, you might have to blacklist it before you install the ndiswrapper driver. See the section on blacklisting on [this page]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/").

---

### Post by PNP on 2007-05-18
looks good.
I did not have any previous drivers.

anyway, 

sudo modprobe ndiswrapper

did not do anything that i can tell.

so now the driver is installed, how do i configure it?

also, do i do anything with the sys file?
and can i delete these from the desktop?

---

### Post by dstew on 2007-05-19
The .inf file contains instructions to install the .sys file. I do not know if it is ok to delete them, but you can move them, reboot, and see if the driver is still working. If it didn't hurt to move them, it is probably ok to delete them.
To configure your wireless network, you need to use the network tools. There is a graphical tool accessible from the menu (System --> Administration --> Networking), or you can use command-line tools. The **iwconfig** command comes to mind. The command-line tools come with built-in user manuals called man pages. You can look at man pages in the terminal using the command **man**. For example, to see the man page for iwconfig enter:```
man iwconfig
```For more help configuring your wireless, there are lots of web forum pages and sites that can help you. [Here]("http://ccsd.msoe.edu/faq/linux/Ubuntu.jsp?IDFaq=223") is a nice one for Feisty with some screen shots.

---

### Post by PNP on 2007-05-19
thanks dstew for all of your help but...

When I do:
ndiswrapper -l

it says:
bcmwl5: driver installed
device (14E4:4320) present (alternate driver: bcm43xx)

I still cannot get a signal though.
Am I missing something?

---

### Post by chamberlain2006 on 2007-05-19
You must blacklist the native bcm43xx driver.  Edit /etc/modprobe.d/blacklist and add blacklist bcm43xx to the end, and reboot.

---

### Post by PNP on 2007-05-19
i got into blacklist but how do i "add it to the end?"

---

### Post by chamberlain2006 on 2007-05-19
Type "blacklist bcm43xx" at the end of the file.

---

### Post by PNP on 2007-05-19
sorry...
I also get:

bash: Edit: command not found

---

### Post by PNP on 2007-05-19
before i used 'nano' instead of 'edit'

---

### Post by chamberlain2006 on 2007-05-19
Yes, you still have to do so, do 
```
sudo nano /etc/modprobe.d/blacklist
```
to edit the file.

---

### Post by PNP on 2007-05-19
Ok... so i did
sudo nano /etc/modprobe.d/blacklist

and went to the bottom and i typed blacklist bcm43xx

is there a way to save it? it doesnt seem like its actually edited

---

### Post by PNP on 2007-05-19
another update...
i hit ctrl x to exit
and hit save 
now it says, "file name to write: /etc/modprove.d/blacklist/
and gives options of: 
get help
to files
mac format
prepend
cancel
dos format
append
backup file

Which do i do?

---

### Post by PNP on 2007-05-19
ugh....
so i got it blacklisted (i think... since when i bring up the blacklist it is still there), restarted, and now my wireless card doesnt even seem like it is recognized.

Before, it said showed up in the network settings and said "this network interface is not configured"

Now it doesn't even show the wireless... only a modem.

---

### Post by chamberlain2006 on 2007-05-20
Have you finished the steps to do with ndiswrapper?  It was recognized using the module we blacklisted.  Now we want to use ndiswrapper.  You have to finish whatever tutorial you were following.

---

### Post by PNP on 2007-05-20
thats the problem...

I did sudo ndiswrapper -i bcmwl5.inf

and then

sudo modprobe ndiswrapper

and nothing has happened.

---

### Post by PNP on 2007-05-20
bumped for help...
please? anyone?

---

### Post by dstew on 2007-05-20
What is the output of```
sudo ndiswrapper -l
```

---

### Post by PNP on 2007-05-20
dstew... thank you for all of your help.
I did figure it out on my own but only after all of your assistance.

---

### Post by Mischief on 2007-06-28
I've got the same problem as you had with the same card.

Would you mind telling me what you did, been struggling with this since I upgraded to 7.04.

Thanks!

---


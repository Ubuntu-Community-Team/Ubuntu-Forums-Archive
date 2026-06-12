---
title: "vmware BIG PROBLEM"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-06
ok, i really messed up this time.. i tried to install vmware but it gave an error during the installation (maybe because i wasn't root at that time).. and after this was when i messed up BIG TIME. 

i deleted the folder where it installed with sudo su and nautilus. now, when i tried to install vmware again it said this:


> A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/maranhao/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

root@maranhao-desktop:/home/maranhao/tmp/vmware-server-distrib#


what should i do to uninstall it so i can install it again?

---

### Post by gn2 on 2006-10-06
Log in as Super-user, search for vmware packages with Synaptic Package Manager, and mark them for removal.

That should do the trick.

---

### Post by cmaranhao on 2006-10-06
how do i log as super user?

edit: after logging the usual way, the only package is this:

xserver-xorg-driver-vmware

decriptions is :

> X.Org X server -- VMware display driver
This package provides the driver for VMware client sessions, i.e. if Linux
is running inside a VMware session.

More information about X.Org can be found at:
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This module can be found as the module 'driver/xf86-video-vmware' at
:pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

shoul i mark this for complete removal?

---

### Post by cmaranhao on 2006-10-06
i uninstalled that file and tried to install vmware again, the same error appears:

> root@maranhao-desktop:/home/maranhao/tmp/vmware-server-distrib# sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/maranhao/vmware/vmware-uninstall.pl.

Failure

Execution aborted.

what should i do?

---

### Post by gn2 on 2006-10-06
Search for all vmware files and delete them.

You can probably leave the video driver installed.

When you installed Ubuntu did you have just one user or two?

Usually the first user set up is the super user account, which has full administrative priviledges.

Log in as this user, then download the linux .rpm file from this link: [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) 

Click on the download button, scroll down, accept the eula, and a list of downloads will be shown.

You want the .rpm file.

Then install "yum" with Synaptic. Yum should be able to open and install the .rpm for you.

This is how I did it with PCLinuxOS and kPackage Manager.

---

### Post by AndyCooll on 2006-10-06
This error message is caused by a previous failed installation, not your latest attempt at installation. It's actually fairly staright forward to overcome for you simply need to delete a couple of offending files.

Unfortunately I'm at work right now and don't have my notes to hand to give you the relevent instructions. When I get home (in a couple of hours) I'll update this post for you.

Hang in there!

:cool:

---

### Post by distroman on 2006-10-06
Not sure if this will help you now, but you could try.

Look in /usr/bin if vmware-uninstall.pl is there then 
```
sudo ./vmware-uninstall.pl
```  

Or maybe this will do it. 

> * Uninstallation failed and reinstall won't work
      ====
      A previous installation of VMware software has been detected.
      The previous installation was made by the tar installer (version 3).
      Keeping the tar3 installer database format.
      Error: Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.
      Failure
      Execution aborted.
      ====

Look for the /etc/vmware directory and either move it to a different location or remove it altogether.
      
```
sudo rm -R /etc/vmware
```

---

### Post by cmaranhao on 2006-10-06
i searched for vmware files.. i had like 5 or 6 in my pc..

i opened terminal, typed

 sudo su to be root

nautilus and deleted all the files by hand.. i will restart my pc and see if anything wrong happens :???:

---

### Post by cmaranhao on 2006-10-06
nothing bad happened but when i try to install vmware again it gives me the same message

edit:

> sudo ./vmware-install.pl

this worked, thanks :)

---

### Post by cmaranhao on 2006-10-06
can anyone give me the answer to this question?

> What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]


---

### Post by NetworkGuy on 2006-10-06
Press Enter.

My experience with VMware is that you shouldn't have to change any of the defaults to get it installed and working.

---

### Post by cmaranhao on 2006-10-06
i completed the installation (finally)

but i'm not set yet ](*,) 

this error appeared:

> Starting VMware services:
   Virtual machine monitor                                             done

The configuration of VMware Server 1.0.1 build-29996 for Linux for this running
kernel completed successfully.

root@maranhao-desktop:/home/maranhao/tmp/vmware-server-distrib# vmware
bash: vmware: command not found


edit: i forgot to reboot, hopefully it will work this time

---

### Post by bulldog on 2006-10-06
The only thing that you better change,is the location where your virtual machines will be placed.

I put mine in my /home/vmware.

Otherwise keep entering all the questions and don't change a thing,only if you know what you're doing you can change the options.

And no offence,but I have not the impression you do.:D

You run the program without sudo,just as a user.

---

### Post by cmaranhao on 2006-10-06
after rebooting, i went into applications, system tools, vmware server console. this error appears:

> Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)

](*,)

---

### Post by bulldog on 2006-10-06
Try ```
sudo /usr/bin/vmware-config.pl
```

---

### Post by cmaranhao on 2006-10-06
> maranhao@maranhao-desktop:~$ sudo /usr/bin/vmware-config.pl
sudo: /usr/bin/vmware-config.pl: command not found


it didn't worked

---

### Post by bulldog on 2006-10-06
I found installing vnware one of the easiest things to do.

Just download and click it,choose unpack here and go to the created folder.
Run 'sudo ./vmware-install.pl' answer all yes exept the place for your vmware machines and your done.

Did you ```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

Use this tutorial and all should work well,don't mix two howto's just follow one!!

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by cmaranhao on 2006-10-06
> **bulldog said:**
> I found installing vnware one of the easiest things to do.

Just download and click it,choose unpack here and go to the created folder.
Run 'sudo ./vmware-install.pl' answer all yes exept the place for your vmware machines and your done.

i just did that and vmware don't run.. why should i "re-install it"??? 

> sudo apt-get install linux-headers-`uname -r` build-essential xinetd

i've done that before (everytime i tried to install vmware)...:???: shall i do that everytime i install vmware?

because it won't install nothing new, it says this:

> maranhao@maranhao-desktop:~$ sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-27-386 is already the newest version.
build-essential is already the newest version.
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
maranhao@maranhao-desktop:~$

like i said it gives this error if i try to run it through applications menu

> Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)

in terminal it gives me this:

> maranhao@maranhao-desktop:~$ vmware
bash: vmware: command not found


---

### Post by bulldog on 2006-10-06
See my previous post.

When you install it does everything for you,you only need to provide the password and enter all the questions without altering.

When you didn't get an error it should be installed fine.

You should have had an error message because it's not installed properly.

I did the install twice without any problems and run twice the config.pl because I had new kernels installed.

Never had any trouble running vmware or my virtual machines.

You must have overlooked something.

---

### Post by cmaranhao on 2006-10-06
ok, finally vmware works.. i searched in the directory where vmare was installed and i discovered the "vmware.exe" lol

then i created a new link for applications but i have another problem

everytime i open this link it goes to vmware server console. then i must press connect and then i must choose the virtual machine i created. only after these steps i can power it on.

i know that there is a way to go directly to the "power on this virtual machine" menu but i don't know how. can anyone help me?

---

### Post by AndyCooll on 2006-10-06
> **cmaranhao said:**
> ok, finally vmware works.. i searched in the directory where vmare was installed and i discovered the "vmware.exe" lol

then i created a new link for applications but i have another problem

everytime i open this link it goes to vmware server console. then i must press connect and then i must choose the virtual machine i created. only after these steps i can power it on.

i know that there is a way to go directly to the "power on this virtual machine" menu but i don't know how. can anyone help me?

As far as I'm aware these steps are normal, since you are getting the option to connect locally or to a remote host (which you probably won't use, but nonetheless it's an option). It's certainly what I do each time.

The straight "power on" option is when you use Player I think.

:cool: 

PS. Well done for your perseverence and not giving up in order to get to this point!

---

### Post by cmaranhao on 2006-10-06
thanks for the clarification andy 8) 

another thing.. when we start windows in vmware for the first time, we should see a vmware tools icon near the clock right? i didn't had that icon..

---

### Post by TFX360 on 2007-11-01
Thanks, needed that for removal of vmware-tools.


Bye,


TFX360

---


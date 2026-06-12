---
title: "Ubuntu 6.06 and installing VMWare Tools"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by mule52 on 2006-07-17
I cannot, for the life of me, install VMWare Tools for my Ubuntu 6.06 in VMWare Workstation 5.5.

I can get to the point where I have installed enough to then have to configure vmware tools by invoking the vmware-config-tools.pl. This is where it fails.

Here are my latest errors.

mule52@mule52-desktop:~$ sudo /usr/bin/vmware-config-tools.pl
sh: /usr/sbin/vmware-checkvm: No such file or directory
sh: /usr/sbin/vmware-checkvm: No such file or directory
sh: /usr/sbin/vmware-checkvm: No such file or directory
This configuration program is to be executed in a virtual machine.

Execution aborted.

I have tried creating that folder and file, but nothing works. Any ideas? Thanks.

---

### Post by jorn on 2006-07-17
I've installed the vmware server because I'd trouble configuring the Workstation version. Not said that it should't work for you.

When you have reached to the point where you are now there should be a config somwhere. Maybe it has got a slightly different name.
Have you been looking in /usr/bin/ for the vmware-config file?

I used this guide:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

> This configuration program is to be executed in a virtual machine.
Have you read this?
The vmware-tools are to be installed after you have set up your virtual mashine.
I think you havn't finished the installation of vmwware. Am I right?

Else:
> 
You will definately want to install the VMWare tools, when windows has been installed. This will speed up your Windows responsiveness

    * Make sure your Windows Virtual Machine is Running and visable/selected. (Not in FullScreen)
    * Go to the VM menu (on the top in the VM Server Console)
    * Select Install VMWare Tools.
      This will start a installation wizard in your WIndows Environment. Just install the stuff and you will have better mouse and system responsiveness.

---

### Post by mule52 on 2006-07-18
I am currently installing VMWare Tools inside a live virtual machine session. Here are my exact steps to reproduce the errors. 

After mounting the CD-rom of the VMWare Tools, I extract them to my /tmp directory. I then run the install file. Please help me troubleshoot this. Thanks!

In a terminal, I have the following. See my latest error (roadblock) at the end.

mule52@mule52-desktop:~$ sudo /home/mule52/Desktop/vmware-tools-distrib/vmware-install.pl Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin] /usr/bin

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc] /etc

What is the directory that contains the init scripts?
[/etc/init.d] /etc/init.d

In which directory do you want to install the daemon files?
[/usr/sbin] /usr/sbin

In which directory do you want to install the library files?
[/usr/lib/vmware-tools] /usr/lib/vmware-tools

The path "/usr/lib/vmware-tools" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes] yes

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware-tools] /usr/share/doc/vmware-tools

sh: /usr/lib/vmware-tools/sbin32/vmware-guestd: No such file or directory
The installation of VMware Tools 5.5.1 build-19175 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config-tools.pl"

Enjoy,

--the VMware team

mule52@mule52-desktop:~$ sudo /usr/bin/vmware-config-tools.pl
sh: /usr/sbin/vmware-checkvm: No such file or directory
sh: /usr/sbin/vmware-checkvm: No such file or directory
sh: /usr/sbin/vmware-checkvm: No such file or directory
This configuration program is to be executed in a virtual machine.

Execution aborted.

---

### Post by digby on 2006-07-18
Just to confirm: you are running some other os and using ubuntu through vmware?

If so installing vmware tools should be as simple as selecting the VM menu (in vmware) and clicking 'Install VMWare Tools.'

---

### Post by mule52 on 2006-07-18
Yes, I am running XP Pro as my host OS, and installing Ubuntu 6.06 inside VMWare. You are correct, "installing vmware tools should be as simple as selecting the VM menu (in vmware) and clicking 'Install VMWare Tools,'" however, it is not. I absolutely agree that it should be as simple as the Windows OS's make it. At this point, I am still stuck.

---

### Post by acidjames on 2006-07-28
Hi,

this is the solution to run vmware tools with dapper 606 on a win xp host :

>    1. Start up a terminal window and do the following:

      sudo bash
      apt-get install build-essential
      apt-get install linux-headers-`uname -r`

   2. Get the patch text from here and drop it into /tmp/patch.txt.

      [Update: changed the link to a locally cached copy, since the original source seems to be down]
   3. Get the vmware-tools-any update by doing this:

      cd /tmp
      wget [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-tools-any-update2.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-tools-any-update2.tar.gz)
      tar xzf vmware-tools-any-update2.tar.gz

   4. From vmware menu, choose vm->install vmware tools - you should see a mounted CD image show up on the desktop. Back in your terminal window, do the following:

      cd /tmp
      tar xzvf /cdrom/VMwareTools*.tar.gz
      cd vmware-tools-distrib/
      ./vmware-install.pl

      During vmware-install.pl, I chose the default answers to everything but at the end did not choose to launch vmware-config-tools.pl.
   5. Then do this in your terminal:

      cd /tmp/vmware-tools-any-update2/
      ./runme.pl

      Again, choose to not run vmware-config-tools.pl yet

      cd /usr/bin
      patch vmware-config-tools.pl /tmp/patch.txt
      ./vmware-config-tools.pl

   6. Lastly, you can edit your config to use the vmware mouse:

      perl -p -i.bak -e 's/\"mouse\"/\"vmmouse\"/' /etc/X11/xorg.conf


all files specified here are mirrored on [http://paradiz.free.fr/vmwaretools/](http://paradiz.free.fr/vmwaretools/) official post [http://asargent.com/blog/archives/35](http://asargent.com/blog/archives/35)

here is a screenshot attached

---

### Post by acidjames on 2006-10-15
Hello, just to say if anyone is still into this stuff,

last update VMWare Tools for VMWare 5.5.2 has XORG 7 support without any mods or patches

---

### Post by baronne on 2006-10-16
I was having much the same difficulty but here's something that really worked for me...
I used a package I grabbed from the Synaptic Package Manager called Alien which converts an RPM to a Debian package.
I then ran sudo alien -c VMWARETools-5.5.2-29772.i386.rpm
it generated a vmwaretools_5.5.2-29773_i386.deb file which I ran and it all installed ok...
ran the vmware-config-tools.pl which worked.
so..dunno.. I am a Windows user dabbling with the ol' dapper. so far I am finding my adventures in Linux/Ubuntu fun, but not that simple.
good luck! see you on the other side.
baz

---


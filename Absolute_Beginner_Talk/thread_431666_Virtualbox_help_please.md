---
title: "Virtualbox help please"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-05-03
I have installed and set up virtualbox, but I would like to know if I can run the software that is still on my windows hard drive, thats if it still works as I haven't booted it up for such a long time now.

Basically I just wanna use DW MX 2004 and Photoshop CS2 or would I have to install the dread XP in virtual box??

Cheers
Ian

---

### Post by gh0st on 2007-05-03
I think you'd have to install Windows and then install the software. VirtualBox create and manages virtual machines so they are like a hardware machine with no OS on them when you first create them. You have to add an OS and then install your apps. You could try running those apps through WINE that may well work and you wouldn't have to boot a virtual machine then every time.

You can just install the apps through WINE and run them directly from a shortcut on the desktop like any other Linux app. Not all programs work in WINE and some work better than others. I'm pretty sure the Macromedia stuff works ok but I haven't tried it much. You can find information about it in the WINE application database.

Have a look at the wine website and see what it says about the programs you want to use and how well they work.

[http://www.winehq.com/](http://www.winehq.com/)

There are loads of guides on how to use WINE about but here's one to get you started
[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

You could always install XP on a VirtualBox machine and do it that way as well. It really depends what you want.

Good luck :)

---

### Post by ianb72 on 2007-05-03
Hi
Wine wont run Dreamweaver MX 2004, I have tried in 6.06 and 7.04 with the latest version of wine thats why I was trying Virtual Box

Thanks anyway

Ian

---

### Post by sc30317 on 2007-05-03
Do you run a dual boot machine with 2 different drives?  If so, and it just so happens to be the case that one is windows and one is linux, you can actually virtualize the windows hard drive in linux. This means that you can run your actual windows on your first drive in linux!  Just download Vmware Workstation 6 beta and install.  Make a new virtual machine.  Choose custom for the setup, and use your physical drive as your partition.  This will allow you to use your XP inside linux

---

### Post by ianb72 on 2007-05-03
> **sc30317 said:**
> Do you run a dual boot machine with 2 different drives?  If so, and it just so happens to be the case that one is windows and one is linux, you can actually virtualize the windows hard drive in linux. This means that you can run your actual windows on your first drive in linux!  Just download Vmware Workstation 6 beta and install.  Make a new virtual machine.  Choose custom for the setup, and use your physical drive as your partition.  This will allow you to use your XP inside linux

Hi
Yeah thats my exact setup, I have my XP on my main drive and Ubuntu 6.06 on my second hard drive, this is my main pc

On my second pc, which is the one I use for all the testing purposes just in case things go wrong, I am only running Ubuntu with 1 hard drive.

Ian

---

### Post by gh0st on 2007-05-03
Impressive knowledge there sc30317 :) thats a neat solution. I've never tried that. It sounds like it could be just what's needed. You could work on the same data in both Windows and Ubuntu, thats cool :)

You might wanna check this out as well:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Qemu is supposed to be really fast and it lets you run programs directly without booting a separate VM like WINE. I've heard really good things about it. I use VMware at the moment but I might have to check this out.

---

### Post by ianb72 on 2007-05-03
I'll check that out too, once I have learn't how to get VmWare up and running!! :confused:

---

### Post by gh0st on 2007-05-03
You might wanna check this out for VMware help - [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

If you need anything let me know, good luck :)

---

### Post by Flavian on 2007-05-03
Does anyone have experience with setting up vmware to run the native windows install?
I really want to run my native windows install (I am dualbooting rightnow) in vmware! I installed vmware workstation... but it does not seem to work.
Do I have to do something else??

---

### Post by ianb72 on 2007-05-03
> **gh0st said:**
> You might wanna check this out for VMware help - [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

If you need anything let me know, good luck :)

Thanks for that.

I tried it with the latest version on my main pc with Dapper, everything seemed to go find till this bit
[HTML] ian-m3gxx@ian-m3gxx-desktop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.3 build-44356 for Linux completed
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files?
[/home/ian-m3gxx/vmware]

The path "/home/ian-m3gxx/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] yes]

The answer "yes]" is invalid. It must be one of "y" or "n".

The path "/home/ian-m3gxx/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] y

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/home/ian-m3gxx/sbin]

The path "/home/ian-m3gxx/sbin" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes] y

In which directory do you want to install the library files?
[/home/ian-m3gxx/lib/vmware]

The path "/home/ian-m3gxx/lib/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] y

In which directory do you want to install the manual files?
[/home/ian-m3gxx/man]

The path "/home/ian-m3gxx/man" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes] y

In which directory do you want to install the documentation files?
[/home/ian-m3gxx/doc/vmware]

The path "/home/ian-m3gxx/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] y

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

ian-m3gxx@ian-m3gxx-desktop:~/Desktop/vmware-server-distrib$

[/HTML]

As you can see I have tried again after I got the same error message the first time

Any ideas??

Ian

---

### Post by gh0st on 2007-05-03
Hmm thats a strange one :-k 

I thought I'd seen everything with VMware errors but obviously not. I'll have a look into it and get back to you. It's obviously something to do with permissions but you ran the command with sudo so it should have full access to your file system. Is it possible that some other process is using the file already? What else do you have open as you are running this?

I'll see what I can find out ;)

---

### Post by gh0st on 2007-05-03
After some serious Googling I managed to find this solution for your problem:

```
Unable to get the access rights of source file “./vmware-vix/bin”.

This is a strange error that I saw for the first time today while trying to install the latest build of VMware server.

The fix for it is as follows,

go to $vmwaresetup_dir/bin directory and create a symbolic link to ../bin

```

I check a few other sources and apprently this works, it's seems to be a Dapper specific thing which explains why I don't know about it, I never really used VMware on Dapper ;)

Good luck :)

---

### Post by ianb72 on 2007-05-03
I have sorted it now

I downloaded a previous version and it worked fine, I think there must be a bug or something with the new version :(

---

### Post by gh0st on 2007-05-03
Oh right, that's strange I have the latest version working fine on Feisty, maybe the it doesn't get on with Dapper for some reason. All the posts I saw were about Dapper. 

Anyway, doesn't matter now. Glad to hear you got it sorted :)

---

### Post by Flavian on 2007-05-04
> **Flavian said:**
> Does anyone have experience with setting up vmware to run the native windows install?
I really want to run my native windows install (I am dualbooting rightnow) in vmware! I installed vmware workstation... but it does not seem to work.
Do I have to do something else??

Anyone?

---

### Post by gh0st on 2007-05-04
Sorry Flavian I've never tried that. Might be work starting a separate thread just to try and increase the chance of a reply. Good luck :)

---

### Post by KhaaL on 2007-05-05
> **Flavian said:**
> Anyone?

You need to follow the steps in this one: [http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

Good luck, and let me know how sucessful it was!

---


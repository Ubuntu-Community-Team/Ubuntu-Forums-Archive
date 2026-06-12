---
title: "vmware help"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-05-06
HELP!! i have been trying everything to quit this dualbooting nonsense and stick windows where it belongs in a little window in my linux.  i have tried installing it numerous times...once it gave an error trying to rebuild my kernel(!).  i am running feisty x64 if that makes any differnce.


william@williams-beast:~$ sudo perl vmware-config.pl
Password:
Can't open perl script "vmware-config.pl": No such file or directory
william@williams-beast:~$ sudo perl /usr/bin/vmware-config.pl
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

/usr/share/doc/vmware-player/EULA: No such file or directory

Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

The file /usr/share/mime/packages/vmware.xml that this program was about to 
install already exists.  Overwrite? [yes] y

In which directory do you want to install the mime type icons? 
[/usr/share/icons]

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

The file /usr/share/pixmaps/vmware-player.png that this program was about to 
install already exists.  Overwrite? [yes] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in 
the "/tmp/vmware-config3" directory.

---

### Post by oilchangeguy on 2007-05-06
what's wrong with dual booting? you do understand that if you get it to work, a virtual machine has only a small part of the computers true resources. for example 8gb hard drive, 256mb of ram, etc.

---

### Post by nonewmsgs on 2007-05-06
i have a terrabyte of disk space and 2gb of ram, so i was going to give it 100gb and 768mb etc.  really i just hate having to restart.

---

### Post by Opsidian on 2007-05-07
There seems to be some issue with vmware, I tried out quite a few tips and never got the thing to run myself so I tried something else I saw posted. Virtual Box, [http://www.virtualbox.org/](http://www.virtualbox.org/) Flawless install on two systems and now I can run Microsoft Publisher  without an issue. 

I hear you on the dual booting, it is quite a big pain. Hate to boot into Windows when there are only two programs I haven't been able to replace. I could have replaced them if I was the only person in the organization that uses them but I am stuck with some MS apps because other people use them as well. VirtualBox fills the gap for me.

---

### Post by nonewmsgs on 2007-05-07
excellant! thanks opsidian.  i was trying for hours for vmmware.  i was thinking of just having a seperate box for windows and linux since im going to have 3 towers at my computer desk, but truth be told, the more i dual boot the more i realize i like windows apps, but i HATE windows.  windows seems to have little evil trolls running it.  i have plugged in an external hard drive and gotten told it would run faster with a usb2.0 port, rebooted did the mass copying in ubuntu at normal usb2.0 speeds.  there are so many examples of things like this where before i blamed the hardware or thought it was my fault until i saw all of the ubuntu "just works" attitude towards things.

---

### Post by Opsidian on 2007-05-07
> **nonewmsgs said:**
> excellant! thanks opsidian.  i was trying for hours for vmmware.  i was thinking of just having a seperate box for windows and linux since im going to have 3 towers at my computer desk, but truth be told, the more i dual boot the more i realize i like windows apps, but i HATE windows.  windows seems to have little evil trolls running it.  i have plugged in an external hard drive and gotten told it would run faster with a usb2.0 port, rebooted did the mass copying in ubuntu at normal usb2.0 speeds.  there are so many examples of things like this where before i blamed the hardware or thought it was my fault until i saw all of the ubuntu "just works" attitude towards things.

Glad it worked for you!

---

### Post by nightskywind83 on 2007-05-07
There are other great ways to get Windows apps to work on Linux too.  For example, you could use WINE, or Cedega to run Windows games on Linux.  The advantage here is that you could use all your system resources toward running the windows app rather than putting it in a VM.  

Wine is free, cedega requires at least a 3 month subscription to some magazine or newsletter or something.  I haven't used it yet, but it's come very highly recommended.

---

### Post by brentoboy on 2007-05-08
I've never run the 64bit vmware product.  So I have no opinion on it.

I have noticed that installing from tarball from the vmware site is a bit touchy (expecially with the frequency at which ubuntu releases kernel updates -- which is a good thing).

If it were me, I would uninstall all vmware everything from your computer.  run the uninstall scripts.  delete anything it leaves behind... flush vmware.

Then, I would completely reboot my system.

when it came back, I would install the vmware player in the repos... (it is in the universe repo)

sudo apt-get install vmware-player

(maybe its just vmware and not vmware-player, I forget)

the version in the repos is nicely tested to work on Ubuntu.

---

### Post by meman63 on 2007-05-08
> **nonewmsgs said:**
> i have a terrabyte of disk space and 2gb of ram, so i was going to give it 100gb and 768mb etc.  really i just hate having to restart.
OK.Are you a sys engineer?
Just wondering,because of the amount of resources that you have.

As always,
              Regards,
                         Scott

---

### Post by veloce on 2007-05-08
> **nonewmsgs said:**
> HELP!! i have been trying everything to quit this dualbooting nonsense and stick windows where it belongs in a little window in my linux.  i have tried installing it numerous times...once it gave an error trying to rebuild my kernel(!).  i am running feisty x64 if that makes any differnce.



First, I suggest you use vmware server instead of vmware player.
Second, there are some tricks to get vmware working on 64 bit versions. You need the 32 bit kernel headers to compile the kernel drivers.  Or, you may be able to install the appropriate bits by switching to the 32 bit repositories.

VMware is an excellent way of running windows, don't give up too easily.

---

### Post by gnipper on 2007-05-08
If you install Automatix, it has an option to install Vmware Player. This worked perfectly for me on Xubuntu Fiesty and everything just worked. Not sure if this will work the same on a 64 bit machine but worth a try.

---

### Post by HolyMurderer on 2007-05-10
My VMWare Server only uses GTK, but I want it to use Qt. I use Kubuntu. I've tried as user and as root to change the GTK settings on Kcontrol, but it stays the same... can anybody help me?

I have gtk and gtk2 engines installed.

Thanks

---


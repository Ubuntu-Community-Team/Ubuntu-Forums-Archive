---
title: "How to install downloaded drivers???"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by icecoldstar on 2008-04-06
I downloaded nvidia driver for ubuntu from their website and placed it on USB disk since my ubuntu computer can't get access to internet at this moment, thanks to this infamous SiS191 Ethernet BS
when i clicked on that thing I downloaded, it says root user required. however, i do not know how to get to root user...
any help:confused:

Also, anyone have solution for not working SiS191 Ethernet controller?
Im running 7.10 BTW.

---

### Post by riven0 on 2008-04-06
Go to the terminal, (Applications > Accessories > Terminal), and copy and paste these commands:

1. sudo -s -H

^It'll ask you for your password

2. cd ~/Desktop

^Since I'm guessing you downloaded the file to the desktop

3. ./replace-this-with-whatever-the-filename-is


I'm guessing it's either a bin or .sh file, so the above should work.

---

### Post by neurostu on 2008-04-06
to run a program as root you need to type sudo before a command
example
```

gedit
vs
sudo gedit

```
the second command will open the command as ROOT

So find the file in your terminal then run it with sudo!

---

### Post by Moop on 2008-04-06
You get to be root by typing sudo before the command you want to run. It might help if you use ```
gksudo nautilus
``` and then copy your downloaded driver to the desktop and run the command from there.

---

### Post by neurostu on 2008-04-06
I personally would recommend against using:
```

sudo -s -H

```
Ubuntu has root disabled by default and unless you know what you are doing you should not  go into super-user mode, which the above command does.

all you need to do is add sudo infront of a command to run THAT command as root.

---

### Post by seth556 on 2008-04-06
Easiest is to navigate to where the file is on your hard drive. 

cd Desktop (or whatever folder it's in, or skp this step if it's in your home folder)

Then use the sh command to run it.

sudo sh filename.run 

However if it's a source file the commands will be different. Also if it's a deb file you can just double click the file and click install.

---

### Post by JoshuaRL on 2008-04-06
The problem there is that to run that file appropriately you need to not be running an Xwindow session.  Below is a five-step install of the Nvidia driver.  Make sure you write down this exactly if you don't have a spare computer to read this on while you do it.

**Five Steps to Nvidia Driver Install!**

1).  Reboot the computer and choose Recovery Mode from the GRUB menu.

2).  Move into the Desktop:
```

cd /home/username/Desktop

```
The capitol "D" is important, and "username" is the name of the user that has the file in their desktop.

3).  Find the name of the installer file:
```

ls

```
That's a lowercase L, not a 1.  The file that you downloaded to the Desktop will show up here.  When you use that name in the steps below, make sure you type it exactly.  I'll be using "nvidiainstallerfile.run" as the fake name.

4).  Change permission level of the installer file so it has internet access, and change to runtime level 3:
```

chmod x+ nvidiainstallerfile.run
init 3

```

5).  Run the installer file in a shell:
```

sh nvidiainstallerfile.run

```
Go through all the options, picking the defaults unless you KNOW you need something else.  After that's done, you reboot the computer and the driver should be installed.

Congratulations!

---

### Post by bsharp on 2008-04-06
> **JoshuaRL said:**
> The problem there is that to run that file appropriately you need to not be running an Xwindow session.  Below is a five-step install of the Nvidia driver.  Make sure you write down the

**Five Steps to Nvidia Driver Install!**

1).  Reboot the computer and choose Recovery Mode from the GRUB menu.

2).  Move into the Desktop:
```

cd ~/Desktop

```
(the capitol "D" is important!)

3).  Find the name of the installer file:
```

ls

```
That's a lowercase L, not a 1.  The file that you downloaded to the Desktop will show up here.  When you use that name in the steps below, make sure you type it exactly.  I'll be using "nvidiainstallerfile.run" as the fake name.

4).  Change permission level of the installer file so it has internet access:
```

chmod x+ nvidiainstallerfile.run

```

5).  Run the installer file in a shell:
```

sh nvidiainstallerfile.run

```
Go through all the options, picking the defaults unless you KNOW you need something else.  After that's done, you reboot the computer and the driver should be installed.

Congratulations!

The drivers won't install in a system running in runtime level 1, so add

```
init 3
```

somewhere before the last step.

---

### Post by JoshuaRL on 2008-04-06
I knew I forgot something!  Thanks man, fixed.

---

### Post by d3adp00l on 2008-04-06
ok just for the rest of us, what is ROOT, and why does it need to be done that way.

I assume it means root directory, but I don't like to assume.

---

### Post by bsharp on 2008-04-06
Root is the GOD account, meaning you can do anything that you want to the system.  Certain operations (installing/upgrading software, drivers)  affect the WHOLE system, so special permissions are needed for them to be executed.  

The root directory is just the root user's home directory like your user's directory is /home/{yourusername}

---

### Post by JoshuaRL on 2008-04-06
> **d3adp00l said:**
> ok just for the rest of us, what is ROOT, and why does it need to be done that way.

I assume it means root directory, but I don't like to assume.

You reminded me that my directions to get to the Desktop were wrong.  I just fixed that.

Root is like the admin account in Windows.  It can do anything.  Recovery Mode is text-based root access.

---

### Post by neurostu on 2008-04-06
So for the reasons given in the previous two posts it is highly recommended that you not login to the root account. In other distrobutions of linux you can type 
```
 
su

```
and switch to "super user" mode or become the root user.

This is disabled in ubuntu as it is VERY EASY to permanently damage a system when working in the root account.

So the way to temporarily work as root is with the SUDO command, which with you can do just as much damage as with root access, but not logging into root and using sudo provides an extra level of security.  When you use SUDO you execute a command as root for only 1 command. If you want to run 3 commands as root you have to type sudo before each command.  (However you will only be prompted for your password once, if the commands are typed within a certain temporal window)

SUDO = Super User DO

Also whenever you read a post that says run command "xyz" with sudo (or as root) be very careful and make sure that not only do other people verify that the command is safe, but that ** YOU UNDERSTAND WHAT THE COMMAND MEANS **.  Commands exist that seem harmless and simple that can **COMPLETELY DESTROY** your system.

Use caution whenever you act as root.

---

### Post by iansane on 2008-04-06
don't want to make assumptions but if you are like me, not knowing how to install the driver might mean you don't know how to install the kernel source it asks for so it can compile a kernel interface.

The package is "linux-headers" for your kernel

"uname -a"  in terminal  to see your kernel version.

Since it's been two hours since your post, I assume that you got it working. I have to redo it everytime the kernel updates and I'm running Hardy server AMD64 so I've done it so many times that it's automatic.

For anyone still using gutsy or older, the new version of xserver-xorg has no video options so if you need to use dpkg-reconfigure xserver-xorg to configure your nvidia, you'll have to downgrade unless they see the error in this and put the video options back in

---

### Post by Tatty on 2008-04-06
> **iansane said:**
> don't want to make assumptions but if you are like me, not knowing how to install the driver might mean you don't know how to install the kernel source it asks for so it can compile a kernel interface.

The package is "linux-headers" for your kernel

"uname -a"  in terminal  to see your kernel version.

Since it's been two hours since your post, I assume that you got it working. I have to redo it everytime the kernel updates and I'm running Hardy server AMD64 so I've done it so many times that it's automatic.

For anyone still using gutsy or older, the new version of xserver-xorg has no video options so if you need to use dpkg-reconfigure xserver-xorg to configure your nvidia, you'll have to downgrade unless they see the error in this and put the video options back in

i believe the nvidia driver installer is a binary so there is no compiling needed.  Dont quote me on that though ;)

---

### Post by icecoldstar on 2008-04-07
Thanks to you ALL!!! I will attempt to install my drivers and stuff right after i log off here....
kudos to all!!!

Here is the problem i got...

[IMG]http://i2.photobucket.com/albums/y39/eatpumpkins/Screenshot-3.png[/IMG]

---

### Post by neurostu on 2008-04-07
Press CNTL+ALT+F1 to open a virtual terminal. Login then run the install script from there.

---

### Post by stchman on 2008-04-07
> **icecoldstar said:**
> I downloaded nvidia driver for ubuntu from their website and placed it on USB disk since my ubuntu computer can't get access to internet at this moment, thanks to this infamous SiS191 Ethernet BS
when i clicked on that thing I downloaded, it says root user required. however, i do not know how to get to root user...
any help:confused:

Also, anyone have solution for not working SiS191 Ethernet controller?
Im running 7.10 BTW.

Envy is very nice for installing Nvidia drivers.

Make sure and install the 0.9.10 as it has the latest Linux drivers.

[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb)

---

### Post by JoshuaRL on 2008-04-07
> **icecoldstar said:**
> Thanks to you ALL!!! I will attempt to install my drivers and stuff right after i log off here....
kudos to all!!!

Here is the problem i got...



Couple things.  You might try attaching any pictures with the Manage Attachments button on the Post page near the bottom.

And you'll need to run the 5 steps in Recovery Mode.  That's the problem you're having, an Xserver session is running.

---


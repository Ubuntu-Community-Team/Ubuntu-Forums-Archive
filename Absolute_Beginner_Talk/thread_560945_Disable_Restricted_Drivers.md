---
title: "Disable Restricted Drivers"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Mad_Max_1412 on 2007-09-27
Guys,

I was having a little problem with video editing in Wine and it was suggested that perhaps turning on any options in Restricted Drivers might resolve the issue (well that's what I thought the advice was saying)

Anyway I went to the restricted drivers option and selected the only thing there which was the nvidia drivers.

I confirmed my choice and it downloaded the drivers (I gather). It then said that a re-boot was required which I did but all I get now is the message about it not starting the X Server.

The message I get is:
"Failed to start the X Server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem."

When I select Yes, part of the message I see says about a mis-match "The nVidia kernel module has version 1.0-9755 but this x module has the version 1.0-9631".


I've tried the following suggestions I've found in other forum threads but they haven't resolved the problem. Here's what I've done.

sudo -s
<password> - now I'm at the root prompt
rmmod nvidia
modprobe vesafb (modprobe nv or modprobe vesa only give me errors)
/etc/init.d/gdm start (I get a message saying "Starting GNOME Display Manager [OK]"
Ctrl+Alt+F7 (I get a message saying "The X Server is now disabled. Restart GDM when it's configured properly")

Then it doesn't matter if I hit the restart button or power off totally, I just get the same problem on bootup.

Could someone please provide some assistance please??

---

### Post by mrfr0g on 2007-09-27
Hello;

I had a similar problem on a friends computer. From what you described, you are now using the restricted nvidia drivers. What's likely happening, is the /etc/X11/xorg.conf file, has some information that is limited to the old driver set. Your best bet is to reconfigure the xorg.conf file. You can do this by;

Rebooting your computer, when the grub list loads, select "Recovery mode" for your kernel.

This will load you in to a command line prompt. Type;

dpkg-reconfigure xserver-xorg

This will take you through a setup process for configuring the xorg file. Once you have finished this process, it will exit to command line. From there you should be able to;

init 3

To continue loading the OS.

**Disclaimer, I am by no means an expert on Linux, this is just what I did to assist my friend.**

---

### Post by Mad_Max_1412 on 2007-09-27
Hi,

Thanks for the info. I will give it a go when I get home.

Being a newbie, I hope when you say:

> This will take you through a setup process for configuring the xorg file.

that it will be a simple to understand process.

Regards

---

### Post by Mad_Max_1412 on 2007-09-27
Hi,

The questions were rather straight forward, but I still get the same error and going into the details show that there is a mismatch in the kernels.

Regards

---

### Post by mrfr0g on 2007-09-27
You could try to uninstall and reinstall the drivers. Log back in to the recovery mode, and type;

sudo apt-get remove nvidia-glx

then

sudo apt-get install nvidia-glx

This *should* uninstall the nvidia drivers, and reinstall them, as well as reconfigure x

---

### Post by Mad_Max_1412 on 2007-09-28
Hello mrfr0g

Thanks for the suggestion but unfortunately it didn't work.

The first time I removed and re-installed them, I then did INIT 3 as per a earlier post as I'm lead to believe this would have made the OS continue to load.

I got the same error, so I re-boot, did the remove and install and this time just re-booted.

I still got the same error.

Then I thought "what would happen if I didn't install the drivers after removing them", so I just did the remove command and re-booted but still no luck.

Given that I'm a newbie, and I have a shared directory that I can access from this Windows machine called "ubuntu-vids", how can I copy the xorg file over to this shared directory so I can attach it so everyone can look through it and see what might be the problem.  I assume my shared directory would be something like \home\ubuntu-vids.

Regards

---

### Post by Mad_Max_1412 on 2007-10-05
I resolved the issue by entering

sudo dpkg -reconfigure -phigh xserver-xorg

and then accepting nv as the answer to the first question, and not selecting any resolutions in the next question.

It then took me to the prompt where I entered

init 3

and this took me into the gui but only at a maximum resolution of 1024x768.

So I've edited the xorg.conf file to add 1680 x 1050 to each of the lines but will need to wait until my updates finish loading so I can re-boot and have this new resolution available.

In the meantime, since I've got a nVidia 6600GT card, how can I be sure I'm using the best driver to get the best out of my graphic card? I seen talk about enabling 3D acceleration etc and since I will be working with video and be trying out some heavy graphic based games, I want to make sure I have the best driver.

Under Administration --> Restricted Drivers it now shows nVidia accelerated drivers as "Not in Use" but enabling them is what caused the problems in the first place.

Under "Applications --> System Tools" there's Nvidia settings but when I select that now it says it can't launch it because there's no such file or directory.

Thanks

---

### Post by Mad_Max_1412 on 2007-10-07
Guys,
 
I've now been to the Nvidia website and downloaded the latest linux driver for my video card and it's saved on the Desktop.

I then opened a Terminal window and typed

cd Desktop

to get the prompt at the desktop.   I then entered the command as shown on the webpage (so my terminal window line reads:)

max@ubuntu:~/Desktop$ sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

and after entering my password, I get the following:

ERROR: You appear to be running an X server; please exit X before
installing. For further details, please see the section INSTALLING
THE NVIDIA DRIVER in the README available on the Linux driver
download page at [www.nvidia.com](www.nvidia.com).

I'm working through the Readme file on the nvidia website to see if I can work out what to do.

Here is the steps I think I have to take based on my understanding of this readme file.

1.  In my /etc/X11/xorg.conf file I need to:
     1.1  Comment out the line 
             Driver "nv" 
      1.2  Enter the following line
             Driver "nvidia"
       1.3 Comment out the lines
             Load "dri"
             Load "GLCore"
      1.4 In the Module section of the file, add the line (if it does not already exist):
             Load "glx"

2.  Then, the Readme also says to exit the X server.  Can I clarify something here please?  References to X Server - is that the GUI?

Anyway, it then goes on to say that Runlevels are what is used to decide what services are started/stopped when the system starts up or shut down.  It says that runlevel of 5 typically starts the X window and that I should change my runlevel to 1, 2 or 3.  It then goes onto say that the runlevels are set in the /etc/inittab file where I change the setting

id:n:initdefault:

with n being the run level.

Unfortunately I don't have this file.  In my /etc directory, my files go from inetd.conf to inputrc, thus not even listing inittab.

So I gather that once I had done point 1 above (modify xorg.conf file) and point 2 (changing the runlevel in the file once I find it)  I do the following:

3.  Restart the system. I assume this should bring me to a command prompt.
4.  Enter the following command, once I change to the Desktop folder

sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

5.  Follow whatever instructions it has.
6.  Change the runlevel back to 5 so it boots to the X Window.
7.  Restart and enjoy the full benefits of an up-to-date driver.

Correct?  Any advice welcome.  I am not game to do anything without some confirmation of what I am going to do.

Thanks

---


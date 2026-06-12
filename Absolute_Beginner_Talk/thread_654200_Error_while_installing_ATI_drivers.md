---
title: "Error while installing ATI drivers"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by raguru on 2007-12-30
Hi,

I am using Kubuntu 7.10 (Gutsy).  All these days, I had a GeForce 6200 video card and the restricted nVidia drivers worked perfectly.  But unfortunately, the graphics card died last week and I went out and got a new one (VisionTek Radeon HD2400 PRO).  This one is an ATI and Ubuntu tells that no restricted drivers are needed for my card, but does not the display the 1440x900 resolution  my 19" widescreen monitor needs.  

So, I followed this guide to install the ATI drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

However, in the last step of the manual install of the driver (sudo apt-get install -f), I get the following error:

-------------------------------------------------------------------------------------
rtumkur@rtumkur-desktop:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  zlib1g-dev libfreetype6-dev libslang2-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xorg-driver-fglrx
The following packages will be REMOVED:
  nvidia-glx-new
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8558kB of archives.
After unpacking 7807kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted xorg-driver-fglrx 7.1.0-8.37.6+2.6.22.4-14.10 [8558kB]
Fetched 8558kB in 1m35s (89.4kB/s)                                             
(Reading database ... 180171 files and directories currently installed.)
Removing nvidia-glx-new ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 180123 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_i386.deb (--unpack):
 trying to overwrite `/usr/bin/amdcccle', which is also in package fglrx-amdcccle
dpkg-deb: subprocess paste killed by signal (Broken pipe)
[B]Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
rtumkur@rtumkur-desktop:~/Desktop$ 
-------------------------------------------------------------------------------------

Can someone please help me with this?  I don't understand the error and I don't know if I should proceed with the next step which is "Configure the Driver".  

My machine is a 32 bit desktop.  I would appreciate any help with this error.  

Thanks in advance.

-Raghu

---

### Post by SOULRiDER on 2007-12-30
I believe you will want to remove the package called **org-driver-fglrx** but im not 100% positive. Check out this guide on how to install the drivers and just ask for help if you get stuck 
[http://ubuntuforums.org/showthread.php?t=515573&highlight=envy](http://ubuntuforums.org/showthread.php?t=515573&highlight=envy)

---

### Post by raguru on 2007-12-30
Thanks SOULRiDER for your quick resposne.  I will take a look at the link you have provided.  I had not come across it in my searches on this topic.  

cheers,
Raghu

---

### Post by SOULRiDER on 2007-12-30
No problem, we're here to help. If you have any further questions just ask, dont be affraid :)

---

### Post by Saint Angeles on 2007-12-30
i have an ATI Radeon X1550 with a samsung 19" widescreen at 1440x900

heres what you need to do:

go to [www.ati.com]("http://www.ati.com") and find the driver download page. look for a link that says "previous drivers..." and find "7.11 catalyst"

download the ati...run file to your desktop

goto a terminal and navigate to the desktop... use the "sudo sh ati...."

hit enter and you will be in a graphical installer like a windows installer. just go through the whole thing using default settings.

after its done, you'll need to add some things to your xorg.conf

i'm gonna attach mine so you can get the idea.

---

### Post by raguru on 2007-12-31
Saint Angeles,

Thanks for the response.  I will try doing what you suggested.  I already have the downloaded drivers.  In my previous attempt, I did not do it through the graphical installer.  Let's see if that works for me.  Thanks again.

cheers,
Raghu

---

### Post by raguru on 2007-12-31
I have tried what SOULRiDER suggested and it got the resolution up from about 1024x760 to 1280x1024.  But the fglrxinfo command still shows MESA for OpenGL and not "ATI....".  

My next option is to try what Saint Angeles has suggested and see how it works in my case.  

Thanks again.

-Raghu

---

### Post by frenchsquared on 2007-12-31
I tried all the option mentioned above with a 2400 series ATIcard in a laptop
what finaly worked was Envy
 
good luck

---

### Post by raguru on 2007-12-31
Thanks Frenchsquared.

How do I go about installing Envy?  Through Synaptic?  Thanks.

-Raghu

---

### Post by raguru on 2007-12-31
I tried the method that Saint Angeles suggested and everything looked like it went well.  But now the xserver won't start! :-(

At the end of the installation, it said that if the xserver does not start, to type the command

aticonfig --uninstall -f

I tried this and it does not recognize the command.  In Grub, I can get in using an older "generic version", but how do I go about fixing it so that the xserver starts up on its own?  

Thanks.

-Raghu

---


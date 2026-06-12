---
title: "Some problem"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by WikipedianKiba on 2005-10-04
Hello there! I been messing with linux for awhile. It totally beat window hand down! :D  Right now, I am in the progress in compling a winmodem driver. I have come accross in a error telling me to get the autoconf.h or whatever it was called. I need to know what to do. This is my first time compling full blown software.

On the other hand. I was unable to adjust my resolution screen bigger than 640 x 480. Please remember that my linux box is internet crippled. (duh, I am trying to get that winmodem online)

Thank you in adavance.

---

### Post by mlomker on 2005-10-04
> On the other hand. I was unable to adjust my resolution screen bigger than 640 x 480. Please remember that my linux box is internet crippled. (duh, I am trying to get that winmodem online)

Try **sudo dpkg-reconfigure xserver-xorg** from a command line.  It'll ask you questions about your video card and you should just press 'enter' for anything that you're not sure of.

---

### Post by Ampersand on 2005-10-04
There's two ways of adding higher resolutions.
Firstly, you can run 'sudo dpkg-reconfigure xserver-xorg'.
Alternatively, you can edit the configuration file manually. Run 'gksudo gedit', and open /etc/X11/Xorg.conf. Towards the bottom, you will find  Section "Screen". You can add additional resolutions in the Modes rows. For example, my section is:
```

Section "Screen"
Identifier	"Default Screen"
Device		"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
Monitor		"Generic Monitor"
DefaultDepth	24
SubSection "Display"
Depth		1
Modes		"1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth		4
Modes		"1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth		8
Modes		"1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth		15
Modes		"1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth		16
Modes		"1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth		24
Modes		"1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

```

---

### Post by WikipedianKiba on 2005-10-04
I did try the first option for trying to fix screen resolution but it did not work. So I will try the second option.

---

### Post by WikipedianKiba on 2005-10-07
I try all option you have suggested. I am still stuck with the lower resolution screen. The second option was to edit the xorg.conf file. The information was already there. like 800 x 600, etc.

Is there any way to know that my modem is actually usable? I install the driver but I had no idea if it will work.

---

### Post by WikipedianKiba on 2005-10-07
I fixed my resolution screen. Now how to know my modem will work without an isp, password, etc?

---

### Post by mlomker on 2005-10-07
[QUOTE=WikipedianKiba]I fixed my resolution screen. Now how to know my modem will work without an isp, password, etc?[/QUOTE]

If you don't have any of those then why do you need it to work?  :p 

I use **minicom** for sending AT commands to modems, or more likely for me, for serial connections to routers.  It can be downloaded in Synaptic and runs from a terminal prompt.

---

### Post by WikipedianKiba on 2005-10-07
I need my Ubuntu installation to be able to connect to the internet once I provided those information. I know it can't go anywhere without those information.

I managed to install a winmodem driver. I go to the network application and select interface PPPo than I select property. Than I go to modem and click on autodetect. They say they didn't detect my modem.

---

### Post by mlomker on 2005-10-07
> They say they didn't detect my modem.

Well, then driver might not be installed properly.  What driver did you install?  Did it have any tests for you to see if it installed properly?

---

### Post by WikipedianKiba on 2005-10-07
Hmmm..the driver is installed indeed. I do not know if it have any test to see if it installed properly. I will check the readme.txt to make sure I followed the instruction correctly.

---

### Post by WikipedianKiba on 2005-10-07
It seem that the installation script did not support the Ubuntu distribution from the list that they say the installation script was designed for.

---

### Post by WikipedianKiba on 2005-10-07
It seem that the directory /dev/modem device file was not found. I did see a modem file but it is not a folder. Do folder indicate a directory?

---

### Post by mlomker on 2005-10-07
When the driver is loaded it should give you some information about what /dev file it uses.  You can look through the contents of **dmesg | less** to see what it is telling you.  I'm not sure if the driver is even loading based upon what you've told me.  If you gave me a link to the driver that you are using then I might be able to help you better.

---

### Post by WikipedianKiba on 2005-10-07
I downloaded the file from here
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=6801&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=6801&strOSs=39&OSFullName=Linux*&lang=eng)

In their text, they say /dev/modem directory will be created.

---

### Post by mlomker on 2005-10-07
And how far did you get?  Did the driver compile without errors?  Were you able to **sudo modprobe intel537** when you were done?

---

### Post by WikipedianKiba on 2005-10-07
I did complie but I never did the command sudo modprobe intel537. I will do so after this post.

---

### Post by WikipedianKiba on 2005-10-07
I met with the fetal error

The msg is:
Module intel537 not found

---

### Post by mlomker on 2005-10-07
> Module intel537 not found

I'm left to assume that it didn't compile properly.  What version of Ubuntu are you using?

What does this say?

```

uname -r

```

---

### Post by WikipedianKiba on 2005-10-07
For uname -r; it say 2.6.10-5-386

I am using version 5.04

---

### Post by mlomker on 2005-10-07
I recommend running through the steps again.  Let me know what errors you receive.  I did sucessfully download and compile the driver.  I'm concerned about giving it to you as a .deb file because there's always a chance that it'll damage your system.  It's better for you to compile it yourself.

Do this:

```

sudo apt-get install linux-headers-$(uname -r)

```

Change to the directory you extracted the intel drivers to:

```

sudo make clean
sudo make 537
sudo make install

```

---

### Post by WikipedianKiba on 2005-10-07
Look like I have to get it from the internet for the package which my Ubtuntu box cannot connect to.
I enocunter an error when I did make 537.

---

### Post by WikipedianKiba on 2005-10-07
Here is the error file I copy from m Ubuntu box when I did make 537:
 Module precompile check
   Current running kernel is: 2.6.10-5-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.10-5-386
make[1]: Entering directory `/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/coredrv.o
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:754: warning: initialization from incompatible pointer type
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:755: warning: initialization from incompatible pointer type
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: In function `dspdrv_CommRamISR':
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:877: warning: function declaration isn't a prototype
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/clmmain.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/rts.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/task.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/uart.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/wwh_dflt.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/locks.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/softserial_io.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/softserial_ioctl.o
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/softserial.o
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/softserial.c: In function `softserial_register_tty':
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/softserial.c:125: warning: assignment from incompatible pointer type
  CC [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/afedsp_int.o
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/afedsp_int.c:48: warning: function declaration isn't a prototype
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/afedsp_int.c:65: warning: function declaration isn't a prototype
/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/afedsp_int.c:454: warning: initialization from incompatible pointer type
  LD [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/.537core.lib.cmd for /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/537core.lib
  CC      /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/Intel537.mod.o
  LD [M]  /home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/kiba/Desktop/intel-537ep-2.60.80.0.tgz_FILES/intel-537EP_secure-2.60.80.0/coredrv'

---

### Post by mlomker on 2005-10-07
To be honest, I don't know what that means becuase I'm not a programmer.  It's safe to say that you didn't successfully install the driver the first time around, though.

You're welcome to try the version that I compiled but I am not sure whether or not it'll wreck your Ubuntu installation.  With that caveat, here is the [link to the file]("http://mail3.mpr.org/mlomker/intel-537-modem_2.60.80.0-1_i386.deb").

If you choose to try it, this command will install it:

```

sudo dpkg -i --force-yes intel-537-modem_2.60.80.0-1_i386.deb

```

Once installed, hopefully, you should be able to use the moprobe command that I had previously posted.

---

### Post by WikipedianKiba on 2005-10-07
It seem that command doesn't work for me. I think it is the first time I install a debian package so I don't know how to do it.

---

### Post by mlomker on 2005-10-07
You need to give me exactly what you typed and exactly what the error message was or I can't help you.

You should be able to cut/paste from the terminal window.

---

### Post by Mustard on 2005-10-07
[QUOTE=WikipedianKiba]It seem that command doesn't work for me. I think it is the first time I install a debian package so I don't know how to do it.[/QUOTE]

Just a hunch, but you might be executing the command on the wrong directory.

Try using the **cd** command to change your working directory in the terminal.  For instructions on how to do that you could type **info cd**.

Change the directory to the same directory you downloaded the .deb package to.

---

### Post by WikipedianKiba on 2005-10-07
Here is the error:
dpkg: unknown force/refuse option `yes'

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
kiba@WikipedianKiba:~/Desktop/File$

---

### Post by mlomker on 2005-10-08
Oops.  I hate it when different commands use slightly different syntax.  I also want to stress the point that I'm not sure what'll happen when you install the package--it could work and it could leave your machine unbootable.  I'm not experienced with building packages, but I gave it my best shot.

```

sudo dpkg -i --force-overwrite intel-537-modem_2.60.80.0-1_i386.deb

```

---

### Post by Mustard on 2005-10-08
[QUOTE=mlomker]Oops.  I hate it when different commands use slightly different syntax.  I also want to stress the point that I'm not sure what'll happen when you install the package--it could work and it could leave your machine unbootable.  I'm not experienced with building packages, but I gave it my best shot.

```

sudo dpkg -i --force-overwrite intel-537-modem_2.60.80.0-1_i386.deb

```[/QUOTE]

Sounds like a good time to do a backup. :)

---

### Post by Dria on 2005-10-14
Have you managed to use your modem? Do you still need hints on this topic?

If so I think you should start over again.
Uninstall the driver you were trying to use, then follow the instructions you find [here]("http://ubuntuforums.org/showthread.php?t=36762&highlight=Intel+537").

Be aware that you may encounter problems like NOT having the symbolic link "/dev/modem" created in the right way, that is, the name of the module CAN be wrong.
Do a ```
ls -l /dev | grep 537
``` and see the results. You may find more than one module containing "537"; something like "/dev/Intel537" or "/dev/537" or even "/dev/Intel5370". If so, look at the creation date and time and pick the newest: that should be the right one.

Then use the name of this module to make a link to "/dev/ttyS15" as described on the Howto.

After that, when you try to configure wvdial or gnome-ppp or even minicom, use the link YOU created following the HowTo, like "/dev/ttyS15" and do NOT use the standard "/dev/modem". At least for me that was the solution.

I've found an additional warning [here]("http://ubuntuforums.org/showthread.php?t=50469&highlight=intel+537"), use this if the above still have problems.


Please send a word if this solves your problem.

---


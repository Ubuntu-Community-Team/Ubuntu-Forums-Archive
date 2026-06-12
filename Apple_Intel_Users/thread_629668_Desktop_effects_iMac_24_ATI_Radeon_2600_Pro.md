---
title: "Desktop effects iMac 24 ATI Radeon 2600 Pro"
date: 2007-12-02
forum: Apple Intel Users
---

### Post by wb9258 on 2007-12-02
I recently installed Ubuntu 7.10 on my new aluminum iMac.  I am new to Linux and am having a hard time setting up desktop effects.  I have found several post discussing ATI 2600 drivers, but can not find any step-by-step guides for the iMac and Gusty.  Please let me know what other system info I need to post.  I have tried to install the newest ATI driver, but get the error...

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again. 

Any help would be greatly appreciated as I have searched for 3 days with no success.

---

### Post by cyberdork33 on 2007-12-02
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually)

If you are getting an error, you need to say what your command was that produced the error.

---

### Post by wb9258 on 2007-12-02
Cyberdork,

Thanks for the quick reply.  I tried this page before I posted and keep getting stuck at "Configure the Driver"  

Below is my terminal output...

wb9258@wb9258-desktop:~$ sudo apt-get install linxu-restricted-modules-generic restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linxu-restricted-modules-generic
wb9258@wb9258-desktop:~$ sudo ap-get install xorg-driver-fglrx
sudo: ap-get: command not found
wb9258@wb9258-desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wb9258@wb9258-desktop:~$ sudo depmod -a
wb9258@wb9258-desktop:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11


Should I then continue to the "sudo aticonfig --overlay-type=Xv"? or am I missing something?

I have also tried the Alternative configure the driver the manual way and when I enter "gksu gedit /etc/X11/xorg.conf" The xorg.conf gedit window is blank.  There is nothing to edit?  Any help would be greatly appreciated.

wb9258@wb9258-desktop:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
wb9258@wb9258-desktop:~$ sudo aticonfig --overlay-type=Xv
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
wb9258@wb9258-desktop:~$ gksu gedit /etc/x11/xorg.conf



Thanks.

---

### Post by yousufinternet on 2007-12-03
have you tried installing the driver using 
system > Adminstration > Restricted Drivers

---

### Post by wb9258 on 2007-12-03
Yes, this tells me there are no restricted drivers needed.  Any other suggestions?

Thanks.

---

### Post by cyberdork33 on 2007-12-03
> **wb9258 said:**
> wb9258@wb9258-desktop:~$ sudo apt-get install linxu-restricted-modules-generic restricted-manager.

You are following the wrong part of the directions. The version of fglrx in the repos does not yet support your graphics card. I specifically linked to the manual install section. You have to install manually.

Actually, if the top section would work, then the restricted drivers manager would be able to offer the driver in the first place.

The good thing about using the newer drivers is that they support compositing without XGL!

---

### Post by wb9258 on 2007-12-03
I went through the wiki and I still get an error.

When I get to the verify step...

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

I see...
wb9258@wb9258-desktop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)
wb9258@wb9258-desktop:~$ 

I did not notice any errors when going through the wiki.  Any suggestions?  Please let me know if you need additional info.


Thanks,

---

### Post by cyberdork33 on 2007-12-03
> **wb9258 said:**
> I went through the wiki and I still get an error.

When I get to the verify step...

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

I see...
wb9258@wb9258-desktop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)
wb9258@wb9258-desktop:~$ 

I did not notice any errors when going through the wiki.  Any suggestions?  Please let me know if you need additional info.


Thanks,
make sure you are re linking the libraries as directed in the bottom of the how to.

---

### Post by wb9258 on 2007-12-04
I am still having a problem getting this setup.

What part of the tutorial is "re linking the libraries as directed in the bottom of the how to."?

When I reboot Ubuntu I get "Ubuntu is running in low graphics mode"  It gives me the option to choose resolution ect....  Is this normal???

I started over from the beginning and went through everything without any noticeable errors.  The only question I had is in this part...

Make it executable

sudo chmod ugo+x /etc/init.d/ati-module-fix

Now, make this run before gdm (which starts with sequence number 13)

sudo update-rc.d ati-module-fix defaults 12

It is possible that gdm sequence number is different. To find the gdm sequence number:

ls /etc/rc2.d/

And substitute 12 in the previous command with gdm sequence number - 1. 


When I run ls /etc/rc2.d/.... This makes me think the 12 should be 29 (30-1) but I can not make a change.


wb9258@wb9258-desktop:~$ ls /etc/rc2.d/
README                       S20apmd           S25bluetooth
S05vbesave                   S20apport         S30gdm
S10acpid                     S20atieventsd     S89anacron
S10powernowd.early           S20hotkey-setup   S89atd
S10sysklogd                  S20makedev        S89cron
S10xserver-xorg-input-wacom  S20nvidia-kernel  S98usplash
S11klogd                     S20powernowd      S99acpi-support
S12ati-module-fix            S20rsync          S99laptop-mode
S12dbus                      S22consolekit     S99rc.local
S12hal                       S24avahi-daemon   S99rmnologin
S19cupsys                    S24dhcdbd         S99stop-readahead
wb9258@wb9258-desktop:~$ 

I hope you can follow what I am saying.  Thank in advance for the help.

---

### Post by wb9258 on 2007-12-06
I am still not able to get compiz working.  I am looking for a guide/wiki written for the new aluminum iMacs.  Do you have any other sugguestions?  Would you recommend I install the original driver and repeat the process?  I seem to get a lot of error messages when Ubuntu boots and I still can only run in low graphics mode. 

Thanks.

---

### Post by wb9258 on 2007-12-08
What is the best way to restore Ubuntu back to original?  I have so many errors from trying to install drivers for compiz I would like to restore and start over.  Thanks.

---

### Post by AlexMR on 2007-12-09
Hello wb9258,

the best way would be to do a fresh install of Ubuntu (hopefully you have got a home partition, otherwise backup your data). And don´t use the 64bit-version, it has got almost no benefit over the 32bit-version but is known to cause problems every once in a while.

After installation, download the latest ATI-driver for Linux:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Choose: Linux x86 -> Radeon -> ATI Radeon HD 2600 series -> GO

After downloading the installer, you need to make it executable. Open a terminal, change to the directory where you downloaded the driver and type

chmod +x *name of downloaded installer file*

After that, run the installer

sudo sh *name of downloaded installer file*

Choose automatic installation. After installation, run

sudo aticonfig --initial

Reboot

3D-acceleration should work now. In order to make compiz function, edit compiz by adding "fglrx" into its internal whitelist

sudo gedit /usr/bin/compiz

#Whitelist
WHITELIST="nvidia intel ati radeon i810 **fglrx**"

You should now be able to activate Compiz as well.

Greets,
Alex

---

### Post by cyberdork33 on 2007-12-09
Use Manual Install Instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Kotare on 2007-12-09
Hello wb9258,

This worked on a 24" aluminium iMac:
Installed from Ubuntu 7.10 386 Live CD: 4GB for /, 1GB for /home. A /etc/X11/xorg.conf  was created by the installation; best available resolution was 1600x1200.

To get 1920x1200 resolution and Desktop Effects, used the Manual Install Instructions as Cyberdork33 says, and exactly as listed on the wiki. This worked without problems.

Apple recommend leaving the machine powered up if it is  in day-to-day use. I decided to follow the recommendation.
After installation of Ubuntu, changed the kernel to 2.6.20-15 from the Feisty source repository. 
Then installed the ati drivers by following the step for manual installation from the ati unofficial wiki, but for Feisty, not Gutsy.
The cost of wanting to have the machine sleep has, so far, been no Stellarium 0.9, no QLandkarte 0.5.3. But a small price to pay for the pleasure of spinning that Cube - I prefer to think of it as almost 8 ft of desktop.

Wouldn't have managed this without the knowledge found by looking through the help given in forums, mainly this Forum, for which I give thanks.

Coupla other items:
Sound through the headphone jack don't work, which means rebooting into OS X to use Skype. 
So I haven't bothered with the iSight camera or the microphone.
Using Nicolas Boichat's bl1.c script to turn down the brightness of the screen, otherwise it's like sitting in front of a sunray lamp.

HTH & Cheers.

---

### Post by cyberdork33 on 2007-12-09
> **Kotare said:**
> After installation of Ubuntu, changed the kernel to 2.6.20-15 from the Feisty source repository. 
Then installed the ati drivers by following the step for manual installation from the ati unofficial wiki, but for Feisty, not Gutsy.
The cost of wanting to have the machine sleep has, so far, been no Stellarium 0.9, no QLandkarte 0.5.3. But a small price to pay for the pleasure of spinning that Cube - I prefer to think of it as almost 8 ft of desktop.

You can use a newer kernel, you just have to compile with SLAB instead of SLUB.

---

### Post by wb9258 on 2007-12-12
I have attempted to install the ATI driver (ati-driver-installer-7-11-x86.x86_64.run) multiple times and keep ending up having to do a fresh install of Ubuntu on my Linux partition because after the driver install (attempt) I am only able to run Ubuntu in low graphic mode and I get multiple errors on startup.  I am going to attempt to write out exactly what I am doing so someone hopefully can find my mistake.  Please note I am new to Ubuntu and Linux in general.  I am well into my 3rd week attempting to get desktop effects and compiz working and have not began to address other issues such as no sound, keyboard number do not work, etc…I am really interested in learning a new OS and getting involved with open source, but I have to say this has been extremely frustrating and time consuming.  I will now post the steps from the wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)) along with my explanation of what I am doing/thinking…I know this is really long, but I would really be thankful for any help!

**I start at Method 2: Install the Catalyst 7.11 Driver manually**

I download the ATI driver using the link in the wiki, but I can only download this to my desktop.  (Please let me know how to change the download directory if downloading to the desktop will cause an issue).  

I then open the terminal and cd Desktop (I can then do a ls and see the download driver files)

**Install necessary tools**

I am not sure what this step is doing, so I just copy each line into the terminal and seem to get through without any error.

sudo apt-get update (then press enter)

sudo apt-get install module-assistant build-essential fakeroot dh-make 
debhelper \ (then press enter)

debconf libstdc++5 linux-headers-generic (then press enter)

**Create .deb packages:**

I assume this is what install the driver files from my Desktop…

I past the following command in the terminal and press enter.

sudo bash ati-driver-installer-7-11-x86.x86_64.run --buildpkg Ubuntu/gutsy 

Still no noticeable errors…

**Blacklist old fglrx module from linux-restriced-modules:**
I do not know what fglrx modules are, so I paste the follow into terminal…

gksu gedit /etc/default/linux-restricted-modules-common

This pops up a box where I can add “fglrx” in the empty quotes on DISABLED_MODULES=””

Before   DISABLED_MODULES=""
After    DISABLED_MODULES="fglrx"

I then save and continue…

**Install .deb packages:**
I just past this exact command in terminal

sudo dpkg -i xorg-driver-fglrx_8.433-1*.deb fglrx-kernel-source_8.433-1*.deb fglrx-amdcccle_8.433-1*.deb

I do not get any of the two mentioned errors so I continue…

I ignore this step as I do not get any errors from the above command

Ignored  ==  sudo apt-get install -f


**Remove any old fglrx debs from /usr/src/:**

I cd to /usr/src/ and make sure there are not any old fglrx debs

I paste this in the terminal sudo rm /usr/src/fglrx-kernel*.deb

**Fix Broken dependencies**

sudo apt-get -f install

Nothing really happens after the above command…

**Compile the kernel module:**

I then paste the three commands in the terminal

sudo module-assistant prepare,update
sudo module-assistant build,install fglrx -f
sudo depmod –a

**Create the following folder**

sudo mkdir /lib/modules/$(uname -r)/volatile

After this I get something saying already exist so I continue…

**Create a symbolic link**
I paste sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko in the terminal exactly
I am not sure if I should replace my username with uname in the above command (so I just paste it exactly as shown)


Then I paste…

sudo gedit /etc/init.d/ati-module-fix

This opens a blank window where I copy the code from the wiki and paste it in the box…

#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0

I then save and close the window…

**Make it executable**
sudo chmod ugo+x /etc/init.d/ati-module-fix I paste this exactly in terminal

**Now, make this run before gdm (This really confuses me)**
I paste ls /etc/rc2.d/ and see a line that say something like
	
30sGDM (not sure exactly what is says, but it’s the only one with GDM)

So I sudo update-rc.d ati-module-fix defaults [29] … replace seqno with 29 (30-1) 

**Is this correct???**

Important:  You have to recompile the kernel module after each kernel update! (Note: This does not affect you until the next time you update your kernel.)

I then sudo gedit /etc/modprobe.d/lrm-video

And comment out the second line as shown

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS #  << this line
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS


I**[SIZE="4"][COLOR="Red"] now reboot my machine and start up without any errors still running in regular (not safe) graphics mode.  After the next steps is when I run into problems…[/COLOR][/SIZE]**

**Alternative: Configure the Driver, The Manual Way:**

I Paste this in terminal     gksu gedit /etc/X11/xorg.conf

**This command opens a Blank Window**

I then paste the below lines in this window and save

Section "Device"
	[...]
#       Driver          "vesa"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	[...]
EndSection

**Finish the installation**

I reboot by sudo shutdown -hr now

**Now I receive errors when Ubuntu loads black screen asking for login id and Ubuntu runs in low graphics mode**.

Verifying

From the terminal I type … 

Fglrxinfo

wb9258@wb9258-desktop:~$ fglrxinfo
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)
wb9258@wb9258-desktop:~$

---

### Post by cyberdork33 on 2007-12-12
> **wb9258 said:**
> sudo apt-get install module-assistant build-essential fakeroot dh-make 
debhelper \ (then press enter)

debconf libstdc++5 linux-headers-generic (then press enter)

```

sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic
```Then press enter... It is all one command. Not that I think this is really a source of the problem. the little "\" at the end of a line means the line continues onto the next line. 
> **wb9258 said:**
> **Create a symbolic link**
I paste sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko in the terminal exactly
I am not sure if I should replace my username with uname in the above command (so I just paste it exactly as shown) that is right... uname -r returns the version of your kernel... it is just a shortcut to access the correct folder. You can type the command by itself to see what it will give.

```
uname -r
```
> **wb9258 said:**
>  Then I paste&#8230;

sudo gedit /etc/init.d/ati-module-fix

This opens a blank window where I copy the code from the wiki and paste it in the box&#8230;

#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0

I then save and close the window&#8230;

**Make it executable**
sudo chmod ugo+x /etc/init.d/ati-module-fix I paste this exactly in terminal

**Now, make this run before gdm (This really confuses me)**
I paste ls /etc/rc2.d/ and see a line that say something like
    
30sGDM (not sure exactly what is says, but it&#8217;s the only one with GDM)

So I sudo update-rc.d ati-module-fix defaults [29] &#8230; replace seqno with 29 (30-1) 

**Is this correct???**

Important:  You have to recompile the kernel module after each kernel update! (Note: This does not affect you until the next time you update your kernel.)

I then sudo gedit /etc/modprobe.d/lrm-video

And comment out the second line as shown

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS #  << this line
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS
I would just ignore making that script unless you really have to have it. I did not create it, and everything works fine on my machine.

> **wb9258 said:**
> **Alternative: Configure the Driver, The Manual Way:**

I Paste this in terminal     gksu gedit /etc/X11/xorg.conf

**This command opens a Blank Window**Well that is not good. that means your xorg configuration file is missing for some reason. I would say that is probably the source of your issues.  This command should generate a xorg.conf for you, which you can then edit as mentioned:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wb9258 on 2007-12-12
Ok, I finally got the driver installed and compiz working properly (I now have the cube!!!).  The wiki instructions still will not work, so I tried what Alex suggested and it worked.

Was I supposed to use the chmod + x name of downloaded installer file in the wiki???  This is what made the difference.      

> chmod +x name of downloaded installer file

After that, run the installer

sudo sh name of downloaded installer file

Choose automatic installation. After installation, run

sudo aticonfig --initial

Reboot

Thanks again for all the help and I am sure I will have many questions in the future :)

Also, It seems now everything runs a bit sluggish.  Is this the price to pay for compiz fusion?  I have 3 GB of ram???  Can I allocate more to the video card to increase proformance?

Thanks!

---

### Post by AlexMR on 2007-12-15
Glad it worked for you...


[QUOTE="wb9258"]Also, It seems now everything runs a bit sluggish. Is this the price to pay for compiz fusion?[/QUOTE]

That´s the price for using an ATI-card with its notorious drivers. At least, it seems that those drivers get better on each new release, so hopefully everything will work fluently in "near" future.

Greets,
Alex

---

### Post by cyberdork33 on 2007-12-15
IDK everything runs pretty nicely on my machine. (iMac w/ X1600). Beryl was kinda sluggish, but compiz is pretty smooth.

---

### Post by Ricardo Matos on 2008-01-09
Hi everyone!!

i have a ATI HD 2600 XT 512MB GDDR3 DVI PCi-x on a brand new box with a plain vanilla  UBUNTU 7.10 installation.

I was having trouble to setup my Graphics card until i found the posts in this forum and follow up the guide lines presented.

i have followed instructions exactly as in:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Afterwards i was able to have the correct driver installed, enable desktop effects, stop the existing flickering and configure settings on the ATI Catalist Control Center.

However, whenever i run some games like Open Arena the screen goes Black and i have to reboot the machine. Another example is the Rhytmbox when i enable the visualization mode with the cool effects i get some horrible flickering...

Can anyone help me?

Thank you in advance...

My  fglrxinfoI:

:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7170 Release



My  dmesg:


[   37.678927] [fglrx] Reserve Block - 0 offset =  0X1fffc000 length = 0X4000
[   37.678934] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   37.678936] [fglrx] Reserve Block - 2 offset =  0Xff7f000 length = 0X80000
[   37.921964] [fglrx] interrupt source 60000001 successfully enabled
[   37.921971] [fglrx] enable ID = 0x00000006
[   37.921981] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[   37.922044] [fglrx] interrupt source 00000040 successfully enabled
[   37.922046] [fglrx] enable ID = 0x00000007
[   37.922050] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[   37.930479] [fglrx] interrupt source ff00002c successfully enabled
[   37.930482] [fglrx] enable ID = 0x00000008
[   37.930488] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   37.930529] [fglrx] interrupt source ff00002d successfully enabled
[   37.930532] [fglrx] enable ID = 0x00000009
[   37.930535] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   37.930566] [fglrx] interrupt source 20000400 successfully enabled
[   37.930568] [fglrx] enable ID = 0x0000000A
[   37.930571] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[   42.783396] hda-intel: Invalid position buffer, using LPIB read method instead.
[   45.895026] eth0: no IPv6 routers present
[   57.299441] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list
[   57.388929] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.432790] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.501957] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.544431] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.616206] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.659308] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.748072] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   57.790043] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   93.312136] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[   93.528090] [fglrx] interrupt source 20000400 successfully disabled!
[   93.528095] [fglrx] enable ID = 0x00000000
[   93.528098] [fglrx] Receive disable interrupt message with irqEnableMask: 20000400; dwIRQEnableId: 0000000a
[   93.528107] [fglrx] interrupt source ff00002d successfully disabled!
[   93.528108] [fglrx] enable ID = 0x00000000
[   93.528110] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002d; dwIRQEnableId: 00000009
[   93.528116] [fglrx] interrupt source ff00002c successfully disabled!
[   93.528118] [fglrx] enable ID = 0x00000000
[   93.528120] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002c; dwIRQEnableId: 00000008
[   93.528126] [fglrx] interrupt source 00000040 successfully disabled!
[   93.528127] [fglrx] enable ID = 0x00000000
[   93.528129] [fglrx] Receive disable interrupt message with irqEnableMask: 00000040; dwIRQEnableId: 00000007
[   93.528135] [fglrx] interrupt source 60000001 successfully disabled!
[   93.528137] [fglrx] enable ID = 0x00000000
[   93.528139] [fglrx] Receive disable interrupt message with irqEnableMask: 60000001; dwIRQEnableId: 00000006
[  100.303985] [fglrx] PCIe has already been initialized. Reinitializing ...
[  100.556641] [fglrx] Reserve Block - 0 offset =  0X1fffc000 length = 0X4000
[  100.556646] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  100.556649] [fglrx] Reserve Block - 2 offset =  0Xff7f000 length = 0X80000
[  100.612406] [fglrx] interrupt source 60000001 successfully enabled
[  100.612413] [fglrx] enable ID = 0x00000006
[  100.612423] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[  100.612485] [fglrx] interrupt source 00000040 successfully enabled
[  100.612487] [fglrx] enable ID = 0x00000007
[  100.612491] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[  100.619311] [fglrx] interrupt source ff00002c successfully enabled
[  100.619314] [fglrx] enable ID = 0x00000008
[  100.619320] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[  100.619360] [fglrx] interrupt source ff00002d successfully enabled
[  100.619362] [fglrx] enable ID = 0x00000009
[  100.619365] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[  100.619397] [fglrx] interrupt source 20000400 successfully enabled
[  100.619399] [fglrx] enable ID = 0x0000000A
[  100.619402] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[  111.701243] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list
[  111.782842] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  111.825040] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  111.900511] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  111.945032] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  112.100391] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  112.146014] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  112.347335] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[  112.390810] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list

---

### Post by handy on 2008-01-10
I used [***_Envy_***]("http://www.albertomilone.com/nvidia_scripts1.html") to install the drivers for my current model 24" iMac, with the ATi Radeon HD 2600 Pro / 256 Mb GPU / Ram combination.  I'm using the 64 bit Ubuntu 7.10 too.

It worked flawlessly & I can't recommend it high enough!

It is written & maintained by Alberto Milone, our resident GPU guru.

---

### Post by cyberdork33 on 2008-01-10
It sounds like your drivers are installed fine.
Compositing and OpenGL don't play nice. Disable desktop effects before playing 3D games and such and the flicking problem will go away.

---

### Post by Ricardo Matos on 2008-01-14
> **cyberdork33 said:**
> It sounds like your drivers are installed fine.
Compositing and OpenGL don't play nice. Disable desktop effects before playing 3D games and such and the flicking problem will go away.

Hi there!

First of all, thank you for your reply s...

After disabling desktop effects the flicking was gone. I can run google earth and enable the visual effects of RhytmBox.

Unfortunately i still cannot play Open Arena and Alien Arena, i always get a black screen and a message from my monitor complaining about the resolution is not the ideal one, and it recommends 1440X900 which is the resolution i have by default, meanwhile i can hear the game sounds in background.

Whenever this happens i can not go back to the desktop environment and i have to reboot. 

It sounds like these games use a different resolution and this cause problems. I actually played a bit it different resolution sets and in a  time only i could seen the alien arena game in a small square on the upper left of my monitor using a different resolution. However i could not replicated a second time.

All resolutions are defined fine on Xorg i believe and i'm using a Samsung monitor 920 nw.

I have also reinstalled everything with Envy just in case of something could be missing...

Any ideas?

Thanks in advance....

---


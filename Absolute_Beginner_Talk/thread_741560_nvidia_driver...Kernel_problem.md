---
title: "nvidia driver...Kernel problem"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by dev48 on 2008-03-31
ok well im trying to install my nvidia driver for my 8800 gtx. im using ubuntu 7.10.

it  tries to connect to the nvidia site and downloaded it but it gets a connection error for some reason.

help? sorry if im not being clear enough let me no ill try to be a little more specific.

---

### Post by dark_harmonics on 2008-03-31
maybe some detail about your connection method, and whether you can connect to other websites would help start of the thread a bit.

---

### Post by dev48 on 2008-03-31
yeah im on my ubuntu boot right now...could it possibly have something to do with closing the x server?

my steps so far

press ctrl+alt+f1
login as root
init 1
then sh NVIDIA-Linux-x88-169.12-pkg1.run

---

### Post by rkd on 2008-04-01
I take it that you are trying to follow some directions you found somewhere about how to install the Nvidia driver.  It probably would help if you told us where to find those directions, so we could look at them and understand what they are doing and what requirements they have.

Also, let me ask: Are you sure you need to get the Nvidia drivers that way?  Have you tried going to System -> Administration -> Restricted Drivers Manager and enabling the driver that Ubuntu has there for you?  I'll admit that I don't keep up with all the versions of graphics cards, so maybe the driver Ubuntu supplies there isn't suitable for some reason, but if you didn't know about it, I wanted to point it out.

---

### Post by dev48 on 2008-04-01
thank you...seeing that is now my second day using linux i did not know about that im installing it now...hopefully it will work and allow dual monitors! thanks

---

### Post by PmDematagoda on 2008-04-01
I highly doubt if using the Restricted Drivers Manager to install the Nvidia driver would fix your problem, especially since you have an 8800GT which is rather poorly supported by the current nvidia-glx package.

Can you please provide some details about your internet connection?

---

### Post by dev48 on 2008-04-01
yeah..

verizon fios 15 down 5 up

wired connection, not wireless.
have not had any problems with it....could going into the text only command thing or closing the x server possibly do anything with it?....


side note...once the installation fails because it cant download the kernel my computer basically freezes and i have to restart
```
dia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Apr  1 20:37:58 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by dev48 on 2008-04-01
sorry for the double post but this is really nagging me

---

### Post by forrestcupp on 2008-04-01
If you can get to your desktop, try using [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to install the latest drivers.  It's a script that automatically downloads and installs the latest drivers.  If you try this, choose the option to uninstall the nvidia drivers first so you can start with a clean slate.  Then use it to install the drivers.  It's much, much easier this way than trying to do it all manually.

---

### Post by rkd on 2008-04-01
The complaint about not finding libc might be solved by installing the build-essentials package:
```
sudo apt-get install build-essentials
```Or do the install via Synaptic if you prefer.

I don't know what the complaint about not finding precompiled kernel interface is about.  There is a chance that you could fix that by installing the linux headers for your kernel version:
```
sudo apt-get install linux-headers-`uname -r`
```I'm not sure that is what it is looking for, but it isn't very hard to install them and see whether that makes the complaint go away.  By the way, the "`" character used around the uname -r part of that command is the character to the left of the number "1" key on the keyboard.

When you told it to attempt to download a kernel interface, it said that download.nvidia.com was an unknown host.  That seems to indicate that your internet access wasn't working at that time.  I wonder whether that init 1 command you entered caused the networking to get shut down.  I suspect you are following some directions that aren't suitable for using on an Ubuntu system.  If you would point out where you got those directions, we might be able to figure out whether they are suitable and if not, how to change them.

And I see forrestcupp suggested that you try Envy.  That certainly is a lot simpler. There have been reports that using Envy causes problems when you go to upgrade, though. Others have said it doesn't cause problems.  Hard to know who to believe.

---

### Post by angryfirelord on 2008-04-01
If you can run the script, you're on the right track. However, skip the download part becuase 99.9999% of the time it's not going to have one for your system. Have it build the kernel module and let it edit your xorg at the end (just press yes). Reboot and the nvidia module should be working.

If you get a compiler error, you may have to install gcc & g++.
```
sudo apt-get install gcc g++
```

---

### Post by dev48 on 2008-04-02
ok i got it installed thanks...i used the Envy tool...But now when i try to enable my second monitor using the nvidia settings thing i have to save my x server config file....when i try to press save i keep getting this:

```
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.
```

i dont get why this is happening...i have "merge with existing" file selected

---

### Post by PmDematagoda on 2008-04-03
That maybe because you are running nvidia-settings without root permissions, open nvidia-settings by entering:-
```
gksudo nvidia-settings
```
and then try again.

---


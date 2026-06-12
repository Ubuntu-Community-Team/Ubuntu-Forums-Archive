---
title: "isight will not work macbook 4,1"
date: 2009-05-25
forum: Apple Hardware Users
---

### Post by monsterfromthefuture on 2009-05-25
I'm completely new to linux and ubuntu.  Ive followed these instructions to get isight to work <https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight>
but it will not make the webcam function. 

I cant seem to get past step 2 and this is what the terminal says

                                 matt@matt-laptop:~$ sudo apt-get install isight-firmware-tools
 [sudo] password for matt:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Recommended packages:
   linux-uvc-source
 The following NEW packages will be installed:
   isight-firmware-tools
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
 Need to get 0B/30.0kB of archives.
 After this operation, 229kB of additional disk space will be used.
 Preconfiguring packages ...
 Selecting previously deselected package isight-firmware-tools.
 (Reading database ... 174600 files and directories currently installed.)
 Unpacking isight-firmware-tools (from .../isight-firmware-tools_1.2-2_i386.deb) ...
 Processing triggers for hal ...
 Regenerating hal fdi cache ...
  * Restarting Hardware abstraction layer hald                            [ OK ]  
 Processing triggers for man-db ...
 Setting up isight-firmware-tools (1.2-2) ...
 

 matt@matt-laptop:~$ sudo cp AppleUSBVideoSupport /lib/firmware/
 cp: cannot stat `AppleUSBVideoSupport': No such file or directory


Any help, I love ubuntu but I need skype for work.

---

### Post by cyberdork33 on 2009-05-26
> **monsterfromthefuture said:**
> ```
matt@matt-laptop:~$ sudo cp AppleUSBVideoSupport /lib/firmware/
 cp: cannot stat `AppleUSBVideoSupport': No such file or directory
```

As stated in the wiki page, you need to get the AppleUSBVideoSupport file off your OS X partition.

Then, when you run the cp command, you have to be in the directory that you placed this file, otherwise you will have to modify the command.
Let's say you put it on your Ubuntu desktop. You need to navigate to the desktop directory in the terminal:

```
cd ~/Desktop
``` (PS the ~ is a shortcut that means your user home directory)

now that you are in the folder that contains the AppleUSBVideoSupport file, you can copy it to /lib/firmware with the command that is currently failing.
```
sudo cp AppleUSBVideoSupport /lib/firmware/
```

---

### Post by monsterfromthefuture on 2009-05-28
Thanks for responding.  


cd ~/Desktop So do I paste this in the terminal after step 1?  I'm completly new to linux and am a newb.


Also step 4 confuses me the more I look at it.  How do I locate this file and copy it?  I know it's a simple question but I'm a complete newb when it comes to linux and ubuntu.

Any help is greatly appreciated!

---

### Post by monsterfromthefuture on 2009-05-28
Solved! Thanks for the Help!

---


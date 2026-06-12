---
title: "Wine configuration"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-01-10
Can any expert help me to configure wine. Trying to with winecfg, it displays a window which when i try to configure it I cannot see apply button to click on. If i try and do it blindly i get no drives addedd on, any help.
below is what i get in terminal

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/sn0m'
sn0m@sn0m-laptop:~$ 

thanks
Koli:confused:

---

### Post by scrooge_74 on 2007-01-10
did you first type wine and after did you type winecfg?

---

### Post by sn0m on 2007-01-10
> **scrooge_74 said:**
> did you first type wine and after did you type winecfg?

either, winecfg or wine winecfg, still the same result.](*,)

---

### Post by scrooge_74 on 2007-01-10
It seems you have some weird video problem, what type of video card you have?  Also did you try using the winehq repository, today there was an update to the wine package, it could help you

---

### Post by david_kt on 2007-01-11
> **sn0m said:**
> 
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/sn0m'
sn0m@sn0m-laptop:~$ 

thanks
Koli:confused:

Did you ever run "sudo wine"?

Regards,
DK

---

### Post by sn0m on 2007-01-11
> **david_kt said:**
> Did you ever run "sudo wine"?

Regards,
DK

I have run sudo wine, no good resilts.
I have a ATI mobility Radeon 200, build in card. My comp is compaq pressario V5000.
thanks
koli

---

### Post by scrooge_74 on 2007-01-11
Even if it worked you should not run wine with root privileges


Did you get the ATI drivers installed properly?

---

### Post by sn0m on 2007-01-11
> **scrooge_74 said:**
> Even if it worked you should not run wine with root privileges


Did you get the ATI drivers installed properly?

I haven't install ati drivers as such. I thought ubuntu would do that automatically. Screen resolution seems fine, don't know, should i install drivers, there's nothing ati wise in synaptic.
I'd appreciate if u could help me with t. My card is ati radeon expres 200.
attached is the output from device manager.
 
Thanks
Koli

---

### Post by scrooge_74 on 2007-01-11
You sould check this information [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html) what happens is that 
Ubuntu will install open source drivers for Nvidia and ATI, but then you dont get 3D acceleration and a few other things your cards is capable of.  

Example: if you use a 3D screensaver, chances are is going to show like very slow or may even crash.

After installing my Nvidia binaries my laptop showed a great improvement, and I can also play 1st person shooter games that couldnt before

---

### Post by david_kt on 2007-01-11
> **sn0m said:**
> I have run sudo wine, no good resilts.
I have a ATI mobility Radeon 200, build in card. My comp is compaq pressario V5000.
thanks
koli

I think that is the problem. Wine should not bu run using sudo. May be you shoud try to remove wine completely, and then install again and run wine without sudo.

Regards,
DK

---

### Post by sn0m on 2007-01-11
> **david_kt said:**
> I think that is the problem. Wine should not bu run using sudo. May be you shoud try to remove wine completely, and then install again and run wine without sudo.
hen error
Regards,
DK

Mate I'v done it all. Ati is fine, i have installed drivers with easyubuntu and can play 3d games.
I have uninstalled wine wint Synaptic P M and re-install everything related to wine as well as wine itsel. Triied Winecfg, same thing says havn't got drive C, add it on, which i have done and then ng toerror.
This is the output from terminal after trying t configutr it:

Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/sn0m', starting in the Windows directory.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\sn0m\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\sn0m\\Desktop"'.
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/sn0m'
sn0m@sn0m-laptop:~$ 

Seems to be a bit difficult to get it working i guess.
thanks
koli

---

### Post by scrooge_74 on 2007-01-11
yes it seems very odd, never had that kind of trouble every time I go into a terminal window and I type winecfg it comes out and I can edit the config no problem.

I have install programs no problem from CDs (as long as wine supports it).

Sorry I cant be of any more help

---

### Post by scrooge_74 on 2007-01-12
> **sn0m said:**
> I have run sudo wine, no good resilts.
I have a ATI mobility Radeon 200, build in card. My comp is compaq pressario V5000.
thanks
koli

I was toying around with my wine install today. And gave me around some error messages.

from a terminal window in your home folder do this

sudo apt-get remove wine
sudo rm -rf .wine
sudo apt-get install wine

then do

winecfg

---

### Post by sn0m on 2007-01-13
> **scrooge_74 said:**
> I was toying around with my wine install today. And gave me around some error messages.

from a terminal window in your home folder do this

sudo apt-get remove wine
sudo rm -rf .wine
sudo apt-get install wine

then do

winecfg

hey buddy thanks, it worked fine
greetings
kolli

---


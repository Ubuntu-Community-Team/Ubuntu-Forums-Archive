---
title: "Add/Remove problem"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by slibuntu on 2006-08-20
Hey, i'm having a problem with Applications->Add/Remove... whenever i try to insall/uninstall anything, it just doesnt work, i click ok and it just closes and i click apply and it reopens as if i hadn't told it to do anything! Its not a huge problem, i can use the command line for this but i'm just trying to find out what the problem is
Thanks,
Shane

---

### Post by aysiu on 2006-08-20
To help people diagnose this, can you post the terminal output of this command when you try to install something? ```
gksudo gnome-app-install
```

---

### Post by slibuntu on 2006-08-20
Heres the output, somthing doesn't look right!


warning: could not initiate dbus
** (gnome-app-install:5261): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:5261): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5261): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5261): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:5261): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

---

### Post by aysiu on 2006-08-20
Okay. [Something is seriously wrong.](http://www.google.com/search?hl=en&q=HtmlUtil-CRITICAL+**%3A+html_stream_cancel%3A+assertion+%60stream-%3Ecancel_func+%21%3D+NULL%27+failed&btnG=Google+Search)

---

### Post by slibuntu on 2006-08-20
That link you've given turns up nothing, whats wrong?

---

### Post by LeslieL on 2006-08-20
I tried "gksudo gnome-app-install" and got the same errors as you, even though my gnome-app-install is working just fine. This problem turns up sometimes when a previous attempt to run the app-installer terminates abnormally, leaving a lock file in place. The simplest thing to try might be just to reboot, which should get rid of the lock file; "sudo apt-get update" might help, but I don't think so.

---

### Post by aysiu on 2006-08-20
> **slibuntu said:**
> That link you've given turns up nothing, whats wrong?
It means no one else has experienced that exact error... or at least posted about it online.

---

### Post by slibuntu on 2006-08-21
Ah i see what your saying, from trawling around, i couldn't find anything, i've tried rebooting and sudo apt-get install, i don't think they work, but thanks anyway!

---

### Post by az on 2006-08-21
From the terminal, what does 

sudo apt-get -f install

do for you?

---

### Post by slibuntu on 2006-08-21
As soon as i get back to my own machine i'll try that, thanks

---

### Post by slibuntu on 2006-08-21
That gives me
"Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded."
Pretty normal output, and i've just realised the update GUI installer isn't working either, in the same way, everything looks fine, but it doesnt install things when i tell it to. 
Thanks everyone, your help is greatly appreciated

---

### Post by slibuntu on 2006-08-21
And also System->Administration->Synaptic Package Manager wont even start up.
I only installed this distro 2 weeks ago!

---

### Post by az on 2006-08-22
> **slibuntu said:**
> And also System->Administration->Synaptic Package Manager wont even start up.
I only installed this distro 2 weeks ago!

So, what error do you get when you run synaptic from the terminal?

sudo synaptic


Maybe that will be more telling.

---

### Post by slibuntu on 2006-08-22
You are a smart man, this could be the key

synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

So do i just have to download that file and put it into the appropriate place?

---

### Post by az on 2006-08-22
sudo apt-get install libvte4

The question is, what happened to that package?  Do you have a bad hard drive?  Were some packages improperly installed (silent failure?)

---

### Post by slibuntu on 2006-08-22
I did install Limewire recently, despite a friend urging me not to,i have uninstalled it though. Also my install of easyubuntu didnt come off perfectly right, might that have something to do with it?

---

### Post by slibuntu on 2006-08-22
Ok i did that terminal command and it came back like this, i'm confused!
Reading package lists... Done
Building dependency tree... Done
libvte4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo synaptic is still:
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

---

### Post by az on 2006-08-22
Ooops!

sudo apt-get install --reinstall libvte4


Sorry...

---

### Post by slibuntu on 2006-08-22
Ok it couldnt be downloaded, it might be cos i just am using the original sources.list and it doesn't include the proper repository, my sources.list is like this:

deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by az on 2006-08-22
> **slibuntu said:**
> Ok it couldnt be downloaded, it might be cos i just am using the original sources.list and it doesn't include the proper repository, my sources.list is like this:

deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper main restricted


You are missing 
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) dapper main restricted

for some reason...

EDIT:  Actually, you have main further down.  Anyway, did you do an 
apt-get update
first?

That package is in main.

---

### Post by slibuntu on 2006-08-22
I dunno whats up! It still doesn't work, the readout i get is:
shane@shane-laptop:~$ sudo apt-get install --reinstall libvte4
Reading package lists... Done
Building dependency tree... Done
Reinstallation of libvte4 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by slibuntu on 2006-08-23
Solution found here : [http://ubuntuforums.org/showthread.php?t=239238](http://ubuntuforums.org/showthread.php?t=239238). Thanks for your help everyone!

---


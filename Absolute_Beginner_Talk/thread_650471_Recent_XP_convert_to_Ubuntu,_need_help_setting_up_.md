---
title: "Recent XP convert to Ubuntu, need help setting up wifi"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Crispygb on 2007-12-26
Hello
I've just installed Ubuntu 7.10 on my Acer laptop, after deciding to switch from XP. I'm now trying to set up the wifi connection but have no real idea what to do.  I've tried to follow the guidance docs but this doesn't seem to work.  Please can someone take me through it step by step. There is no Device Manager facility listed under the Administration bit on the toolbar so I don't know if this is a problem.
I'd really welcome your help.
Thanks

---

### Post by overdrank on 2007-12-26
> **Crispygb said:**
> Hello
I've just installed Ubuntu 7.10 on my Acer laptop, after deciding to switch from XP. I'm now trying to set up the wifi connection but have no real idea what to do.  I've tried to follow the guidance docs but this doesn't seem to work.  Please can someone take me through it step by step. There is no Device Manager facility listed under the Administration bit on the toolbar so I don't know if this is a problem.
I'd really welcome your help.
Thanks

HI and welcome, then network is located under system, administration. If you can tell us your wireless device and if you do not know then use this command in the terminal ```
lspci
```the terminal is located under applications, accessories.

---

### Post by Crispygb on 2007-12-26
Hello
Thanks for helping me out, I really appreciate it.
No wireless device is showing under the Administration/Network option.
Wireless device is Atheros AR5006EG.
Regards

---

### Post by jimrz on 2007-12-26
have a look at [[COLOR="Sienna"]**_ this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=649019&highlight=AR5006EG") thread  seems to be the same sort of card you have

---

### Post by overdrank on 2007-12-26
> **Crispygb said:**
> Hello
Thanks for helping me out, I really appreciate it.
No wireless device is showing under the Administration/Network option.
Wireless device is Atheros AR5006EG.
Regards

And if the above does not help look here
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
It helped me with my acer 3680.

---

### Post by Crispygb on 2007-12-27
> **overdrank said:**
> And if the above does not help look here
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
It helped me with my acer 3680.


Thanks to both for that.

Under

"have a look at  this thread seems to be the same sort of card you have"
it says:
goto system-administration-Windows Wireless Drivers


click on Install New Driver

click on location then browse to where you extracted your windows file

Select the file with extension .inf

click on Open then click on Install

you can close Windows Wireless Drivers after you see a confirmation that hardware is present.


There is no Windows Wireless Drivers option under System-Administration so how can I install the new drivers?

Thanks

---

### Post by zero-9376 on 2007-12-27
you will need to install ndisgtk to have that option in your menu.

sudo apt-get install ndisgtk
OR use add/remove or synaptic for GUI methods

---

### Post by Crispygb on 2007-12-27
> **zero-9376 said:**
> you will need to install ndisgtk to have that option in your menu.

sudo apt-get install ndisgtk
OR use add/remove or synaptic for GUI methods

Thanks
I get E: Couldn't find package ndisgtk' on the sudo bit

As I'm an idiot I don't understand what to do with the other options you suggested!
Any help would be appreciate. Sorry I'm such a numbskull

---

### Post by zero-9376 on 2007-12-27
system>administration>software sources enable universe then retry the command

regarding the other methods, synaptic (system>admin>synaptic package manager) is a nice GUI for searching and installing packages

---

### Post by Crispygb on 2007-12-27
> **zero-9376 said:**
> system>administration>software sources enable universe then retry the command

regarding the other methods, synaptic (system>admin>synaptic package manager) is a nice GUI for searching and installing packages

No.
Tried the enable thing, that made no difference, got the same message when I tried the command.
Synaptic manager - presumably I just search for ndisgtk, well I did that and couldn't find anything....

excuse my ignorance but what does GUI mean?

thanks again

---

### Post by overdrank on 2007-12-27
> **Crispygb said:**
> No.
Tried the enable thing, that made no difference, got the same message when I tried the command.
Synaptic manager - presumably I just search for ndisgtk, well I did that and couldn't find anything....

excuse my ignorance but what does GUI mean?

thanks again

Hi and GUI, I believe is Graphical User Interface. And could you post the output of this command
```
 cat /etc/apt/sources.list
``` And maybe we can help with your repos

---

### Post by Crispygb on 2007-12-27
Right, I've successfully installed the driver and it says the hardware is present.
What's all this stuff about blacklist? I tried something and nothing happened.  

[COLOR="Red"]"then it's time for commandline:

we have to blacklist ath_pci

so run

gksu gedit /etc/modprobe.d/blacklist

and add the following:



blacklist ath_pci at the end of file[/COLOR]

what does end of the file mean?  that sort of text file that comes up after I've run that command or does it go at the end of the command?
Sorry, I'm easily confused

[COLOR="Red"]then enter the following commands one by one:

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

then the last one: gksudo gedit /etc/modules
and add: ndiswrapper at the end of file
[/COLOR]
please note:

In my case after the last command I rebooted but nothing happened, so I turned off the PC the turn it on back again then I was able to see the Orange Light of my wireless, then after loging in every thing worked super fine.

Good luck

Salam Alikoum
__________________

---

### Post by Crispygb on 2007-12-27
> **overdrank said:**
> Hi and GUI, I believe is Graphical User Interface. And could you post the output of this command
```
 cat /etc/apt/sources.list
``` And maybe we can help with your repos

cat /etc/apt/sources.list
# 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by jimrz on 2007-12-27
looks like you have the universe repo in your sources.list. I checked Synaptic and it came up on mine showing in Networking-universe. After enabling new repos you need to reload synaptic (button on top toolbar) or do a 
```
sudo apt-get update
```
 before it will show the new packages. If you did not, try Synaptic again, you should find it now.

---


---
title: "Installing always gives me an error..."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Leela on 2008-01-01
When I want to install something on Ubuntu Gutsy Gibbon, I always get the same error, which is:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

```
Anyone willing to help?

Thanks

---

### Post by bigken on 2008-01-01
go into synaptic and see if there are any broken packages if there is remove them


System/Administration/Synaptic Package Manager

Use the custom filters select broken

---

### Post by Leela on 2008-01-01
There aren't any broken packages...

---

### Post by bigken on 2008-01-01
try running 

sudo apt-get update

sudo apt-get upgrade

---

### Post by Leela on 2008-01-01
Well, I did some more research, and I added 2 lines:
```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```
Then i did 
```

sudo apt-get update

sudo apt-get upgrade
```
And it was like updating for half an hour, after that, I had to reboot, and it killed my Compiz fusion, but I was able to install *SOME* applications, others still give errors like
```

libemeraldengine0:
 Depends: libwnck18 (>=2.15.90) but it is not installable
 Depends: emerald but it is not going to be installed

```

---

### Post by Leela on 2008-01-02
Bump...

---

### Post by bapoumba on 2008-01-02
There is no package libwnck18 for gutsy. Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Leela on 2008-01-02
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy 

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## Avant Window Navigator
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```

---

### Post by Bliepo32 on 2008-01-02
Try:

```

sudo apt-get --fix-missing

```

---

### Post by Leela on 2008-01-02
This is not a right command, it gives me just the help of apt-get...

---

### Post by RomeReactor on 2008-01-02
Hi. Open Synaptic (System->Administration->Synaptic), there go to "Settings->Repositories" and on the first tab (Ubuntu Software) check all the boxes except "Source" and "CD-ROM"; you have most of your sources commented out (disabled) probably due to performing Ubuntu's installation without internet access.

One thing to note is that you have a few Feisty repositories even though you now have Gutsy:
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
Please remove them in the second tab (Third-Party Software). You really shouldn't have mixed repositories; try finding the appropriate version of those (for Gutsy). Every time you upgrade from one version of Ubuntu to the next, you should disable any repositories added by you.

Once you have finished all that, close that window and, still in Synaptic, press the blue "Reload" button.

Hope this helps.

---

### Post by bapoumba on 2008-01-02
Please backup your sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

Edit the file:
```
sudo nano /etc/apt/sources.list
```

In the file, remove the **#** in front of the lines starting with **deb** for the gutsy repos (and these lines only. I would keep the backports commented though).

Now **remove** all these lines at the end of the file:
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy 
```

Save the file with CTRL-O
Exit nano with CTRL-X

If you  are not sure, please post the modified file so we have a look before you continue:
```
cat /etc/apt/sources.list
```

If you are sure you have only gutsy repos, please run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Leela on 2008-01-02
Thanks ppl, I now found it, although my compiz-fusion is still not working >_>
EDIT:
When i type in terminal: 'Compiz', My screen flickers a bit, and then I get this:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 1002:5b63 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

---

### Post by bapoumba on 2008-01-02
> **Leela said:**
> Thanks ppl, I now found it, although my compiz-fusion is still not working >_>
You're welcome.
What kind of video card do you have?

---

### Post by Leela on 2008-01-02
ATI (I think)

---

### Post by RomeReactor on 2008-01-02
Please post the output of this command:
```
sudo lshw -C display
```

If it is an ATI card, maybe you need to install xserver-xgl.

---

### Post by Leela on 2008-01-02
```
*-display:0             
       description: VGA compatible controller
       product: RV370 [Sapphire X550 Silent]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 secondary [Sapphire X550 Silent]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:04:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
```

---

### Post by RomeReactor on 2008-01-02
Have you tried enabling the proprietary dirvers from "System->Administration->Restricted Drivers Manager"? I don't have an ATI card and don't know much about them, but if you already have the restricted drivers, you can try installing xserver-xgl and see if that helps:
```
sudo apt-get install xserver-xgl
```
after it finishes installing, press CTRL+ALT+BACKSPACE to restart the display, and then see if you can enable Compiz.

However, I recommend you wait until someone else can give you more accurate advice.

---


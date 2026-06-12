---
title: "Package installation problems"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by mmmpancakes on 2007-04-07
I'm setting up Ubuntu with KDE on my laptop, and the first thing I did was install EasyUbuntu. That seemed to install Ok.

But now I'm trying to install the ndiswrapper in Ubuntu via Synaptic. However, during the installation process I get an error box with the following message:


E: cpio: subprocess post-installation script returned error exit status 2
E: ubuntu-standard: dependency problems - leaving unconfigured
E: ubuntu-base: dependency problems - leaving unconfigured

Any advice you have would be greatly appreciated.

---

### Post by chamberlain2006 on 2007-04-07
EasyUbuntu doesn't always install programs properly.  Running "sudo apt-get install -f" should fix the dependency problems, but I wouldn't recommend using EasyUbuntu, as it can do some whacky stuff.

---

### Post by Maestro23 on 2007-04-07
Ndiswrapper Wiki: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

*I believe version 1.9 is available now. Search your repositories.

---

### Post by mmmpancakes on 2007-04-07
> **chamberlain2006 said:**
> EasyUbuntu doesn't always install programs properly.  Running "sudo apt-get install -f" should fix the dependency problems, but I wouldn't recommend using EasyUbuntu, as it can do some whacky stuff.

Ok I just did that, but the output seems to indicate an error:

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cpio (2.6-10ubuntu0.2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format errordpkg: error processing cpio (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cpio; however:
  Package cpio is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-standard; however:
  Package ubuntu-standard is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cpio
 ubuntu-standard
 ubuntu-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chamberlain2006 on 2007-04-07
Well I don't know what the problem with cpio is.  I've never used it, but when I looked into it I don't really know why you'd need it.  If it's not important to you, remove it "sudo apt-get remove cpio"

---

### Post by mmmpancakes on 2007-04-07
> **chamberlain2006 said:**
> Well I don't know what the problem with cpio is.  I've never used it, but when I looked into it I don't really know why you'd need it.  If it's not important to you, remove it "sudo apt-get remove cpio"

Similarly scary output from this command. I haven't agreed yet -- safe to do so?

The following packages will be REMOVED:
  cpio gnome-power-manager gnome-session gnome-volume-manager hal
  hal-device-manager hwdb-client initramfs-tools kubuntu-desktop linux-386
  linux-image-2.6.15-23-386 linux-image-2.6.15-28-386 linux-image-386
  linux-restricted-modules-2.6.15-23-386
  linux-restricted-modules-2.6.15-28-386 linux-restricted-modules-386
  lvm-common lvm2 mdadm pcmciautils ubuntu-base ubuntu-desktop ubuntu-minimal
  ubuntu-standard udev update-notifier usplash
0 upgraded, 0 newly installed, 27 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 182MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 96055 files and directories currently installed.)
Removing ubuntu-base ...
Removing ubuntu-standard ...
Removing linux-386 ...
Removing linux-restricted-modules-386 ...
Removing linux-restricted-modules-2.6.15-28-386 ...
Removing linux-image-386 ...
Removing linux-image-2.6.15-28-386 ...

  You are running a kernel (version 2.6.15-28-386) and attempting to remove
  the same version. This is a potentially disastrous action. Not only
  will /boot/vmlinuz-2.6.15-28-386 be removed, making it impossible to boot
  it, (you will have to take action to change your boot loader to boot
  a new kernel), it will also remove all modules under the directory
  /lib/modules/2.6.15-28-386. Just having a copy of the kernel image is not
  enough, you will have to replace the modules too.

    I repeat, this is very dangerous. If at all in doubt, answer
    no. If you know exactly what you are doing, and are prepared to
    hose your system, then answer Yes.
Remove the running kernel image (not recommended) [No]?

---

### Post by mmmpancakes on 2007-04-07
Uninstalling cpio as advised just cratered my entire system, and I had to reinstall the OS.

---

### Post by chamberlain2006 on 2007-04-08
Was the warning not enough?  I wasn't sure but when it tells you something like that it's best to take it's advise and not mine.

---

### Post by mmmpancakes on 2007-04-10
> **chamberlain2006 said:**
> Was the warning not enough?  I wasn't sure but when it tells you something like that it's best to take it's advise and not mine.

I selected "no" and it still crashed. Running the code you gave me hosed the entire system - it wasn't my answer to the warning that did it. Just FYI.

---


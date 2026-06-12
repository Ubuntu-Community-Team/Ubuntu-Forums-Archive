---
title: "Installing VMplayer"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by boz_1812 on 2007-09-30
Hi,
I managed to install VMplayer yesterday and open a pre-built WIN XP virtual machine.  All worked OK.
Today, I tried to launch Vm player and it failed.  I couldn't make any sense of the errors, so decided to uninstall, then reinstall.
The uninstall seemed to work OK.
When I try to run the installer, it fails with the following message,
:> sudo ./vmware-install.pl
"The following VMware kernal modules have been found on your system that were not installed by the VMware installer.  Please remove them then run the installer again.

- vmblock
- vmmon
- vmnet

Execution aborted."

I'm not sure what they are, where they are, and how to get rid of them.
Thinking about it now, I suspect that it may have been a problem trying to connect to my ADSL connection because that seems to be the only difference between yesterday (connected) and today (not connected).  If not that, then I don't know.
Thanks.

---

### Post by julian67 on 2007-09-30
> **boz_1812 said:**
> Hi,
I managed to install VMplayer yesterday and open a pre-built WIN XP virtual machine.  All worked OK.
Today, I tried to launch Vm player and it failed.  I couldn't make any sense of the errors, so decided to uninstall, then reinstall.
The uninstall seemed to work OK.
When I try to run the installer, it fails with the following message,
:> sudo ./vmware-install.pl
"The following VMware kernal modules have been found on your system that were not installed by the VMware installer.  Please remove them then run the installer again.

- vmblock
- vmmon
- vmnet

Execution aborted."

I'm not sure what they are, where they are, and how to get rid of them.
Thinking about it now, I suspect that it may have been a problem trying to connect to my ADSL connection because that seems to be the only difference between yesterday (connected) and today (not connected).  If not that, then I don't know.
Thanks.

You need to uninstall the kernel modules. I haven't used the VMware installer for quite a while but I believe it can be used to completely uninstall the application and the kernel modules it built. Read the VMplayer install doc and readme. If you don't have any success this way you can check out the command modprobe which is used to add modules to the kernel. It can also be used to remove them with the option -r. Read the man page.

If I were you once I had this dealt with I would not install VMplayer but instead install VMware Server from the commercial repository (it's also no cost) or have a look at VirtualBox which is free and has some very nice features like unlimited snapshots which you don't get from VMware without handing over the cash.

---

### Post by n3tfury on 2007-09-30
sorry, can't help you with your problem, but just thought i'd toss up another vote for Virtualbox.

[http://ubuntuforums.org/attachment.php?attachmentid=44578&d=1190936637](http://ubuntuforums.org/attachment.php?attachmentid=44578&d=1190936637)

---

### Post by boz_1812 on 2007-09-30
Thanks Guys.  
I'll try the Vmplayer uninstall first, just to clean up the mess.  For a reinstall, I'll have a look at VMserver; don't know much about it, but VirtualBox sounds interesting.  I use VM Workstation on my work PC and the snapshot functionality is very handy.
As you've probably guessed I'm struggling to get my head around Ubuntu, but I'll keep at it.
Thanks again for your help.

---

### Post by boz_1812 on 2007-10-05
I've been away for a few days holiday, so haven't had a chance to try your suggestions until today.  

For my first attempt to uninstall vmplayer, I followed instructions I got from [https://help.ubuntu.com/community/InstallingVmPlayer](https://help.ubuntu.com/community/InstallingVmPlayer)
It says that an install will fail if it detects a current installation and goes on to explain how to remove that installation by running the command,
$ sudo rm -rf /etc/vmware
then running the installer again.
I did that, but a reinstall failed with the message about removing the three vm kernal modules.

I've checked the uninstall process from the Vmware documentation, and it gave very little detail.
"To uninstall a tar installation of VMware Player on a Linux host
If you used the tar installer to install VMware Player, remove the software from your system by
entering
      vmware-uninstall.pl"

This won't work because it won't find the tar installer because everything under /etc/vmware has been deleted.
 
Bob:~/programs/vmware-player-distrib$ sudo ./bin/vmware-uninstall.pl
Uninstalling the tar installation of VMware Player.

Unable to find the tar installer database file (/etc/vmware/locations)

Execution aborted.
------------
Catch 22!  I can install and I can't uninstall.

I had a look at the man page for modprobe.  I tried the following commands, but no joy.
Bob:~/programs/vmware-player-distrib$ modprobe -l vmblock
/lib/modules/2.6.20-16-generic/misc/vmblock.ko
Bob:~/programs/vmware-player-distrib$ modprobe -r /lib/modules/2.6.20-16-generic/misc/vmblock.ko
FATAL: Module /lib/modules/2.6.20_16_generic/misc/vmblock.ko not found.

Maybe I haven't got the command syntax right?
I've pretty much decided to go with VirtualBox, so I guess its not critical to remove this dud install, but it would be nice to get rid of it.
Thanks.

---

### Post by hyper_ch on 2008-01-07
Why don't you download and install VmWare server? It's also free and it's in the Gutsy Canonical repos.

---

### Post by Jhongy on 2008-01-07
Be cautious with rm -rf as suggested above! There's no need for the -f option, and the -r option is only needed if the kernel module you are trying to delete is in a folder.

---

### Post by AzureCerulean on 2008-03-26
sudo rm -rf /lib/modules/$(uname -r)/misc/vm*

will remove the modules.  

then search through the install scripts  and change the following 


From:
if (scalar(@modules) > 0) {
To:
if (scalar(@modules) == 0) {

this should work smoothly..

if not ...
 use the vmware-uninstall script

you may have to make the same chages to this script as well..

and then reinstall..

cross fingers and pray....

Good Luck.

---


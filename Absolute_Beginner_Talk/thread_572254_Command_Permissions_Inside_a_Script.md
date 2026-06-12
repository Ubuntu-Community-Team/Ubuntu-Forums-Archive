---
title: "Command Permissions Inside a Script"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by strikenowhere on 2007-10-10
Hello,
I am currently pulling my hair out in frustration trying to get this to work:

I have a script (LaunchVirtualBox) that dynamically creates a tap/bridge interface for using VirtualBox to host a Guest Win2K operating system on my headless 6.06 server:

#!/bin/bash

/usr/local/bin/VMTapBridgeUp
/usr/bin/VBoxManage startvm Win2KADBackup -type vrdp on


 The first line of my script calls another script (VMTapBridgeUp) which does the following:

#!/bin/bash

echo "creating tap0"
sudo /usr/sbin/tunctl -t tap0 -u mars
echo "bringing up tap0"
sudo /sbin/ifconfig -v tap0 0.0.0.0 promisc up
echo "creating br0"
sudo /usr/sbin/brctl addbr br0
echo "adding eth1 to br0"
sudo /usr/sbin/brctl addif br0 eth1
echo "adding tap0 to br0"
sudo /usr/sbin/brctl addif br0 tap0
echo "bringing up br0"
sudo /sbin/ifconfig br0 up
echo "assigning 10.4.1.10 to br0"
sudo /sbin/ifconfig br0 10.4.1.10 netmask 255.255.255.0 up

Now, when run manually from my /usr/local/bin directory as the non-root owner of the script, everything runs smoothly and the tap and bridge interfaces get setup correctly.  However, if I place a command inside crontab to run LaunchVirtualBox, when cron runs LaunchVirtualBox, which in turn runs VMTapBridgeUp, the network setup does not happen and seems to bail on this line:

sudo /sbin/ifconfig -v tap0 0.0.0.0 promisc up

It seems to me that there is some sort of permission problem occurring.  I had run into this problem originally and wound up doing a chmod u+s/chmod g+s on /sbin/ifconfig, so that whoever ran ifconfig would run it as if they had root permissions.

Basically what it boils down to is that I need to be able to run commands as root inside a script that gets placed into crontab as a non-root user.  I thought I had solved this by using the chmod trick, but I'm still stuck...any thoughts?

Thanks,
Greg

---

### Post by strikenowhere on 2007-10-10
Also, in case you are wondering why I am not using the TAPSetup and TAPTerminate parameters to launch my VMTapBridgeUp/VMTapBridgeDown scripts as VirtualBox would normally do, its because I was running into this same permission problem when VirtualBox was started and called VMTapBridgeUp.  It would complain that it was unable to bring up tap0 when "sudo /sbin/ifconfig -v tap0 0.0.0.0 promisc up" was called.

---

### Post by strikenowhere on 2007-10-10
Hah!  Seemed to have found the problem myself...it looks like sticking "sudo" into the VMTapBridgeUp is what is causing the problem...I removed it and now cron executes the scripts correctly.  My bet is that sudo was trying to ask the cronjob for the required password as it normally would, but since its a cronjob, there was no way to give it that data, so it bailed.

At least thats what I think the problem/solution is ... all I know now is that everything is running correctly :)

---


---
title: "completely freezed PC after few minutes of work.."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by howitz on 2008-03-31
My pc freezes completely after few minutes of work , when i worked in mozilla firefox the same thing happend , now happens with opera also , why when i use some of the programs my pc freezes ?

What's the cause , please help

---

### Post by Jim! on 2008-03-31
Is the computer only freezing when you run a web browser? Could you be a little more specific please? Care to name a few of the programs your using that cause your system to freeze?

Also, could you please tell us which OS your using?

---

### Post by Daveg4otu on 2008-03-31
Lot of possible causes - both software and hardware ...

Hardware - you need to check the PSU voltages(should be within +/- 5% of nominal.)and also System /CPU temps and - if you can - the GPU temps- check all fans are working and that Heatsinks etc are not clogged with dust.

Software - you'll need one of the experts as I've only just started with Ubuntu

---

### Post by howitz on 2008-03-31
Whole pc , notthing works except the hard reset button, i use 7.10 gutsy , the first time i only used mozilla firefox , i said oh well ok , i'll use opera , and now with opera freezes again , the last two times i was using , bittorrent , Totem Movie Player 2.20.0 , and pidgin.

---

### Post by howitz on 2008-03-31
> **Daveg4otu said:**
> Lot of possible causes - both software and hardware ...

Hardware - you need to check the PSU voltages(should be within +/- 5% of nominal.)and also System /CPU temps and - if you can - the GPU temps- check all fans are working and that Heatsinks etc are clogged with dust.

Software - you'll need one of the experts as I've only just started with Ubuntu

I am a hardware assembler i work with hardware and software 10 years , trust me it's not the hardware nor the bios settings.

---

### Post by Daveg4otu on 2008-03-31
**trust me it's not the hardware**

If I had a £ or $ for every time I've heard that(over the past 20 years).... Lockups with only the reset working are typical of  overworked/underpowered  or failing Graphics Cards.

---

### Post by Jim! on 2008-03-31
OK, Well It seems that quite a few people have had simialar problems in the past and quite often the cause has been related to a program that is connected to the internet. In this case 4/5 programs you mentioned are related to the internet so lets start there.

A quick search of the forum found quite a few simialar cases to yours and a lot of the people seemed to think it was related to firefox. Completely uninstall firefox and then reinstall it/restart the computer and see how everything runs. 

Here is a thread simialar to yours:[http://ubuntuforums.org/showthread.php?t=706304](http://ubuntuforums.org/showthread.php?t=706304)

You might also find this link helpful: (was posted in linked thread above)[http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_kernel](http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_kernel)

Hope something here helps...

---

### Post by howitz on 2008-03-31
Ok Jim i'll try that see how it works , thanks for the help.

---

### Post by howitz on 2008-03-31
Seems like it's not the mozilla , i guess it's the kernel , but what can i update on it , i have the latest or i am wrong ?
I end up helpless , dunno what's the problem except the kernel :( 

anybody to help

uname -r
2.6.22-14-generic

---

### Post by Jim! on 2008-03-31
Ah-Hah! I think the problem may have been a 'bug' in an update: [https://bugs.launchpad.net/ubuntu/+bug/175331](https://bugs.launchpad.net/ubuntu/+bug/175331)

The solution for now is to downgrade, to do so type in the terminal: sudo apt-get install linux-ubuntu-modules-2.6.22-14-generic=2.6.22-14.37

Try it and tell us how it works.

---

### Post by howitz on 2008-03-31
Hey Jim i tried that , and look at this ..

zdravko@zdravko-desktop:~$ sudo apt-get install linux-ubuntu-modules-2.6.22-14-generic=2.6.22-14.37
[sudo] password for zdravko:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-ubuntu-modules-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


:/ thanks for helping me , any solution for this ?

EDIT: i followed the link and tried this..

Linux zdravko-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
zdravko@zdravko-desktop:~$ lsb release -a
bash: lsb: command not found
zdravko@zdravko-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

---

### Post by mivo on 2008-03-31
I had one instance where my system would freeze after a few minutes, even after reboots. The fix was to turn off Compiz Fusion and then re-enable it. Yes, it was this simple, and I have no idea what had caused it since CF worked just fine before. This may not be the cause of your trouble, but it's so easy to do, it may be worth a try. :)

---

### Post by dstew on 2008-03-31
You can try to see what happened to your system by looking at the system log file. If your system locks, reboot and do```
more /var/log/syslog.0
```Look toward the end of the file and see if you were getting any error messages from a process before it locks.

Also, are you sure the whole computer locks? When it seems to be frozen, try ctrl-alt-F1 and see if you get a command line. If you do, it is likely that only the xserver is freezing, but the underyling system is OK.

---

### Post by howitz on 2008-03-31
I have installed the linux-image server kernel , and now i am on generic , and seems like the bug [https://bugs.launchpad.net/ubuntu/+bug/175331](https://bugs.launchpad.net/ubuntu/+bug/175331) is fixed , i am gonna test it and see how it works.

EDIT: Notthing :((( freezes completely again , notthing works , nor mouse , nor keyboard. dead. ???

---

### Post by howitz on 2008-03-31
this is what syslog.0 is telling

> 
Mar 31 16:43:00 zdravko-desktop kernel: [   62.434819] eth0: no IPv6 routers present
Mar 31 16:43:05 zdravko-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 31 16:43:06 zdravko-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 


I think it's a known bug or i need something to install ! this is driving me NUTS , all day i can't do my job :S

---

### Post by dstew on 2008-03-31
Looks like a Network Manager problem. In [This Document]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") there is a section on how to disable it. Also, you can try a different network managing program like [Wicd]("http://wicd.sourceforge.net/").

---

### Post by howitz on 2008-03-31
I've read everything and can't find how to disable this thing , :/ i am still trying i'll post my results

---

### Post by dstew on 2008-03-31
Here are the instructions taken from the [Network Manager document]("https://help.ubuntu.com/community/WifiDocs/NetworkManager").

First, stop network manager:```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```Then, create two files using a text-editor like gedit with only the word **exit** in them. These files will prevent network manager from starting again. The file names and the paths where they go are:```
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
```

---

### Post by howitz on 2008-03-31
Thanks dstew for your time!!

I removed Network Manager and installed Wicd, works like charm for now , i'll keep updated this thread , thanks for your time and for your help!! :)

---

### Post by howitz on 2008-04-01
Ok, here i am again , i started the pc this morning and boom , freezed again :((

this time it gives..

> Apr  1 10:43:49 zdravko-desktop kernel: [  142.804084] NET: Registered protocol family 10
Apr  1 10:43:49 zdravko-desktop kernel: [  142.804204] lo: Disabled Privacy Extensions
Apr  1 10:43:51 zdravko-desktop avahi-daemon[5207]: Registering new address record for fe80::21a:92ff:fe5a:351d on eth0.*.
Apr  1 10:44:00 zdravko-desktop kernel: [  153.460977] eth0: no IPv6 routers present
Apr  1 10:46:47 zdravko-desktop syslogd 1.4.1#21ubuntu3: restart.

Dunno what's the problem, i can't find a solution to this problem , i installed new network manager and notthing. If i don't find what's the problem i am finished , i will format the ubuntu partition together with him, i can't work this way :(

If anybody knows how i can fix it , please reply.

---

### Post by howitz on 2008-04-01
C'mon guys , somebody must know , or have a clue about this issue ?! :confused::(

---

### Post by dstew on 2008-04-01
Now I'm pretty much guessing, but there is a history of problems with IPv6. Usually, these problems only interfere with network traffic, but don't cause freezes. Anyway, you could try to disable the IPv6 protocols in the avahi-daemon. See if there is a /etc/avahi/avahi-daemon.conf file, and look if there is a setting like **use-ipv6="yes"**. If there is not a setting ("yes" is the default, so there might not be), just add **use-ipv6="no"** and see if that changes anything. Also, look at the syslog.0 file after each freeze, and see if it is always the same. If not, it might be a hardware problem.

Does the system freeze if you boot in recovery mode, and leave it for a while? Since that mode doesn't use the xserver, if you don't get a freeze in recovery mode the problem might be with your graphics software or hardware.

---

### Post by howitz on 2008-04-01
Thanks , dstew , i opened the file and the settings was "no" by default , ok , i reinstall the xserver , and all i got is kinit , and cannot show desktop , ok with that , i sorted that thing somehow ,

now i got this .... the system doesnt boot to login screen but in terminal ctrl+alt+f1 by default and ctrl+alt+f7 doesnt react (kinit: cannot show ...) , i need to type , sudo gdm so it can show the desktop ... 

is there way directly to go into login , cuz i need to login in terminal and again in graphic mode, btw when i login everythings works fine for now.

---

### Post by dstew on 2008-04-01
> i reinstall the xserverDid you *reconfigure* the xserver, or re-install it from a debian package?> the system doesnt boot to login screen but in terminalDoes it do this when you choose the regular boot item from the grub menu?

---

### Post by howitz on 2008-04-01
Yes i reconfigure it step by step.
Yep i choose regular boot and he does the same , i need to enter my user name and pass , and then i type sudo gdm , and after that displays the login screen and GUI.
Kinit says some thing that he cannot start it i can't remember what , and some error but i cannot copy it , i'll try to re-type it later.

---

### Post by dstew on 2008-04-01
Without really understanding the problem (probably something is wrong with the initialization scripts) you can get gdm to start by adding the line```
gdm &
```to the file /etc/rc.local. That will run the gdm startup script as if it were any other program you wanted to run at boot time. Put the **gdm &** line above the **exit 0** line. But, that is not really understanding the problem, just a workaround. If it works, it is harmless, I think. See [this thread]("http://www.techsupportforum.com/alternative-computing/linux-support/157435-ubuntu-gdm-does-not-start-boot.html").

---

### Post by howitz on 2008-04-01
> **dstew said:**
> Without really understanding the problem (probably something is wrong with the initialization scripts) you can get gdm to start by adding the line```
gdm &
```to the file /etc/rc.local. That will run the gdm startup script as if it were any other program you wanted to run at boot time. Put the **gdm &** line above the **exit 0** line. But, that is not really understanding the problem, just a workaround. If it works, it is harmless, I think. See [this thread]("http://www.techsupportforum.com/alternative-computing/linux-support/157435-ubuntu-gdm-does-not-start-boot.html").


Thanks Dstew! That worked now it's loading completely! thanks again! :)

Btw as far as freezing goes , still freezes .... but i have installed new video card , and will see how it goes with the new on, i keep you updated, thanks again

live long and prosper!

---


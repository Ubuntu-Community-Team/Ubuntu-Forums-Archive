---
title: "I can't share files with XP"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by siroche on 2008-03-17
OK, I think its time to install XP again - I give up after this last post. Please save me from MICROSOFT:confused:

Still cannot get a shared file between XP and ubunto.
I followed a HOWTO after trying all sorts of things on different threads and the closest I could get was I can see each machine from each other in PLACES>Network or Network Places frm XP and even get a prompt for a login from windows when mapping to the ubunto laptop (from XP \\simon-laptop\media\shared or \home\samba) but it comes up with (after a request to login) "the folder you entered does not appear to be valid. Please choose another"
When trying from the laptop (ubun) when following instructions from another thread only error I got
mount: can't find //simon-laptop/home/samba in /etc/fstab or /etc/mtab
simon@simon-laptop:~$ sudo mount -l

Here is the contents of FSTAB
simon@simon-laptop:~$ sudo mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
simon@simon-laptop:~$ sudo gedit /etc/fstab

after this I give up and Bill wins !!!

---

### Post by DrScum on 2008-03-17
A philosophical remark at the beginning: 
I don't see Ubuntu or any other Linux OS as a substitute for any MS OS. To use Linux just is the next step some make it earlier than others. There are many reasons to make that step later than others, just don't feel left behind, your time will come!

In order to provide more specific help, I would need to have more detailed information about your network architecture. For now I assume that you have a Win workgroup with an internet connection through a DSL router and want your Linux machine to be part of that by being hooked up to a switch using a Cat 5 cable.

Just to be clear: I am not one of the Linux guru's, I am not familiar with unix commands entered in terminal mode and by all means I don't understand completely the configuration of my Ubuntu systems. I switched about a year ago from WinXP and all my Ubuntu machines (one desktop and 2 Laptops) just work for me.

When you had your linux machine available in the Win network, and vice versa, I think you were there. When you are prompted for a user/password from the linux side just login as root and it'll work. Don't try another user. I think in order to have that working you would have to configure a Samba client. In order to have the Windows side available from the Linux client, the user logged on on the linux machine also has to exist on the windows side and the folders you want to have access to need to be marked "shared" on the windows side (see below).

Here are the steps I did when I included a Linux machine into a Microsoft driven Workgroup. 

Windows side:
DSL router configured as DHCP server any other (DHCP server works as well)
Folders to be shared with network clients need to be marked as shared (right click folder in file manager, select properties, navigate to the "shared" pane and select "share this folder on the network". The user logged on to the Linux machine should also exist as user on the Windows machine.

Linux side: settings for wired connection Interface eth0: Automatic configuration (DHCP)
To acces the network settings choose System>administration>network 
there you should see a wired connection with  a check mark in the checkbox. Highlight it and choose "Automatic configuration" in the Configuration line. Everything else should be grayed out.

With this configuration I was successful in sharing files between Windows and Linux systems. Just one more hint. It may take a while and maybe one or two reboots on the Windows side to make the linux system available in the network.

---

### Post by Faud on 2008-03-17
Don't know if you've read this page yet or not
[https://help.ubuntu.com/7.10/internet/C/networking-shares.html](https://help.ubuntu.com/7.10/internet/C/networking-shares.html)
Ive used the info on it to set up between Ubuntu and XP several times w/o any problems.
Good luck

---


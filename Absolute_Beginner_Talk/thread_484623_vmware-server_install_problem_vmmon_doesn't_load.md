---
title: "vmware-server install problem vmmon doesn't load"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by PCFascist on 2007-06-26
I followed the directions here:
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)


terminal output from install (apt-get):
```

Preconfiguring packages ...

Selecting previously deselected package netkit-inetd.

(Reading database ... 80793 files and directories currently installed.)

Unpacking netkit-inetd (from .../netkit-inetd_0.10-10.3ubuntu4_i386.deb) ...

Selecting previously deselected package vmware-server-kernel-modules-2.6.20-16.

Unpacking vmware-server-kernel-modules-2.6.20-16 (from .../vmware-server-kernel-modules-2.6.20-16_2.6.20.5-16.28_i386.deb) ...

Selecting previously deselected package vmware-server-kernel-modules.

Unpacking vmware-server-kernel-modules (from .../vmware-server-kernel-modules_2.6.20.16.28.1_i386.deb) ...

Selecting previously deselected package libssl0.9.7.

Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7k-3_i386.deb) ...

Selecting previously deselected package vmware-server.

Unpacking vmware-server (from .../vmware-server_1.0.3-1_i386.deb) ...

Setting up netkit-inetd (0.10-10.3ubuntu4) ...

 * Starting internet superserver...                                      [ OK ] 

Setting up vmware-server-kernel-modules-2.6.20-16 (2.6.20.5-16.28) ...

Setting up vmware-server-kernel-modules (2.6.20.16.28.1) ...

Setting up libssl0.9.7 (0.9.7k-3) ...

Setting up vmware-server (1.0.3-1) ...

Making sure services for VMware Server are stopped.

Stopping VMware services:

   Virtual machine monitor                                             done

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)

[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 

[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.17.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.17.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 

[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 

[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.123.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.123.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Generating SSL Server Certificate

Starting VMware services:

   Virtual machine monitor                                            failed

   Virtual ethernet                                                   failed

Module vmnet is not loaded.  Please verify that it is loaded before

running this script.

```

I can't start the service:
```
pcfascist@vmserver-cog:/etc/init.d$ sudo ./vmware-server start

Starting VMware services:

   Virtual machine monitor                                            failed

   Virtual ethernet                                                   failed

Module vmnet is not loaded.  Please verify that it is loaded before

running this script.
```

I tried to modprobe vmmon and it gives me:
```
FATAL: Module vmmon not found.

```

I found this:
[http://ubuntuforums.org/showpost.php?p=2893075&postcount=1048](http://ubuntuforums.org/showpost.php?p=2893075&postcount=1048)
and get this:
```
pcfascist@vmserver-cog:~/vmware-any-any-update109$ sudo ./runme.pl

Password:

Updating /usr/bin/vmware-config.pl ... corrupted

The file /usr/lib/vmware-server/modules/source/vmmon.tar that this script was 

about to install already exists. Overwrite? [yes] y

The file /usr/lib/vmware-server/modules/source/vmnet.tar that this script was 

about to install already exists. Overwrite? [yes] yes

Updating /usr/bin/vmware ... No patch needed/available

Updating /usr/bin/vmnet-bridge ... No patch needed/available

Updating /usr/lib/vmware-server/bin/vmware-vmx ... No patch needed/available

Updating /usr/lib/vmware-server/bin-debug/vmware-vmx ... No patch needed/available

VMware modules in "/usr/lib/vmware-server/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 

for your running kernel by invoking the following command: 

"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 

you now? [yes] yes

sh: /usr/bin/vmware-config.pl: not found


```




What can I try next?

Cheers,
Jesse JAmes

---

### Post by RAH66 on 2007-06-26
What are you trying to run in VMware?

I use VirtualBox to run XP  on my Ubuntu 7.04 Box... It wirks great :D

I followd these instructions 

[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)

---

### Post by lahook on 2007-06-26
I followed the directions here " [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto) " and it worked great. I think I messed up on one step though, because I have to start the server using "gksudo vmware".

---

### Post by PCFascist on 2007-06-26
> **RAH66 said:**
> What are you trying to run in VMware?

I use VirtualBox to run XP  on my Ubuntu 7.04 Box... It wirks great :D

I followd these instructions 

[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)


Thanks for the idea but I'd have to pay for that because I use it for work... as far as I understand VMserver is a free program.

---

### Post by PCFascist on 2007-06-26
> **lahook said:**
> I followed the directions here " [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto) " and it worked great. I think I messed up on one step though, because I have to start the server using "gksudo vmware".

I did try that way before I tried the apt-get method, I seem to have even less luck with installing stuff from the tar files.

Thanks for the suggestion though!

---

### Post by PCFascist on 2007-06-27
> **PCFascist said:**
> I did try that way before I tried the apt-get method, I seem to have even less luck with installing stuff from the tar files.

Thanks for the suggestion though!


Turns out installing from tar worked just fine this time around.... I did happen to install 1.0.2 however... but whatever, working for now.

---

### Post by stainblack on 2007-06-29
Hi,
try this:

user@cpu01:~$ uname -r
2.6.20-**16**-generic

I got the same trouble, but looking at /lib/modules/, I found that vmware modules are for kernel 2.6.20-16.
I installed ubuntu 7.04 with kernel 2.6.20-15-generic, but after a dist-upgrade It upgraded to 2.6.20-16-generic.
Grub menu's shows all kernel version and I didn't selected the 2.6.20-16-generic one but the oldest -15- one.
Rebooting the system with the -16-, vmware works greatly.

user@cpu01:~$ sudo /etc/init.d/vmware-server status
Bridged networking on /dev/vmnet0 is running
Host-only networking on /dev/vmnet1 is running
Host-only networking on /dev/vmnet8 is running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded

Do not try to copy *.ko from -16- to -15- or symlinking them, it doesn't work! --> "Invalid module format"

I hope it's helpful.

stainblack

---

### Post by Cygnus on 2007-07-06
I had the exact same problem with vmware-player. I thought perhaps the previous post would solve it as I had updated but not restarted with the new kernel, but that did not help either I get the same messages.

Installing manually however worked fine.

---

### Post by anewguy on 2007-07-06
> **lahook said:**
> I followed the directions here " [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto) " and it worked great. I think I messed up on one step though, because I have to start the server using "gksudo vmware".


;)I seem to remember that when you have that problem (it probably starts otherwise and gives permission errors, hence running it in root), the main way to fix this is to be sure there is a group named "disk" and that your userid is added to that group. You can do all of this via "System/Administration/Users and Groups".  I forget where I saw that - may have been another post here, may have been in the user guide.  I do know it helped me so I no longer needed to run as the super user or root.

---

### Post by servo153 on 2007-07-06
Heads up folks, I spent the last day beating my face against getting vmware server to work with the latest stable kernel, 2.6.21.5.  It just would not work.  I rebooted with the ubuntu installed 2.6.20-16-generic and vmware worked just fine.  I used the any any110 patch and it still would not work until the latest kernel.  I guess we have to wait for a newer version of vmware to come out.

---


---
title: "Some programs don't run while docked"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by glickmiller on 2007-05-14
I have recently switched to Ubuntu from Windows.  My IBM T43 runs great with Feisty except for one small issue:  When I dock my laptop some programs won't run.  For example, when I click on OpenOffice Writer, I see the splash screen and then it goes away and nothing happens.  When I am undocked, Writer will open with no problems.  I have installed the drivers for the ATI Radeon Mobility 300

Any ideas?  

-cgm

*First time poster; long time listener*

---

### Post by hartz on 2007-05-18
I have a gut-feeling this has got to do with disks and/or partitioning.  To help you to troubleshoot this I will need a few bits of information.

Could you please run these commands in a terminal window, and post their output here.

While un-docked:

```
mount
sudo fdisk -l
```

Then dock the laptop, and run those commands again, and show the output.  I want to look for differences in the output.

In addition, can you please run these commands while docked:
```
tail -30 /var/log/messages
tail -30 /var/log/system
dmesg | tail -30
```

And then finally, to see what the openoffice.org applications do when you start them, run this in the terminal:

```
oowriter
```

Besides showing a "spash-screen", it will produce some output in the terminal - please copy-n-paste that into this forum as well.

Last question:  You suggested that openoffice is not the only things that doesn't work when docked - can you maybe give a few more examples of apps that are not affected and ones that are affected, sometimes it helps to know to discover a pattern.

---

### Post by glickmiller on 2007-05-21
Here is the undocked output:
```
:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cglickmiller@aptica04u:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

Here is the docked output:
```
:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cglickmiller@aptica04u:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

Here are the additional commands while docked:
```
cglickmiller@aptica04u:~$ tail -30 /var/log/messages
May 21 08:59:54 aptica04u kernel: [   32.600000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May 21 08:59:54 aptica04u kernel: [   32.600000] apm: overridden by ACPI.
May 21 08:59:54 aptica04u kernel: [   32.756000] Non-volatile memory driver v1.2
May 21 08:59:54 aptica04u kernel: [   32.824000] input: /usr/sbin/thinkpad-keys as /class/input/input7
May 21 08:59:54 aptica04u kernel: [   32.996000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
May 21 08:59:54 aptica04u kernel: [   33.092000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
May 21 08:59:54 aptica04u kernel: [   33.092000] NFSD: starting 90-second grace period
May 21 08:59:58 aptica04u kernel: [   36.260000] Bluetooth: Core ver 2.11
May 21 08:59:58 aptica04u kernel: [   36.260000] NET: Registered protocol family 31
May 21 08:59:58 aptica04u kernel: [   36.260000] Bluetooth: HCI device and connection manager initialized
May 21 08:59:58 aptica04u kernel: [   36.260000] Bluetooth: HCI socket layer initialized
May 21 08:59:58 aptica04u kernel: [   36.300000] Bluetooth: L2CAP ver 2.8
May 21 08:59:58 aptica04u kernel: [   36.300000] Bluetooth: L2CAP socket layer initialized
May 21 08:59:58 aptica04u kernel: [   36.440000] Bluetooth: RFCOMM socket layer initialized
May 21 08:59:58 aptica04u kernel: [   36.440000] Bluetooth: RFCOMM TTY layer initialized
May 21 08:59:58 aptica04u kernel: [   36.440000] Bluetooth: RFCOMM ver 1.8
May 21 08:59:59 aptica04u kernel: [   37.540000] bridge-eth0: already up
May 21 09:01:28 aptica04u gconfd (cglickmiller-5434): starting (version 2.18.0.1), pid 5434 user 'cglickmiller'
May 21 09:01:28 aptica04u gconfd (cglickmiller-5434): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 21 09:01:28 aptica04u gconfd (cglickmiller-5434): Resolved address "xml:readwrite:/home/cglickmiller/.gconf" to a writable configuration source at position 1
May 21 09:01:28 aptica04u gconfd (cglickmiller-5434): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 21 09:01:28 aptica04u gconfd (cglickmiller-5434): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 21 09:01:28 aptica04u gconfd (cglickmiller-5434): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 21 09:01:38 aptica04u gconfd (cglickmiller-5434): Resolved address "xml:readwrite:/home/cglickmiller/.gconf" to a writable configuration source at position 0
May 21 09:01:41 aptica04u dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May 21 09:01:41 aptica04u bonobo-activation-server (cglickmiller-5485): Passing command-line arguments in .server files is deprecated: "/usr/bin/tomboy --panel-applet"
May 21 09:01:52 aptica04u kernel: [  151.008000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May 21 09:01:58 aptica04u dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
May 21 09:01:58 aptica04u dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
May 21 09:01:58 aptica04u dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
cglickmiller@aptica04u:~$ tail -30 /var/log/system
tail: cannot open `/var/log/system' for reading: No such file or directory
cglickmiller@aptica04u:~$ dmesg | tail -30
[   37.540000] /dev/vmnet: open called by PID 5251 (vmnet-bridge)
[   37.540000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   37.540000] /dev/vmnet: port on hub 0 successfully opened
[   37.540000] bridge-eth0: enabling the bridge
[   37.540000] bridge-eth0: up
[   37.540000] bridge-eth0: already up
[   37.540000] bridge-eth0: attached
[   37.604000] /dev/vmnet: open called by PID 5265 (vmnet-natd)
[   37.604000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   37.604000] /dev/vmnet: port on hub 8 successfully opened
[   42.116000] /dev/vmnet: open called by PID 5353 (vmware-vmx)
[   42.116000] /dev/vmnet: port on hub 8 successfully opened
[   42.268000] /dev/vmmon[5363]: host clock rate change request 0 -> 19
[   42.268000] /dev/vmmon[5363]: host clock rate change request 19 -> 83
[   47.560000] /dev/vmnet: open called by PID 5364 (vmnet-netifup)
[   47.560000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   47.560000] /dev/vmnet: port on hub 1 successfully opened
[   47.568000] /dev/vmnet: open called by PID 5369 (vmnet-netifup)
[   47.568000] /dev/vmnet: port on hub 8 successfully opened
[   47.764000] /dev/vmnet: open called by PID 5386 (vmnet-dhcpd)
[   47.768000] /dev/vmnet: port on hub 8 successfully opened
[   47.884000] /dev/vmnet: open called by PID 5387 (vmnet-dhcpd)
[   47.884000] /dev/vmnet: port on hub 1 successfully opened
[   57.712000] vmnet1: no IPv6 routers present
[   58.264000] vmnet8: no IPv6 routers present
[   63.928000] /dev/vmnet: open called by PID 5363 (vmware-vmx)
[   63.928000] /dev/vmnet: port on hub 8 successfully opened
[  151.008000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  151.080000] ieee80211_crypt: registered algorithm 'WEP'
[  167.584000] eth1: no IPv6 routers present

```

Here is the output when I run Writer from the terminal:
```
cglickmiller@aptica04u:~$ oowriter

** (process:6070): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

I did do a little bit of research on this error, but did not find anything helpful.  Other programs that do not run while docked are Keepass, ```
cglickmiller@aptica04u:~$ keepass
Floating point exception (core dumped)

```
I thought there were others, but I can't find them right now.  It may well be that the other OpenOffice programs are sticking in my head as other programs.  They all give the same "unkown error," by the way.

Thanks for your help!

---

### Post by hartz on 2007-05-21
No help there... I want a trace of the execution - Please run this command:

strace -vx -o /tmp/oowriter.out oowriter

This will create a text file called /tmp/oowriter.out - you can attached the file to your post in the forum, or if it is not too long, copy-and-paste it into the forum.

---

### Post by glickmiller on 2007-05-21
execve("/usr/bin/oowriter", ["oowriter"], ["SSH_AGENT_PID=5428", "SHELL=/bin/bash", "TERM=xterm", "GTK_RC_FILES=/etc/gtk/gtkrc:/hom"..., "WINDOWID=62914720", "USER=cglickmiller", "SSH_AUTH_SOCK=/tmp/ssh-QtfayJ539"..., "GNOME_KEYRING_SOCKET=/tmp/keyrin"..., "SESSION_MANAGER=local/aptica04u:"..., "USERNAME=cglickmiller", "PATH=/usr/local/sbin:/usr/local/"..., "DESKTOP_SESSION=default", "GDM_XSERVER_LOCATION=local", "PWD=/home/cglickmiller", "LANG=en_US.UTF-8", "GDMSESSION=default", "SHLVL=1", "HOME=/home/cglickmiller", "GNOME_DESKTOP_SESSION_ID=Default"..., "LOGNAME=cglickmiller", "DBUS_SESSION_BUS_ADDRESS=unix:ab"..., "DISPLAY=:0.0", "COLORTERM=gnome-terminal", "XAUTHORITY=/home/cglickmiller/.X"..., "_=/usr/bin/strace"]) = 0
brk(0)                                  = 0x805f000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fb0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_dev=makedev(8, 1), st_ino=5737499, st_mode=S_IFREG|0644, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=88, st_size=42365, st_atime=2007/05/21-13:38:31, st_mtime=2007/05/21-09:22:00, st_ctime=2007/05/21-09:22:00}) = 0
mmap2(NULL, 42365, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7fa5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\x7f\x45\x4c\x46\x01\x01\x01\x00\x00\x00\x00\x00\x00\x00"..., 512) = 512
fstat64(3, {st_dev=makedev(8, 1), st_ino=3296484, st_mode=S_IFREG|0644, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=2568, st_size=1307104, st_atime=2007/05/21-13:38:31, st_mtime=2007/04/04-06:48:47, st_ctime=2007/04/25-09:18:06}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e64000
mmap2(0xb7f9f000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7f9f000
mmap2(0xb7fa2000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fa2000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e63000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7e636c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f9f000, 4096, PROT_READ)   = 0
munmap(0xb7fa5000, 42365)               = 0
getpid()                                = 18161
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x805f000
brk(0x8080000)                          = 0x8080000
getppid()                               = 18160
stat64("/home/cglickmiller", {st_dev=makedev(8, 1), st_ino=425986, st_mode=S_IFDIR|0755, st_nlink=45, st_uid=1000, st_gid=1000, st_blksize=4096, st_blocks=8, st_size=4096, st_atime=2007/05/21-09:14:24, st_mtime=2007/05/21-09:06:53, st_ctime=2007/05/21-09:06:53}) = 0
stat64(".", {st_dev=makedev(8, 1), st_ino=425986, st_mode=S_IFDIR|0755, st_nlink=45, st_uid=1000, st_gid=1000, st_blksize=4096, st_blocks=8, st_size=4096, st_atime=2007/05/21-09:14:24, st_mtime=2007/05/21-09:06:53, st_ctime=2007/05/21-09:06:53}) = 0
open("/usr/bin/oowriter", O_RDONLY)     = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x8055270, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\nexport OOO_EXTRA_ARG=\'"..., 8192) = 84
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e63708) = 18162
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 18162
--- SIGCHLD (Child exited) @ 0 (0) ---
read(10, "", 8192)                      = 0
exit_group(0)                           = ?

---

### Post by hartz on 2007-05-21
Nothing out of the ordinary.  Notably the initial program is NOT the one producing the error you see.  We need to trace forked processes (follow child processes)

Please rerun it with an extra switch, like this:

```
strace -fvx -o /tmp/trace.out oowriter
```

The above should result in a rather .... larger trace file.

---

### Post by hartz on 2007-05-21
And had I checked I would have noticed that /usr/bin/oowriter is a 3-line bash script.

So please re-run with the -f switch extra :-(

---

### Post by TekNullOG on 2007-05-21
i had a similar problem. It would do that when i removed my T43 from my docking station. It turns out software was trying to open in my second screen that is usually configured when the computer is docked. Turns out, I have to switch my screen resolution back to native when i undock 

(System > Preferences > Screen Resolution )

It boggled me for the longest time and it turned out to be something this simple.

Good luck

---

### Post by glickmiller on 2007-05-22
I ran "strace -vxf -o /tmp/oowriter.out oowriter"  It is a *much* larger file so I attached it.  

I also verified that I am using the exact same resolution docked and undocked.  You got my hopes up, eightinches! :D

---

### Post by hartz on 2007-05-23
Right now the only odity that I can see is that there is a SIGFPE in proc 6125

```
6125  --- SIGFPE (Floating point exception) @ 0 (0) ---
```


This is the following process:
execve("/usr/lib/openoffice/program/soffice.bin", ["/usr/lib/openoffice/program/soff"..., "-writer", "-splash-pipe=5"],

Somehow I have a feeling the splash screen is responsible... but I have not yet checked properly....

Shortly after this, proc 6111 (The same binary) notes a coredump:
6110  <... wait4 resumed> [{WIFSIGNALED(s) && WTERMSIG(s) == SIGFPE && WCOREDUMP(s)}], 0, NULL) = 6125
6110  --- SIGCHLD (Child exited) @ 0 (0) ---
6110  exit_group(0)                     = ?

You will be able to get a back-trace from the dump (look for a file named "core" in the directory where you run the program from).  This file may be useful to a developer if you log a bug against OpenOffice, which is what I am thinking this might be.

I will investigate some more later when I get more time.

---


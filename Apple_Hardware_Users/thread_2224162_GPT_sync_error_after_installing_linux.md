---
title: "GPT sync error after installing linux"
date: 2014-05-14
forum: Apple Hardware Users
---

### Post by fabianmkteo on 2014-05-14
WOT below
Hi everyone, I am a complete newbie in linux and I am trying to install linux on a mac aluminium (late 2007). 
I encountered the ' gptsync: GPT partition of type 'Unknown' found, will not touch this disk.' and followed #6 of this thread
[http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229)

I am fine until I reach step 7 when sudo does not work anymore and throws up an error
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo: unable to resolve host ubuntu[/TD]
[/TR]
[/TABLE]

when I tried the command [COLOR=#ff0000]hostname [/COLOR]I get
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]ubuntu[/TD]
[/TR]
[/TABLE]

so I looked at the hosts by using [COLOR=#ff0000]cat /etc/hosts[/COLOR]
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]127.0.0.1         localhost

127.0.1.1         fabian-MacBook

 
 
# The following lines are desirable for IPv6 capable hosts

::1     ip6-localhost ip6-loopback

fe00::0 ip6-localnet

ff00::0 ip6-mcastprefix

ff02::1 ip6-allnodes

ff02::2 ip6-allrouters[/TD]
[/TR]
[/TABLE]

after searching for awhile I tried [COLOR=#ff0000][FONT=Ubuntu Mono]sudo gedit /etc/hosts[/FONT][/COLOR][FONT=Ubuntu Mono] to edit the host name but got another error[/FONT]
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo: unable to resolve host ubuntu

No protocol specified

 
** (gedit:3969): WARNING **: Could not open X display

process 3969: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/etc/machine-id": No such file or directory

See the manual page for dbus-uuidgen to correct this issue.

No protocol specified

error: XDG_RUNTIME_DIR not set in the environment.

 
 
(gedit:3969): Gtk-WARNING **: cannot open display: :0 [/TD]
[/TR]
[/TABLE]

I went on ahead with the steps to try and identify more problems. I could unpack the gptsync in step 8 without problem except for the 'sudo:unable to resolve host' problem. 
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo: unable to resolve host ubuntu

(Reading database ... 163212 files and directories currently installed.)

Preparing to unpack gptsync_0.14-2_amd64.deb ...

Unpacking gptsync (0.14-2) over (0.14-2) ...

Setting up gptsync (0.14-2) ...

Processing triggers for man-db (2.6.7.1-1) ...[/TD]
[/TR]
[/TABLE]

I then ran [COLOR=#ff0000]sudo gptsync /dev/sda[/COLOR]  in step 9 and got
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo: unable to resolve host ubuntu

 
 
Current GPT partition table:

 #      Start LBA      End LBA  Type

 1             40       409639  EFI System (FAT)

 2         409640    117007159  Mac OS X HFS+

 3      117008384    309508095  Unknown

 4      310532096    312580095  Linux Swap

 5      309508096    310532095  BIOS Boot Partition

 
 
Current MBR partition table:

 # A    Start LBA      End LBA  Type

 1              1       409639  ee  EFI Protective

 2 *       409640    117007159  af  Mac OS X HFS+

 3      117008384    309508095  83  Linux

 4      310532096    312580095  82  Linux swap / Solaris

 
 
Status: GPT partition of type 'Unknown' found, will not touch this disk. [/TD]
[/TR]
[/TABLE]

while for the last step I ran [COLOR=#ff0000]sudo grub-install /dev/sda
[/COLOR][TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo: unable to resolve host ubuntu

Installing for i386-pc platform.

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

device node not found

Installation finished. No error reported. [/TD]
[/TR]
[/TABLE]

I tried to reboot but as expected, I cannot boot ubuntu up and the partition editor in rEfit still has the same error ptsync: GPT partition of type 'Unknown' found, will not touch this disk. I am at a lost on how to proceed and I appreciate any help I can get

---


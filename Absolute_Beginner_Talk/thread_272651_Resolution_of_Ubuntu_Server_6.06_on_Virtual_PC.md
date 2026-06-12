---
title: "Resolution of Ubuntu Server 6.06 on Virtual PC"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by dominicrodger on 2006-10-06
Hi,

I've installed Ubuntu server on a virtual PC (using Microsoft Virtual PC 2004) on windows XP. Install worked (after a while!) and on turning my virtual PC on, all works fine until:

isapnp: checksum for device 1 is not valid (0x89)

at which point the screen resolution becomes 640x200 and the bottom text flows off the screen (so I can't reach it). If I leave it long enough I can logon (though I can't see what I'm doing!) and get to a bash prompt. Is there any way to fix it from there?

Many thanks,

Dominic

---

### Post by az on 2006-10-06
Can you file a bug report with MS virtual PC?

Probably not....

---

### Post by dominicrodger on 2006-10-07
Not that I know of.

---

### Post by dominicrodger on 2006-10-08
Any ideas?

---

### Post by rbdsd on 2007-04-03
[FONT="Courier New"]
[SIZE="3"]

I actually got Ubuntu 6.06 LTS to install and run on
top of Microsoft Virtual PC 2004.  Here are the steps:

o Download the ubuntu-6.06.1-server-i386.iso file
o Create a New Virtual Machine as type Other
o Start the new virtual machine
o Click on CD in the virtual machine menu and select: Capture 
  ISO Image.  Choose the ubuntu-6.06.1-server.i386.iso file.
o Press Enter in the VM screen
o Use the up/down arrows to pick "Install to the hard disk" or
  "Install a LAMP server" BUT then press F6 for Other Options
o Add the following to the end of the Boot Options:
     BOOT_DEBUG=3
o Press Enter

The install will enter a busybox shell.  At the shell prompt, do
the following:
   cd /lib/debian-installer-startup.d
   rm S40framebuffer-module-linux-x86
   exit

You will get another BusyBox shell prompt.  Just type: exit

At this point you will actually be able to read the screen
and follow the installation normally.  However, beyond the
screen problems, there are network issues that have to be
addressed (at least in my experience).  So go through the
installation up to the point where it asks you for the system's
hostname.

Before you enter the new hostname, do the following:
o Type an ALT-F2 to switch VTs
o Press Enter to activate that console
o At the BusyBox shell prompt, type:
     ifconfig eth0 mtu 1480

o Type an ALT-F1 to switch back to the install VT
o Continue with the installation as normal.  This will take
  a while.


o When the installation is complete and there is a message
  that says that all that remains is to restart the system,
  type an ALT-F2 to switch back the the BusyBox shell VT
o At the BusyBox shell prompt, type
      chroot /target /bin/sh
	  cd /boot/grub
	  vi menu.lst   (or use whatever other editor)
	    Search for: splash BOOT_DEBUG=3
	    Remove both splash and BOOT_DEBUG=3 from defoptions and
	      from the Ubuntu kernel line
	  :wq (write the file and quit the editor for vi)
	  exit (exit from the chrooted shell)
	  Type an ALT-F1 to go back to the install screen
	  Type Enter to finish the installation

The VM should reboot and Ubuntu Server should come up with a
readable screen.  Log in and then:

sudo bash
cd /etc/network
vi interfaces  (or use whatever other editor)

After the line that defines iface eth0, add
<TAB>post-up ifconfig eth0 mtu 1480

:wq (write the file and quit the editor for vi)

cd /etc/init.d
sh networking restart

ifconfig eth0

The MTU should show 1480.

At this point, I reboot for good measure.


[/SIZE]
[/FONT]

---


---
title: "Some noob Q's: fonts, graphics, filesystem"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-07
[LIST=1]
[*]doesn't Verdana exist on Ubuntu...? websites are showing up in an ugly base font...
[*]I have an ATI Rage Pro 9800 graphics card. Upon installing Ubuntu, text and images don't look too sharp / colours not vibrant? How do I improve this...? There is no driver specifically for Ubuntu for this card, which is over 3 yrs old and discontinued on ATI's site...
[*]when I browse the filesystem, it seems cluttered with folders like bin, media, dev, boot etc.... if these are system folders why can't they be hidden away neatly like in WIndows? Is there an equivalent to Program Files?
[/LIST]

Thx!

---

### Post by Jagot on 2006-07-07
1) Enable the universe and multiverse repositories as described it:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, in Terminal:

```
sudo aptitude update && sudo aptitude install msttcorefonts
```

3ish) There are various locations that programs are installed, but the primary one is /usr/bin

---

### Post by Indras on 2006-07-07
> **BlackMambo said:**
> 
when I browse the filesystem, it seems cluttered with folders like bin, media, dev, boot etc.... if these are system folders why can't they be hidden away neatly like in WIndows? Is there an equivalent to Program Files?

Most of the filesystem clutter is a holdover from Unix days.  It is still kept for compatibility reasons.  Here's a basic run down of the purpose of each main folder.  (I'm borrowing this without permission from [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/))

> /sbin - This directory contains all the binaries that are essential to the
working of the system. These include system administration as well as
maintenance and hardware configuration programs. Find lilo, fdisk, init,
ifconfig etc here. These are the essential programs that are required by
all the users. Another directory that contains system binaries is /usr/sbin.
This directory contains other binaries of use to the system administrator.
This is where you will find the network daemons for your system along with
other binaries that only the system administrator has access to, but which are
not required for system maintenance, repair etc.

/bin - In contrast to /sbin, the bin directory contains several useful
commands that are used by both the system administrator as well as
non-privileged users. This directory usually contains the shells like
bash, csh etc. as well as much used commands like cp, mv, rm, cat, ls.
There also is /usr/bin, which contains other user binaries. These binaries
on the other hand are not essential for the user. The binaries in /bin
however, a user cannot do without.

/boot - This directory contains the system.map file as well as the Linux
kernel. Lilo places the boot sector backups in this directory.

/dev - This is a very interesting directory that highlights one important
characteristic of the Linux filesystem - everything is a file or a
directory. Look through this directory and you should see hda1, hda2 etc,
which represent the various partitions on the first master drive of the
system. /dev/cdrom and /dev/fd0 represent your CDROM drive and your floppy
drive. This may seem strange but it will make sense if you compare the
characteristics of files to that of your hardware. Both can be read from
and written to. Take /dev/dsp, for instance. This file represents your
speaker device. So any data written to this file will be re-directed to
your speaker. Try 'cat /etc/lilo.conf > /dev/dsp' and you should hear some
sound on the speaker. That's the sound of your lilo.conf file! Similarly,
sending data to and reading from /dev/ttyS0 ( COM 1 ) will allow you to
communicate with a device attached there - your modem.

/etc - This directory contains all the configuration files for your system.
Your lilo.conf file lies in this directory as does hosts, resolv.conf and
fstab. Under this directory will be X11 sub-directory which contains the
configuration files for X. More importantly, the /etc/rc.d directory
contains the system startup scripts. This is a good directory to backup
often. It will definitely save you a lot of re-configuration later if you
re-install or lose your current installation.

/home - Linux is a multi-user environment so each user is also assigned a
specific directory which is accessible only to them and the system
administrator. These are the user home directories, which can be found
under /home/username. This directory also contains the user specific
settings for programs like IRC, X etc.

/lib - This contains all the shared libraries that are required by system
programs. Windows equivalent to a shared library would be a DLL file.

/lost+found - Linux should always go through a proper shutdown. Sometimes
your system might crash or a power failure might take the machine down.
Either way, at the next boot, a lengthy filesystem check using fsck will
be done. Fsck will go through the system and try to recover any corrupt
files that it finds. The result of this recovery operation will be placed
in this directory. The files recovered are not likely to be complete or
make much sense but there always is a chance that something worthwhile is
recovered.

/mnt - This is a generic mount point under which you mount your filesystems
or devices. Mounting is the process by which you make a filesystem
available to the system. After mounting your files will be accessible
under the mount-point. This directory usually contains mount points or
sub-directories where you mount your floppy and your CD. You can also
create additional mount-points here if you want. There is no limitation to
creating a mount-point anywhere on your system but convention says that
you do not litter your file system with mount-points.

/opt - This directory contains all the software and add-on packages that
are not part of the default installation. Generally you will find KDE and
StarOffice here. Again, this directory is not used very often as it's
mostly a standard in Unix installations.

/proc - This is a special directory on your system. We have a more detailed
article on this one here.

/root - We talked about user home directories earlier and well this one is
the home directory of the user root. This is not to be confused with the
system root, which is directory at the highest level in the filesystem.

/tmp - This directory contains mostly files that are required temporarily.
Many programs use this to create lock files and for temporary storage of
data. On some systems, this directory is cleared out at boot or at
shutdown.

/usr - This is one of the most important directories in the system as it
contains all the user binaries. X and its supporting libraries can be
found here. User programs like telnet, ftp etc are also placed here.
/usr/doc contains useful system documentation. /usr/src/linux contains the
source code for the Linux kernel.

/var - This directory contains spooling data like mail and also the output
from the printer daemon. The system logs are also kept here in
/var/log/messages. You will also find the database for BIND in /var/named
and for NIS in /var/yp

As far as hiding them from the user, it seems like a neat idea, especially the /sbin and /boot folders, as only advanced users will want to change anything in them.  You'll have to wait for a Linux guru to come along with a solution.

Oh, and the equivalent of the "Program Files" directory is /usr/bin.  Although you could also argue that /bin and /etc directories contain this type of info as well, but that's just opinion.

---

### Post by BlackMambo on 2006-07-07
> **Jagot said:**
> 1) Enable the universe and multiverse repositories as described it:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, in Terminal:

```
sudo aptitude update && sudo aptitude install msttcorefonts
```

3ish) There are various locations that programs are installed, but the primary one is /usr/bin
thanks - I did as you say but no change (and I rebooted the system). My System/Admin/Software Properties didn't quite match the screenshot shown in  that link... nevertheless I checked all available boxes (bar those that were 'source') and ran the query in Terminal. It basically said at the end something to the effect that it hadn't found any msttcorefonts

Anything else I can try? There must be a basic reason why my brand new install of Ubuntu displays Courier on so many websites......

---


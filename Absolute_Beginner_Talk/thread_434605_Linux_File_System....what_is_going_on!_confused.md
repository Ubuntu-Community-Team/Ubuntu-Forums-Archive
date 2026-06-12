---
title: "Linux File System....what is going on! :confused:"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by blop on 2007-05-06
Hi all,

loving my ubuntu havent used XP for surfing since i installed it.... But im finding other bits a bit scary...

like the file system i mean it look so complex and scary....what are all those folders in / where does software go....its crazy.

One that i find bizarre is i have installed wine and its in my home folder but i cant see the wine dir directly there i have to type /.wine.

what is the . infront of wine do?

any help appreciated..

---

### Post by viciouslime on 2007-05-06
> **blop said:**
> Hi all,

loving my ubuntu havent used XP for surfing since i installed it.... But im finding other bits a bit scary...

like the file system i mean it look so complex and scary....what are all those folders in / where does software go....its crazy.

One that i find bizarre is i have installed wine and its in my home folder but i cant see the wine dir directly there i have to type /.wine.

what is the . infront of wine do?

any help appreciated..

The . makes it hidden. Press ctrl+h to see hidden folders :)

---

### Post by Zalbor on 2007-05-06
Or you can go to the file management preferences and choose to make all hidden directories visible. That's what I do.

---

### Post by OffHand on 2007-05-06
> The first thing that most new users shifting from Windows will find
confusing is navigating the Linux filesystem. The Linux filesystem
does things a lot more differently than the Windows filesystem.
This article explains the differences and takes you through the
layout of the Linux filesystem.

For starters, there is only a single hierarchal directory structure.
Everything starts from the root directory, represented by '/', and then
expands into sub-directories. Where DOS/Windows had various partitions and
then directories under those partitions, Linux places all the partitions
under the root directory by 'mounting' them under specific directories.
Closest to root under Windows would be c:.

Under Windows, the various partitions are detected at boot and assigned a
drive letter. Under Linux, unless you mount a partition or a device, the
system does not know of the existence of that partition or device. This
might not seem to be the easiest way to provide access to your partitions
or devices but it offers great flexibility.

This kind of layout, known as the unified filesystem, does offer several
advantages over the approach that Windows uses. Let's take the example of
the /usr directory. This directory off the root directory contains most of
the system executables. With the Linux filesystem, you can choose to mount
it off another partition or even off another machine over the network. The
underlying system will not know the difference because /usr appears to be
a local directory that is part of the local directory structure! How many
times have you wished to move around executables and data under Windows,
only to run into registry and system errors? Try moving c:windowssystem
to another partition or drive.

Another point likely to confuse newbies is the use of the frontslash '/'
instead of the backslash '' as in DOS/Windows. So c:windowssystem would
be /c/windows/system. Well, Linux is not going against convention here.
Unix has been around a lot longer than Windows and was the standard a lot
before Windows was. Rather, DOS took the different path, using '/' for
command-line options and '' as the directory separator.

To liven up matters even more, Linux also chooses to be case sensitive.
What this means that the case, whether in capitals or not, of the
characters becomes very important. So this is not the same as THIS or ThIs
for that matter. This one feature probably causes the most problems for
newbies.

We now move on to the layout or the directory structure of the Linux
filesystem. Given below is the result of a 'ls -p' in the root directory.

bin/ dev/ home/ lost+found/ proc/ sbin/ usr/
boot/ etc/ lib/ mnt/ root/ tmp/ var/

/sbin - This directory contains all the binaries that are essential to the
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
and for NIS in /var/yp.

This was a short and basic look at the Linux filesystem. You do need to
have at least this basic knowledge of the layout of the filesystem to
fully utilize its potential. One good place to read about the filesystem
is this detailed document at [www.pathname.com/fhs/1.2/fsstnd-toc.html](www.pathname.com/fhs/1.2/fsstnd-toc.html) that
specifies the standard structure of the Linux filesystem. 

Source: [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by blop on 2007-05-06
hi all,

can you tell me where that setting is? i have been hunting through Konquer and finding nothing...

---

### Post by Najand on 2007-05-06
Hmm... about the file system... Any of them are for some specified purposes... For example you'll find all of the most used commands in /bin. /etc is for system configuration. /home is your home and other users home. The /usr directory contains files and programs meant to be used by all of the users on the system. etc. Don't worry about it... Use [The Linux Documentation Project]("tldp.org/") To learn what is going on...
The dot(.) before file names in home directory of a user are configuration of packages just for that user. Well... they are hidden by default and can be seen by some commands like "ls -a" you can change directory (cd) to that directory and see what is in it using ls command again.

---

### Post by AAM on 2007-05-06
The file system is much less scary if you start from the point that you can see **/home/blop** and need rarely to look elsewhere until you are better at this Linux thing. The hidden files are hidden for a good reason - they related to stuff going on when you use a program that you can see other ways if you want but really don't need to see. You can think of this as the linux kernel letting you use a self-destructing copy of the program along with the configuration information from the dot file in your home directory (that's **/home/blop** not **/home**!).

Walk carefully to start with man! You can install most things with Synaptic Manager + (Automatix &/or EasyUnbuntu) which have easy to follow instructions. All these guides tell you exactly what to do.

I would suggest that you put off **wine** for a while until you have a better handle on what's happening. There isn't too much that you can't do with another linux/OS program which would usually be much easier to install than a Windows program under wine as part of your first excursion into linux.

What I'm saying is ... baby steps first, huge leaps later. Otherwise the frustration of your inability will be translated into a belief about the inability of Linux.

---

### Post by hyper_ch on 2007-05-06
In Konqueror:  click on "View" and then select "Show hidden files" :)

---

### Post by Jebster69 on 2007-05-07
Hi All ... I'm a complete newbie to this Linux / Xubuntu stuff and I'm not that keen when it comes to using Forums, so if I'm in the wrong place for this, then I appologize. But, I have a problem that I need help with. I'm using Xubuntu 7.04 and I managed to put some pics onto my desktop, but I want to use them in a webpage that I'm making. So, I opened the File Manager and opened the /var directory, then the /www directory and then, being an old windows user, I tried dragging the pic files into the www directory, but the pics just won't go into the directory, so I think I have a permissions problem. So how can I make the /var/www directory accessible to my pictures and my mousepad editor files? Any help would be appreciated!

---

### Post by Nythain on 2007-05-07
try adding your user to the group www-data... that might give you the permission you need without havening to change the ownership of /var/www... and if thats not the right group you can always right click on the folder in your filemanager, go to properties, or whatever its called in gnome and see what group its owned by... as for adding your user to a group in gnome, im at a loss, i use kde

---

### Post by Jebster69 on 2007-05-07
> **Nythain said:**
> try adding your user to the group www-data... that might give you the permission you need without havening to change the ownership of /var/www... and if thats not the right group you can always right click on the folder in your filemanager, go to properties, or whatever its called in gnome and see what group its owned by... as for adding your user to a group in gnome, im at a loss, i use kde

Thanks very much for the reply!

Jebster69

---


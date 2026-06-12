---
title: "That crazy directory tree!"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Maelgwyn on 2006-02-05
As you will have undoubtedly noticed, Linux stores it's system files in a totally different way to Windows. I'm going to try to explain a few of what those folders are, and what's kept in them.

< / >

This is the root (or base) directory. Everything starts here. Every file & directory in your system is under the root directory. This 'folder' normally only contains sub-directories, so it's not recommended to store single files directly under root.

Don't confuse root directory with 'root' user.

< /boot >

This one's kind of obvious. Linux keeps the information it needs when booting in here. As an example, your Linux kernel is kept here. If you **ls /boot**, you'll see a file called *vmlinux* - that's your kernel.

< /etc >

Your configuration files for your Linux system are kept here. Most of them are text files which you can edit. Here's some well-known config files:
    */etc/inittab*
    This is a text file that describes what processes are started at system bootup and during
    normal operation. For example, you can set the X Window System to start automatically and
    even configure what happens if a user presses **Ctrl-Alt-Del**

    */etc/fstab*
    This file contains descriptive information about the various file systems and their         mount points, like floppies, cdroms, and so on.

    */etc/passwd*
    This is where users are defined.

< /bin, /usr/bin >

A lot of binaries (hence the name) for system programs are kept here. The /bin directory contains the most important programs the system needs to operate (like shells, **ls**, **grep** etc. The /usr/bin contains applications for users. Just to be confusing though, in some cases, it doesn't really matter which folder you put a program in.

< /sbin, /usr/sbin >

Very similar to /bin & /usr/bin, but these ones are for system admin. In many cases you'll have to run these programs as 'root'.

< /usr >

This directory holds user applications and other things like source codes, pictures, docs. /usr is often the largest directory on a Linux system, so quite a few people like to have it on a separate partition. Some subdirectories:

    */usr/doc*
    Documentation for the user applications, in many file formats.

    */usr/share*
    Config files and graphics for many user applications.

    */usr/src*
    Source code files for the system's software, including the Linux kernel.

    */usr/include*
    Header files for the C compiler. The header files define structures and constants that         are needed for building most standard programs. A subdirectory under /usr/include         contains headers for the C++ compiler.

    */usr/X11R6*
    The X Window System and things for it. The subdirectories under /usr/X11R6 may contain         some X binaries themselves, as well as documentation, header files, config files, icons,         sounds, and other things related to the graphical programs.

< /usr/local >

This is where applications and other files for use on your local machine are installed. If you're part of a network, the /usr directory may be on another machine and shared by may workstations.

It's more likely that your machine is setup like this, but it doesn't mean that /usr/local is useless! If you find interesting applications that aren't officially part of your distribution, you can install them there. As an example, if you have a program that'd normally go to /usr/bin but it's not part of your distribution, you could install to /usr/local/bin instead, which will keep things nice and clean.

< /lib >

Shared libraries (again, hence the name) are kept here. They're dynamically linked - similar to DLL's on Windows.

< /home >

This is kind-of like My Documents. All your stuff goes here, and 'normal' users are only allowed to write to files within /home. You can even configure your Linux system so that /home for each user is hidden so that way your mum can't see what's in your /home!

< /root >

The 'root' user's home directory. Don't confuse this with the root directory (/) of a Linux system.

< /var >

Variable (again, with the naming!) data that changes/updates when your system is running is kept here. Here's some of the interesting subdirectories:

    */var/log*
    A directory that contains system log files. They're updated when the system runs, and         checking them out can give you valuable info about the health of your system. If         something in your system suddenly goes wrong, the log files may contain some info about         the situation.

    */var/mail*
    Incoming and outgoing mail is stored in this directory.

    */var/spool*
    This directory holds files that are queued for some process, like printing.

< /tmp >

Temporary files written by programs/files are stored here.

< /dev >

This is where CD's, floppy disks, USB drives etc are available. Remember, in Linux, everything is a file. For example:

    */dev/fd0* is your first floppy drive
    */dev/cdrom* is your CD drive
    [/i]/dev/hda[/i] is your first IDE HDD etc etc.

All the devices that your Linux kernel can understand are in here, which is why there are hundreds of files.

< /mnt >

This is your 'mount' point. Different physical storage devices (like HDD, floppies, CD's etc) must be attached to some directory in the file system tree before you can access them. This 'attaching' is called mounting, and the directory where the device is mounted is called the **mount point**.

This directory contains mount points for different devices. As an example:

    */mnt/floppy* would be the floppy drive
    */mnt/cdrom* would be your CD drive etc.

However - you don't [b]have]/b] to use this directory for this, you can really use whatever directory you want. Some distributions default to /floppy and /cdrom as the mount point.

< /proc >

This one is fun... It doesn't actually exist. It's just a virtual directory. It contains some kernel info. There's a whole bunch of numbered entries that correspond to all running processes on your system, and there's also named entries that permit access to your current configuration.

< /lost+found >

Here Linux keeps the files that it restores after a system crash or when a partition hasn't been unmounted before a system shutdown. This way you can recover files that would otherwise have been lost.

Adapted from Nana Långstedt's TuxFile at [http://www.tuxfiles.org]("http://www.tuxfiles.org").

---

### Post by el3ktro on 2006-02-05
Nice, this will definitely help some Windows converts understanding the Linux file system hierarchy. When you look at some newbie posts you'll know that it's very confusing for many of them!

Tom

---

### Post by Maelgwyn on 2006-02-05
Yeah, I had serious problems understanding this when I first started... I couldn't get my head around the "put everything in the /home folder" concept!

---

### Post by paulmilliken on 2006-02-05
Nice post thanks Maelgwyn.  Good to see another NZer on the forums too :)

Paul

---

### Post by Sutekh on 2006-02-05
I've bookmarked this Maelgwyn, good stuff!

---


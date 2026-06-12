---
title: "Ar-r-r-r-r-gh! - HELP Please! - Execute Permissions - CDROM"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Kerry Lange on 2006-11-19
Hi there:

I'm a newbie and have asked this question in Installation & Upgrades & Hardware & Laptops but either the question is too basic or *I'm* too basic.

I'm trying to get an installation program to run via the terminal off a CDROM but I'm getting an error message telling me I don't have permission.

I can't seem to figure out how to give myself execute permissions for the CD drive.  I edited the "fstab" file with no effect.  "chmod" doesn't work, as I need to be logged in as root (don't know how to log in as root either).  "sudo" doesn't work either.

Can ANYONE tell me what I need to do?

---

### Post by taurus on 2006-11-19
You can't change permissions on the CD-ROM since it's a read only device.  If you need to be root to install something from the CD, open a terminal, Applications -> Accessories -> Terminal, and run it from there with sudo...

```
sudo /media/cdrom0/<name of the program>
```
p.s.  If sudo doesn't work, then what is the output of this command, assuming that your CD is mounted on /media/cdrom0?

```
ls -la /media/cdrom0
```

---

### Post by Kerry Lange on 2006-11-19
Output of the command you spec'd is as follows:

```
dr-xr-xr-x 4 root root    2048 2006-11-15 20:52 .
drwxr-xr-x 7 root root    4096 2006-11-19 12:00 ..
dr-xr-xr-x 4 root root    2048 2006-11-15 20:52 dists
-r-xr-xr-x 1 root root    3112 2000-06-22 12:34 getlibcver
-r-xr-xr-x 1 root root 4378020 2000-06-23 20:58 install
-r--r--r-- 1 root root    3824 1998-03-24 13:25 newdaisy.gif
-r--r--r-- 1 root root   31302 2000-06-26 06:25 ReadmeFirst.html
-r-xr-xr-x 1 root root    9677 2000-06-22 12:34 remove-graphics9
dr-xr-xr-x 3 root root    2048 2006-11-15 20:52 Setup
-r--r--r-- 1 root root     282 2000-06-26 13:15 volinfo.txt
```

The reason I was thinking its a permissions issue is the fact when I run the following from the cd root:

```
sudo ./install
```

I get the following error message:

```
sudo: unable to execute ./install: Permission denied
```

---

### Post by PriceChild on 2006-11-19
btw instillation and upgrades is for the instillation and upgrade of the actual operating system.

---

### Post by taurus on 2006-11-19
Is install a binary or a script file?

```
file install
```
If it is a script file, that does the first few lines say?

```
more install
```

---

### Post by Kerry Lange on 2006-11-19
> **PriceChild said:**
> btw instillation and upgrades is for the instillation and upgrade of the actual operating system.

So noted.  Thanks.

---

### Post by Kerry Lange on 2006-11-19
Here's what file install yeilds:

```
install: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
```

So, it's not a script.

---

### Post by taurus on 2006-11-19
Try to copy the install to your $HOME and run it from there?

```
cp install ~/
cd ~
chmod 755 install
sudo ./install
```

---

### Post by Kerry Lange on 2006-11-19
Here's what results ('nother error message):

```
Log file name:/tmp/corel/Setup.log
Qt: Locales not supported on X server
X Error: BadValue 2
  Major opcode:  18
Aborted (core dumped)
```

I tried copying everything into a folder in my home directory during an earlier attempt at installing this program but got the same error, which is why I was trying to run it from the CD.  I thought the file might be designed to run from a CD but not from a HDD.

---

### Post by taurus on 2006-11-19
Are you trying to install Corel stuff?  What does the output of this command then?

```
ldd install
```

---

### Post by Kerry Lange on 2006-11-19
Yes, this is Corel PhotoPaint 9.

The result of the command you spec'd is as follows:

```
not a dynamic executable
```

---

### Post by taurus on 2006-11-19
Hmm...  What about the Setup directory?

```
ls -la Setup
```
Otherwise, you may want to have a look at the "ReadmeFirst.html" for any instruction on how to install it!

---

### Post by Kerry Lange on 2006-11-19
The files in the Setup directory are as follow:

```
comp.csw  Draw9.bil  license.txt  project.csw  relnotes.txt  setup.str  wizard
```

Here's the result of the command you spec'd:

```
dr-xr-xr-x 3 root root    2048 2006-11-15 20:52 .
dr-xr-xr-x 4 root root    2048 2006-11-15 20:52 ..
-r--r--r-- 1 root root 1438430 2000-06-22 12:34 comp.csw
-r--r--r-- 1 root root      28 2000-06-22 12:34 Draw9.bil
-r--r--r-- 1 root root   29714 2000-06-22 12:34 license.txt
-r--r--r-- 1 root root   11351 2000-06-22 12:34 project.csw
-r--r--r-- 1 root root   27783 2000-06-26 06:28 relnotes.txt
-r--r--r-- 1 root root  217888 2000-06-22 12:34 setup.str
dr-xr-xr-x 2 root root    2048 2006-11-15 20:52 wizard
```

I *am* (as far as I can tell) following the installation instructions from the "ReadmeFirst.html" file but nothing appears to work.  Here's the relevant part from the instructions:

```
To install Corel PHOTO-PAINT 9 for LINUX using a graphical file browser
1. Insert the CD-ROM into the CD-ROM drive.
2. Navigate to the CD-ROM drive, and run install.
If the setup program fails to launch from your file browser, see the instructions for installing Corel PHOTO-PAINT 9 for LINUX from a shell.

To install Corel PHOTO-PAINT 9 for LINUX from a shell (prompt)
1. Mount the Corel PHOTO-PAINT 9 for LINUX CD-ROM.
If your system does not automount the CD-ROM, you need to use the Mount command while logged in as root (e.g., mount -t iso9660 /dev/cdrom /mnt/cdrom). For further instructions, type man mount at the console.
2. In an X-Windows terminal program (Console in Corel LINUX), change to the root directory of the CD-ROM.
3. Type ./install, and press ENTER.
If you are not logged in as root, it will prompt for the root password to continue. After the installation is complete, you will no longer have root privileges, but only rights that are assigned to the user. 
```

and...

```
For Debian LINUX Users
Debian users may install the Debian packages using methods familiar to them.

To have the dependencies between packages automatically resolved, use apt-get as follows:
1. Log in as root, and make sure that the CD-ROM is a source in your "/etc/apt/sources.list" file.
2. Type the following commands at a shell prompt:
apt-get clean
apt-get update
apt-get install <package name>, where <package name> is graphics9-paint for Corel PHOTO-PAINT 9 for LINUX installation

Notes:
1. For more information on the "/etc/apt/sources.list" file, refer to the manual page by typing man sources.list.
2. The .DEB files with the dependencies can be found on the CD-ROM in the following directory:
/dists/stable/non-free/binary-i386/
/dists/stable/main/binary-i386/
3. Instructions for Debian users are also applicable to Corel LINUX users. However, Corel LINUX users who wish to use the Corel Update utility may follow the "To install program files using Corel Update" procedure.
```

---

### Post by taurus on 2006-11-19
Well, according to the instruction, you just open a terminal in X and navigate to where your CD-ROM is and run it to install it, except you need to use sudo since you can't log in as root...

Do you still have the install on your harddrive when you copied it over?  Run this command with the install already on your $HOME directory!

```
ldd install
```

---

### Post by Kerry Lange on 2006-11-19
Yes, the file is still there and when I run the command you spec'd, I get the following:

```
not a dynamic executable
```

To be precise, I've got the executable in the following directory:

```
home/kerry/expand/
```

If that makes a difference.

---

### Post by MrGuty on 2007-04-27
Hi.

I'm also a newbee and a long time Windows user.  And I experience the same problems.  I think it's just incredible that a third party application won't install automatically with the installer program.  This is why most people don't have the time to use Linux.  It's just too time consuming.  Are there anybody at all that has an easy answer to this question about installing Corel Photopaint in, for instance Ubuntu 7.04? :confused:

---


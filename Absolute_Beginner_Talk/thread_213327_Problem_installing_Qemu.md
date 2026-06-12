---
title: "Problem installing Qemu"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by tonyp1969 on 2006-07-11
Everything seems to be going swimmingly when this happens:-

39 (255.97 KB/s) - `install_qemu.sh.1' saved [10721/10721]

tony@tony-desktop:~$ chmod +x ./install_qemu.sh
tony@tony-desktop:~$ sudo ./install_qemu.sh
Your Ubuntu release is: Dapper Drake 6.06
Is this correct? y
Would you like to download QEMU from the CVS (Unstable)? y
Installing Dependencies...
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
g++-3.4 is already the newest version.
libsdl1.2debian is already the newest version.
libsdl1.2debian-all is already the newest version.
build-essential is already the newest version.
libsdl1.2-dev is already the newest version.
zlib1g-dev is already the newest version.
checkinstall is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Installing Kernel Headers (686)...
Reading package lists... Done
Building dependency tree... Done
linux-headers-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Preparing for Download...
Downloading QEMU...
--08:13:16--  
[http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-07-11_23.tar.bz2](http://qemu.dad-answers.com/download/qemu/qemu-snapshot-2006-07-11_23.tar.bz2)
           => `qemu-snapshot-2006-07-11_23.tar.bz2'
Resolving qemu.dad-answers.com... 66.98.184.92
Connecting to qemu.dad-answers.com|66.98.184.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:13:16 ERROR 404: Not Found.

Downloading KQEMU...
--08:13:16--  [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)
           => `kqemu-1.3.0pre9.tar.gz'
Resolving fabrice.bellard.free.fr... 212.27.63.117
Connecting to fabrice.bellard.free.fr|212.27.63.117|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 190,070 (186K) [application/x-gzip]

100%[====================================>] 190,070      482.09K/s

08:13:17 (481.58 KB/s) - `kqemu-1.3.0pre9.tar.gz' saved [190070/190070]

Extracting QEMU...
tar: qemu-snapshot-2006-07-11_23.tar.bz2: Cannot open: No such file or 
directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ERROR: Unable to extract QEMU.
tony@tony-desktop:~$

I must admit that I had to cancel the first attempt as it hung for over an hour.

---

### Post by 4ebees on 2006-07-25
Hi Tonyp1969,

Try something like:

-cdrom /dev/cdrom

---

### Post by moma on 2006-07-25
Install latest QEMU and KQEMU (accelerator) as instructed here
[http://www.futuredesktop.net/script-of-moma.html]("http://www.futuredesktop.net/script-of-moma.html")
Note 2).

But I haven't tried to get network functioning in QEMU. Propably the script needs to be extended.

Please check that /etc/init.d/bootmisc.sh is edited correctly.

The end of /etc/init.d/bootmisc.sh must look like this. (the green lines are added by inst_qemu.sh script)

[INDENT]
....
        ;;
esac
[COLOR="Green"]
# Added by root(0), Tue Jul 25 14:06:24 UTC 2006 ------BEG
# Load kqemu accelerator module
/sbin/modprobe kqemu

# Create kqemu device
mknod /dev/kqemu c 250 0 2> /dev/null

# Make it accessible to all users
chmod 666 /dev/kqemu 2> /dev/null
# Added by root(0), Tue Jul 25 14:06:24 UTC 2006 ------END
[/COLOR]
: exit 0
[/INDENT]


// moma
   [http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

---


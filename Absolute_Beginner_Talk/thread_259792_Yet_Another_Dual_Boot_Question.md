---
title: "Yet Another Dual Boot Question"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by BrianAT on 2006-09-17
I installed Ubuntu on my second hard drive (presently setup as NTFS, then the Linux Swap, then the Linux partition where Ubuntu is setup on).
Here is my boot.ini file:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\GRLDR="Start Grub"
```

Which works fine, and if I select Start Grub, it brings up a grub menu where it shows several Ubuntu choices.
These choices are not listed in my menu.lst (at least not the one on Windows' C: drive), but they must be pointing to the wrong partition as they try to start in 0,2 and have an Error 23: Partition doesn't exist, or something to that effect. Where is it getting the 0,2 info and how do I point it to 1,3, which is where partition magic says it is at?
The only way I can get into Ubuntu right now is the LiveDVD. I don't have a floppy drive, and for some reason my DVD drive no longer reads CDs, just DVDs. I also want to avoid messing with the MBR.
I also would prefer to boot into safe graphics mode, as from the LiveDVD if I use the regular mode, I don't see a thing but lots of lines running up and down the screen, probably a driver issue with the ones on the DVD, so until new drivers are installed on the hard drive version...
Anyone have any ideas on what is going on?

Here is my menu.lst in case it is needed:
```
default 1
timeout 60
# Sample boot menu configuration file
#
# Boot automatically after a minute.
# By default, boot the second entry.
# Fallback to the first entry.
fallback 0

title Windows XP
unhide (hd0,0)
rootnoverify (hd0,0)
chainloader +1
# For booting Linux

title Linux
root (hd1,3)
```

I could use Partition Magic to remove the NTFS partition on that drive, but I had the same problem the last time I tried installing and there was no NTFS partition that time. This time I intend to find a solution.

---

### Post by catlett on 2006-09-17
0,2 is 1,3 to grub. grub's values start at 0, so the third partition of the first drive is 0,2
the grub menu is found in /boot/grub/menu.lst To view it and change it if you think there is an error, install the ext2 driver in windows. Then you can access the ubuntu partition and get to /boot/grub/menu.lst (just to be thorough, the file menu.lst is in the grub folder which is in the boot folder) Here is the ext2 driver link [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bodhi.zazen on 2006-09-17
If you  Ubuntu FS is  not ext2 you can mount it and fix grub (menu.lst) with the live CD.

You need a full grub entry...

titile Ubutu
root (hd1,2)
kernel=/boot/vmlinuz.xyz root=/dev/hda3 ro quiet nosplash
initrd=/boot/initrd.xyz
boot

Hi catlett. At it again I see.

---

### Post by BrianAT on 2006-09-17
Thank you for the info about the ext2 driver. That may help a lot. That does look like the menu.lst it is using.
The question now is why does it not think that is a valid partition of 0,2 shows drive 1, partition 3?
Actually, I have to question why partition magic says it is drive 1, when that should actually be the second drive. Under windows, before installing Ubuntu, it was listed as drive E, after the C drive and the DVD drive. It was an empty drive. Just spare drive that I intended to use for backups of some data.

---

### Post by BrianAT on 2006-09-17
the menu.lst looks like it is a full grub entry that bodhi.zazen said to use.
I believe I used ext3... I can't recall why. I seem to remember it was better for something down the line... Should I reset it to ext2? Can that be done without having to reinstall?
In Windows my partition tool is Partition Magic 8.

Okay, here is the menu.lst from the Ubuntu's boot/grub directory:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdd3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdd3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdd3 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by Scunizi on 2006-09-17
If you're using SATA drives or PATA drives you should read [This]("http://www.ubuntu.com/download/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24")

The important part is below.  I really spent a lot of time trying to get Dapper installed until I found this.  I have 2 SATA drives and 1 ide and the installer just borked everything.  Even if you don't have raid but you have SATA, do this anyway an reinstall ... unless someone comes up with an easier solution.

> If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer.

---

### Post by bodhi.zazen on 2006-09-17
your grub entry looks a little off.

Post the oputput of ```
sudo fdisk -l
```

That is a small "L" and not the number 1.

ext3 is "journaled" ext2 and is an improved ext2, very standard, no need to change.

---

### Post by BrianAT on 2006-09-17
Okay, changing the 0 to a 1 in the menu.lst fixed it, to a degree anyhow.
I'll try changing the 1 to an l to see if that fixes the remaining problem.
I have to use recovery mode, if I use the first choice (the default) it just jumps back to the boot menu. 

When using the recovery mode, I am not 100% sure what I am supposed to do when it ends at:
root@brian-desktop:~#
Typing "exit" seems to make it continue on, but not 100% sure that is the correct path, but it works.

The first time into the main desktop, it had updates, then rebooted, no desktop, just a brown screen. Rebooted again, chose Gnome from the Options list and everything is good.

Thanks for all the help so far.
So only stuff to solve now is the jumping back to the boot menu if I choose the first option.
There is a minor question of how to hide the Linux drives from Windows now that the Ext2 driver is installed until I want to view them. (To keep Windows users from seeing what is on that partition.)

---

### Post by bodhi.zazen on 2006-09-17
Sounds like you are up and running. The ubuntu recovery mode boots to cli (command line interface) and not a gui. It is single user only and as you can see you are logged in as root. Used to fix things. You do not need this for now.

If you have any  specific questions beyond that I advise yo start a new thread.

[color=blue]Welcome to Linux[/color]

---

### Post by xhaan on 2006-09-18
> **BrianAT said:**
> Okay, changing the 0 to a 1 in the menu.lst fixed it, to a degree anyhow.
I'll try changing the 1 to an l to see if that fixes the remaining problem.
I have to use recovery mode, if I use the first choice (the default) it just jumps back to the boot menu. 

When using the recovery mode, I am not 100% sure what I am supposed to do when it ends at:
root@brian-desktop:~#
Typing "exit" seems to make it continue on, but not 100% sure that is the correct path, but it works.

The first time into the main desktop, it had updates, then rebooted, no desktop, just a brown screen. Rebooted again, chose Gnome from the Options list and everything is good.

Recovery mode is a minimal command line environment for repairing the system when it won't boot otherwise, like your system is doing now.

My first thought is that framebuffer may not be working properly on your system. Framebuffer is what allows the console to display actual graphic images instead of just text, it's what makes Ubuntu's nice boot splash screen work.

The reason I think the problem is the framebuffer is because when you boot in recovery mode it doesn't use framebuffer, and by exiting the root environment you're able to start GDM and login as a user with the full Gnome environment, which means xorg is working.

Unfortunately I don't know about fixing framebuffer problems, but framebuffer is enabled by the kernel so you can try editing the line in your menu.lst:

```
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdd3 ro quiet splash
```

and remove the 'quiet splash' options.
Try it and see if it helps.

edit: I overlooked something.
You'll also need to edit this part of menu.lst: 

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

delete the words 'quiet splash' and leave the rest of this part as is.

---

### Post by catlett on 2006-09-18
To hide the Ubuntu partitions in windows, go to the start menu and then to the control panel. That is where the shortcut 'IFS Drives' is found, it is easiest to find if you switch to 'classic view'.
Hit on that and your hard drive will be displayed as a bar graph with your partitions sectioned out. Each partition will have a drive letter attached to a drop down menu. Just drop down the menu and select 'none' and the drive will be hidden. When you want it again, just select a letter from the drop down.
You do not need to have the ubuntu partitions be ext2. Ext3 is the new improved file system but the driver is technically an ext2 driver. What that means is the file system when accessed from windows with that driver acts like an ext2 filesystem. Which means it will not have the journaling capabilities that were added to ext3. Long story short, keep your partitions ext3.

P.S. Hi bodhi

---

### Post by BrianAT on 2006-09-19
Thank you everyone for the help. Everything is almost working now. I am able to boot using the normal mode now that I commented out "savedefault." Not sure why it doesn't like that. I saw an error of some type pop up once while it was still there which led me to comment it out. I was able to put "quiet splash" back in even and it still works.

My only poroblem at the moment is that it won't update. It keeps saying "Only one software management tools is allowed to run at a time."
I tried a manual update, but I get a "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." Running that however freezes the computer.
I tried:
```
ps -e |grep syn
ps -e |grep apt
```
and both just return to the terminal prompt, so I guess they are not running.

Should it need to be known, I am using Ubuntu 6.06 LTS Dapper Drake.

EDIT: I must not have used "dpkg --configure -a" last time, as when I tried it again, it said I need SuperUser privlages, so I must have done another dpkg configure thing found in another forum somewhere.

---

### Post by catlett on 2006-09-20
Make sure you run the dpkg command with sudo
```
sudo dpkg --configure -a
```

---

### Post by BrianAT on 2006-09-20
> **catlett said:**
> Make sure you run the dpkg command with sudo
```
sudo dpkg --configure -a
```

Ah, well that changed things a bit. It now reboots once it hits the Generating Locales en_AU.UTF-8 bit rather then freeze there.

I read on another thread that they used
```
strace apt-get -f install >& /tmp/apt-get.txt
```
So I used that and did a strace on apt-get update as well, both from the recovery console so it was from root. I exited after both were done to read the results.

Here is the apt-get -f intall results:
```
execve("/usr/bin/apt-get", ["apt-get", "-f", "install"], [/* 25 vars */]) = 0
uname({sys="Linux", node="brian-desktop", ...}) = 0
brk(0)                                  = 0x522000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac1000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=33886, ...}) = 0
mmap(NULL, 33886, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg-libc6.3-6.so.3.11", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\374\1"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=658912, ...}) = 0
mmap(NULL, 1706736, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaabc2000
mprotect(0x2aaaaac5f000, 1063664, PROT_NONE) = 0
mmap(0x2aaaaad5f000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9d000) = 0x2aaaaad5f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\345\4"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=959808, ...}) = 0
mmap(NULL, 2083288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaad63000
mprotect(0x2aaaaae45000, 1157592, PROT_NONE) = 0
mmap(0x2aaaaaf45000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe2000) = 0x2aaaaaf45000
mmap(0x2aaaaaf4d000, 76248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaf4d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000>\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=546000, ...}) = 0
mmap(NULL, 1591784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaaf60000
mprotect(0x2aaaaafe5000, 1047016, PROT_NONE) = 0
mmap(0x2aaaab0e4000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x84000) = 0x2aaaab0e4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\37\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=54256, ...}) = 0
mmap(NULL, 1101488, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab0e5000
mprotect(0x2aaaab0f2000, 1048240, PROT_NONE) = 0
mmap(0x2aaaab1f1000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc000) = 0x2aaaab1f1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\305\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0755, st_size=1267512, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab1f2000
mmap(NULL, 2327016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab1f3000
mprotect(0x2aaaab310000, 1159656, PROT_NONE) = 0
mmap(0x2aaaab410000, 94208, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11d000) = 0x2aaaab410000
mmap(0x2aaaab427000, 16872, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaab427000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab42c000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab42d000
arch_prctl(ARCH_SET_FS, 0x2aaaab42cae0) = 0
munmap(0x2aaaaaac4000, 33886)           = 0
brk(0)                                  = 0x522000
brk(0x543000)                           = 0x543000
open("/dev/null", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
stat("/var/lib/apt/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/apt.conf.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
getdents64(4, /* 8 entries */, 4096)    = 264
stat("/etc/apt/apt.conf.d/05aptitude", {st_mode=S_IFREG|0644, st_size=80, ...}) = 0
stat("/etc/apt/apt.conf.d/10periodic", {st_mode=S_IFREG|0644, st_size=129, ...}) = 0
stat("/etc/apt/apt.conf.d/20archive", {st_mode=S_IFREG|0644, st_size=85, ...}) = 0
stat("/etc/apt/apt.conf.d/50unattended-upgrades", {st_mode=S_IFREG|0644, st_size=227, ...}) = 0
stat("/etc/apt/apt.conf.d/70debconf", {st_mode=S_IFREG|0644, st_size=182, ...}) = 0
stat("/etc/apt/apt.conf.d/99update-notifier", {st_mode=S_IFREG|0644, st_size=116, ...}) = 0
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/05aptitude", O_RDONLY) = 4
read(4, "aptitude::Keep-Unused-Pattern \"^"..., 8191) = 80
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/10periodic", O_RDONLY) = 4
read(4, "APT::Periodic::Update-Package-Li"..., 8191) = 129
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20archive", O_RDONLY) = 4
read(4, "APT::Archives::MaxAge \"30\";\nAPT:"..., 8191) = 85
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/50unattended-upgrades", O_RDONLY) = 4
read(4, "// allowed (origin, archive) pai"..., 8191) = 227
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY) = 4
read(4, "// Pre-configure all packages wi"..., 8191) = 182
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/99update-notifier", O_RDONLY) = 4
read(4, "DPkg::Post-Invoke {\"if [ -d /var"..., 8191) = 116
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/etc/apt/apt.conf", {st_mode=S_IFREG|0644, st_size=30, ...}) = 0
open("/etc/apt/apt.conf", O_RDONLY)     = 4
read(4, "Acquire::http::Proxy \"false\";\n", 8191) = 30
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=971145, ...}) = 0
stat("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=336216, ...}) = 0
stat("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=17, ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffffbe08d0) = -1 ENOTTY (Inappropriate ioctl for device)
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGWINCH, {0x406080, [WINCH], SA_RESTORER|SA_RESTART, 0x2aaaab2221b0}, {SIG_DFL}, 8) = 0
ioctl(1, TIOCGWINSZ, 0x7fffffbe0940)    = -1 ENOTTY (Inappropriate ioctl for device)
open("/var/lib/dpkg/lock", O_RDWR|O_CREAT|O_TRUNC, 0640) = 4
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
fcntl(4, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
open("/var/lib/dpkg/updates/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 5
fstat(5, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(5, F_SETFD, FD_CLOEXEC)           = 0
getdents64(5, /* 4 entries */, 4096)    = 104
close(5)                                = 0
close(4)                                = 0
write(2, "E: ", 3E: )                      = 3
write(2, "dpkg was interrupted, you must m"..., 90dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ) = 90
write(2, "\n", 1
)                       = 1
close(3)                                = 0
exit_group(100)                         = ?
```

For some reason, I thought there was an error about lock somewhere when I did it the first time, but I don't see it there this time...
Okay, here is the end part from the first time:
```
write(2, "E: ", 3E: )                      = 3
write(2, "Could not open lock file /var/li"..., 73Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)) = 73
write(2, "\n", 1
)                       = 1
write(2, "E: ", 3E: )                      = 3
write(2, "Unable to lock the administratio"..., 75Unable to lock the administration directory (/var/lib/dpkg/), are you root?) = 75
write(2, "\n", 1
)                       = 1
close(3)                                = 0
exit_group(100)                         = ?
```

Anyhow, here is the output from the apt-get update strace:
```
execve("/usr/bin/apt-get", ["apt-get", "updat"], [/* 26 vars */]) = 0
uname({sys="Linux", node="brian-desktop", ...}) = 0
brk(0)                                  = 0x522000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac1000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=33886, ...}) = 0
mmap(NULL, 33886, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg-libc6.3-6.so.3.11", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\374\1"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=658912, ...}) = 0
mmap(NULL, 1706736, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaabc2000
mprotect(0x2aaaaac5f000, 1063664, PROT_NONE) = 0
mmap(0x2aaaaad5f000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9d000) = 0x2aaaaad5f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\345\4"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=959808, ...}) = 0
mmap(NULL, 2083288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaad63000
mprotect(0x2aaaaae45000, 1157592, PROT_NONE) = 0
mmap(0x2aaaaaf45000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe2000) = 0x2aaaaaf45000
mmap(0x2aaaaaf4d000, 76248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaf4d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000>\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=546000, ...}) = 0
mmap(NULL, 1591784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaaf60000
mprotect(0x2aaaaafe5000, 1047016, PROT_NONE) = 0
mmap(0x2aaaab0e4000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x84000) = 0x2aaaab0e4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\37\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=54256, ...}) = 0
mmap(NULL, 1101488, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab0e5000
mprotect(0x2aaaab0f2000, 1048240, PROT_NONE) = 0
mmap(0x2aaaab1f1000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc000) = 0x2aaaab1f1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\305\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0755, st_size=1267512, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab1f2000
mmap(NULL, 2327016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaab1f3000
mprotect(0x2aaaab310000, 1159656, PROT_NONE) = 0
mmap(0x2aaaab410000, 94208, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11d000) = 0x2aaaab410000
mmap(0x2aaaab427000, 16872, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaab427000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab42c000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab42d000
arch_prctl(ARCH_SET_FS, 0x2aaaab42cae0) = 0
munmap(0x2aaaaaac4000, 33886)           = 0
brk(0)                                  = 0x522000
brk(0x543000)                           = 0x543000
open("/dev/null", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
stat("/var/lib/apt/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/apt.conf.d/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
getdents64(4, /* 8 entries */, 4096)    = 264
stat("/etc/apt/apt.conf.d/05aptitude", {st_mode=S_IFREG|0644, st_size=80, ...}) = 0
stat("/etc/apt/apt.conf.d/10periodic", {st_mode=S_IFREG|0644, st_size=129, ...}) = 0
stat("/etc/apt/apt.conf.d/20archive", {st_mode=S_IFREG|0644, st_size=85, ...}) = 0
stat("/etc/apt/apt.conf.d/50unattended-upgrades", {st_mode=S_IFREG|0644, st_size=227, ...}) = 0
stat("/etc/apt/apt.conf.d/70debconf", {st_mode=S_IFREG|0644, st_size=182, ...}) = 0
stat("/etc/apt/apt.conf.d/99update-notifier", {st_mode=S_IFREG|0644, st_size=116, ...}) = 0
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/05aptitude", O_RDONLY) = 4
read(4, "aptitude::Keep-Unused-Pattern \"^"..., 8191) = 80
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/10periodic", O_RDONLY) = 4
read(4, "APT::Periodic::Update-Package-Li"..., 8191) = 129
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20archive", O_RDONLY) = 4
read(4, "APT::Archives::MaxAge \"30\";\nAPT:"..., 8191) = 85
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/50unattended-upgrades", O_RDONLY) = 4
read(4, "// allowed (origin, archive) pai"..., 8191) = 227
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY) = 4
read(4, "// Pre-configure all packages wi"..., 8191) = 182
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/99update-notifier", O_RDONLY) = 4
read(4, "DPkg::Post-Invoke {\"if [ -d /var"..., 8191) = 116
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/etc/apt/apt.conf", {st_mode=S_IFREG|0644, st_size=30, ...}) = 0
open("/etc/apt/apt.conf", O_RDONLY)     = 4
read(4, "Acquire::http::Proxy \"false\";\n", 8191) = 30
read(4, "", 8191)                       = 0
close(4)                                = 0
stat("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=971145, ...}) = 0
stat("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=336216, ...}) = 0
stat("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=17, ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffffcc3ec0) = -1 ENOTTY (Inappropriate ioctl for device)
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGWINCH, {0x406080, [WINCH], SA_RESTORER|SA_RESTART, 0x2aaaab2221b0}, {SIG_DFL}, 8) = 0
ioctl(1, TIOCGWINSZ, 0x7fffffcc3f30)    = -1 ENOTTY (Inappropriate ioctl for device)
write(2, "E: ", 3E: )                      = 3
write(2, "Invalid operation updat", 23Invalid operation updat) = 23
write(2, "\n", 1
)                       = 1
close(3)                                = 0
exit_group(100)                         = ?
```

In both cases it looks like there is a problem with write(2, "E: ", 3E: ). E is the drive letter Windows used to assign to the drive Ubuntu is installed on.

---


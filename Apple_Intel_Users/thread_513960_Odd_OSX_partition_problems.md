---
title: "Odd OSX partition problems"
date: 2007-07-31
forum: Apple Intel Users
---

### Post by ripdog on 2007-07-31
I have been trying to mount my OS X partition in Kubuntu for a while now, but it appears that nothing can access it.

Running ```
fdisk -l
```
Simply causes fdisk to freeze for a second, display nothing and return to the command line.

```
parted
print
```

(In a root terminal) Prints this list:```
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI System Partition  boot
 2      210MB   217GB  217GB   hfs+         Merged_Untitled
 3      217GB   219GB  1572MB  linux-swap   Swap
 4      219GB   250GB  31.4GB  ext3         primary               boot

```

I then tried to run a check on partition 2...
```
(parted) check 2
Warning: The journal is not empty.  Parted must replay the transactions before
opening the file system.  This will modify the file system.
Fix/Cancel? Fix


You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

        http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

        http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (1.7.1)
along with the error message below, the output of

        parted DEVICE unit co print unit s print

and additional information about your setup you consider important.

Assertion (n > 0) at ../../libparted/exception.c:112 in function ped_log2()
failed.

```

Trying to ignore the error...```
Error: SEGV_MAPERR (Address not mapped to object)Aborted (core dumped)

```

And mount absolutely refuses to admit /dev/sda2 exists. I HAVE managed to mount this partition in an earlier installation of Ubuntu, (as well as get the sound working, which is another story entirely... ) And there have no major changes to the hard drive configuration since then.

NOTE: I DO have hfsplus and etc installed.

Thanks in advance... :)

---

### Post by cyberdork33 on 2007-07-31
I would first suggest booting an OSX DVD and repairing your OSX partition. I am pretty sure you are going to need it after that.

After that turn off journaling in OSX. Here is some good information on the subject.
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

MANY drive utilities (such as fdisk) will not work well with the GPT/MBR hybrid. Do not use them. I have used parted to resize a partition before, but after doing so running repairs to fix errors. All in all, I would suggest not fixing or checking an OSX volume under linux. I have only had trouble from doing so. If you REALLY want to, try Dirk's thread on checking HFS+ volumes.

You did not post the mount command you are using, so that might be helpful in determining the problem. Also, I have no idea what gave you the posted error. did it come from parted?

---

### Post by ripdog on 2007-07-31
Well, this is weird, i just did the exact same mount command as yesterday, and this time it worked. Well, im not sure what happened, but thanks for your help.

Bye the way, my mount command was:
```
mount /dev/sda2 /mnt/macos
```

---


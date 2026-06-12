---
title: "Problem Mounting cdrom"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by matrisking on 2007-07-11
Hi all,

I just installed ubuntu-server on a desktop and when I try to install certain applications via apt-get (in this case, openssh-server) it will ask me to insert the fiesty fawn cd.  However, when I insert the CD and hit enter, it just re-prompts me to insert the CD.

I checked out /media/cdrom0 with the cd in the drive and no files show up in the directory.  

I have had ubuntu installed on my laptop for a while and never ran into a problem getting it to recognizing discs like this.

Any advice?

Thanks!

matrisking

---

### Post by Ek0nomik on 2007-07-11
I'd like to point out that you don't have to install it off the CD.  You can download it from the repository instead of having it grab it off the CD.  You need to change your sources for this to work though.

By, "in the directory" do you mean cdrom0, or can you see a directory on the disc?  I am wondering because I have never actually looked at the contents of the Ubuntu install disc.

---

### Post by pizzutz on 2007-07-11
Well, I can solve the symptoms at least, if not the disease. You need to edit your /etc/apt/sources.list  and remove the lines at the top that refer to the fiesty cd.  This will force apt to use the latest versions from the repos instead of the versions on the CD. 

```
sudo nano /etc/apt/sources.list
```
put a # in front of the lines that reference the CD-ROM
```
sudo apt-get update
sudo apt-get install ssh
```
And you are set.

As far as your CD-rom mounting, I would need to see your fstab, and the output of the sudo mount command to get a better idea of the problem.

---

### Post by coquinho61 on 2007-11-13
HI all,

Well, I've got a similar problem that at least fits to the thread title :p

I cannot mount a cdrom. I expected it to automount when I put in my cd. Instead, nothing happened.

This is an ls -l of /dev/cdrom:

lrwxrwxrwx 1 root root 3 2007-10-31 18:27 /dev/cdrom -> hda

Which I found a bit weird. What is hda?

This is what I get when I do moun /dev/cdrom as root:

mount: can't find /dev/hda in /etc/fstab or /etc/mtab

Again, that strange hda. Hda used to be hard disk a, right? And partitions would be hda1, hda2 etc. 

Just for completeness, here is my /etc/fstab

# fstab
#
# !!START FSTAB INSTALL SCRIPT!! Do not mess. Do not remove this line
#
# Device          Dir                  Type      Options                  BN FN
#
/dev/systemvg/root /                   ext3      noatime,errors=remount-ro  0 1
/dev/systemvg/swap none                swap      defaults                   0 0
/dev/systemvg/var /var                 xfs       noatime                    0 2
LABEL=DATA        /data                xfs       noatime                    0 2
proc              /proc                proc      defaults                   0 0
LABEL=BOOT        /boot                ext3      noatime,errors=remount-ro  0 2
# fstab
#
# !!END FSTAB INSTALL SCRIPT!!
#


and /etc/mtab:

/dev/mapper/systemvg-root / ext3 rw,noatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/mapper/systemvg-var /var xfs rw,noatime 0 0
/dev/sda4 /data xfs rw,noatime 0 0
/dev/sda2 /boot ext3 rw,noatime,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0


Any clues? 

Thanks,

Coquinho

---


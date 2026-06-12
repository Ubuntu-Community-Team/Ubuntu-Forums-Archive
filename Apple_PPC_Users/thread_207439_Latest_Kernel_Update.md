---
title: "Latest Kernel Update"
date: 2006-07-01
forum: Apple PPC Users
---

### Post by RHTopics on 2006-07-01
I just completed a fresh install of Ubuntu 6.06 using the Shipit Live CD install.  I then did a full download and update of 93 packages using Update Manager.

The downloaded packages included an updated kernel (version 2.6.15-25-powerpc).

Rebooting the iMac after the updates were applied still shows the kernel being:
    2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux

In Synaptic, I can see the packages for 2.6.15-25-powerpc as being installed.

Any thoughts on why the newer kernel is not being loaded.

---

### Post by BoneKracker on 2006-07-01
what is the output from
```
uname -a
```

---

### Post by RHTopics on 2006-07-02
Output from uname -a

Linux challenger 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux

Do you know which log file to check for applied package updates?  I thought I would look in that log file to see if there were any error messages.

---

### Post by RHTopics on 2006-07-02
I found the log file for package updates.

It is /var/log/dpkg.log.

Using the System Log Viewer, here is a filtered search results for "installed linux-image";

2006-07-01 19:03:28 status installed linux-image-2.6.15-25-powerpc 2.6.15-25.43

---

### Post by BoneKracker on 2006-07-02
That's strange.

There's /var/log/aptitude, but I believe it gets overwritten each time.

Have you tried to dist-upgrade?

---

### Post by RHTopics on 2006-07-02
I do not find "/var/log/aptitude" on my system.

I have not done a dist-upgrade, but I am completely uptodate for a Ubuntu 6.06 installation after doing a reload and checking for upgrades through Synaptic.

I tried reinstalling the 2.6.15-25 linux image package through Synaptic.  It acted like it worked.  In fact when you look in the /boot directory, you see the following:

-rw-r--r-- 1 root root  248749 2006-05-23 09:10 abi-2.6.15-23-powerpc
-rw-r--r-- 1 root root  249070 2006-06-14 06:54 abi-2.6.15-25-powerpc
-rw-r--r-- 1 root root   57999 2006-05-23 08:45 config-2.6.15-23-powerpc
-rw-r--r-- 1 root root   57941 2006-06-14 06:25 config-2.6.15-25-powerpc
lrwxrwxrwx 1 root root      28 2006-07-01 19:43 initrd.img -> initrd.img-2.6.15-23-powerpc
-rw-r--r-- 1 root root 8594791 2006-07-01 19:42 initrd.img-2.6.15-23-powerpc
-rw-r--r-- 1 root root 8087425 2006-07-02 18:49 initrd.img-2.6.15-25-powerpc
-rw-r--r-- 1 root root  667985 2006-05-23 09:10 System.map-2.6.15-23-powerpc
-rw-r--r-- 1 root root  660245 2006-06-14 06:54 System.map-2.6.15-25-powerpc
lrwxrwxrwx 1 root root      25 2006-07-01 19:43 vmlinux -> vmlinux-2.6.15-23-powerpc
-rw-r--r-- 1 root root 4262734 2006-05-23 09:10 vmlinux-2.6.15-23-powerpc
-rw-r--r-- 1 root root 4207671 2006-06-14 06:54 vmlinux-2.6.15-25-powerpc

Yet, it still boots into 2.6.15-23.

---

### Post by zachws on 2006-07-02
same problem, is there a way to get 2.6.17.3 (latest stable?) or beyond?

---

### Post by christhemonkey on 2006-07-02
Hate to point out the obvious, 
But when booting did you go into the grub menu (press `esc`) and select to boot the new kernel?

---

### Post by zachws on 2006-07-02
[QUOTE=christhemonkey]Hate to point out the obvious, 
But when booting did you go into the grub menu (press `esc`) and select to boot the new kernel?[/QUOTE]

sorry to mention the obvious, but where do i press escape and choose new kernel? i was pressing esc pretty much the entire booting process and i got nothing.

---

### Post by christhemonkey on 2006-07-02
Just after your bios booting thing finishes, it should flash up
> loading GRUB, press 'esc' to enter GRUB menu...

That would be when you press escape...

---

### Post by zachws on 2006-07-02
humph... i guess i don't have grub.

---

### Post by RHTopics on 2006-07-02
zachws,

Well, I am glad not to be alone with this problem.

With the Mac version of Ubuntu 6.06, you go through yaboot instead of GRUB.

By creating the following symbolic links in the /boot directory, I am now able to boot to the newer kernel by choosing the "old" kernel from the second stage of the yaboot process (press tab key at second stage to see choices):

lrwxrwxrwx 1 root root 28 2006-07-02 22:37 initrd.img.old -> initrd.img-2.6.15-25-powerpc

lrwxrwxrwx 1 root root 25 2006-07-02 22:35 vmlinux.old -> vmlinux-2.6.15-25-powerpc

Yes, that is reversed from the way it should be, but I did not want to disturb the other symbolic links in /boot.

Oddly enough, I think this problem maybe related to the time problem I am having with Ubuntu 6.06.  The time stamp on the newer kernel files used UTC time (+6 hours), instead of local time.  This problem shows up as well when you do multiple "sudo" commands.  Example:

sudo: timestamp too far in the future: Jul  2 22:42:20 2006

I was hoping the newer kernel would have solved the sudo problem, but it is still there.

---

### Post by christhemonkey on 2006-07-03
Sorry didnt notice this was the mac forum! *slaps wrist*

---

### Post by zachws on 2006-07-03
[QUOTE=christhemonkey]Sorry didnt notice this was the mac forum! *slaps wrist*[/QUOTE]

ha, its ok. at least you tried to help. thanks a lot to you both.

---

### Post by rasec on 2006-07-03
I had the same problem upgrading the kernel to on my powerbook. I think there's a problem the way the ubuntu powerpc kernel package installs itself because it doesn't seem to add itself to the yaboot.conf file. To get the new kernel to work, edit the /etc/yaboot.conf file (you need to super user permissions, so use sudo with your editor) and add the following just above the first line that starts with image=

image=/vmlinux-2.6.15-25-powerpc
        label=update
        read-only
        initrd=/initrd.img-2.6.15-25-powerpc
        append="quiet splash"

After you save the file, do a `sudo ybin` and your new kernel should work the next time you start ubuntu.

---

### Post by RHTopics on 2006-07-03
To follow up on the approach I took to solve this problem, here some more information.

With approach taken by rasec, you are hardcoding a specific
kernel image in /etc/yaboot.conf instead of using symbolic links to the kernel images found in the /boot directory.  This may cause problems for you later on when new updates are applied.

Instead, just change the symbolic links in the /boot directory and leave the /etc/yaboot.conf unchanged.

Below is a listing from a bash script file that does just that for latest kernel update:
```
#!/bin/bash
# set_boot_links.sh

cd /boot

rm initrd.img.old
rm vmlinux.old

ln -s initrd.img-2.6.15-23-powerpc initrd.img.old
ln -s vmlinux-2.6.15-23-powerpc vmlinux.old

rm initrd.img
rm vmlinux

ln -s initrd.img-2.6.15-25-powerpc initrd.img
ln -s vmlinux-2.6.15-25-powerpc vmlinux

```


After running the script by using sudo, it will give you the following symbolic links in the /boot directory:

```
lrwxrwxrwx 1 root root      28 2006-07-03 08:24 initrd.img -> initrd.img-2.6.15-25-powerpc
-rw-r--r-- 1 root root 8594791 2006-07-01 19:42 initrd.img-2.6.15-23-powerpc
-rw-r--r-- 1 root root 8087644 2006-07-03 07:58 initrd.img-2.6.15-25-powerpc
lrwxrwxrwx 1 root root      28 2006-07-03 08:23 initrd.img.old -> initrd.img-2.6.15-23-powerpc
lrwxrwxrwx 1 root root      25 2006-07-03 08:24 vmlinux -> vmlinux-2.6.15-25-powerpc
-rw-r--r-- 1 root root 4262734 2006-05-23 09:10 vmlinux-2.6.15-23-powerpc
-rw-r--r-- 1 root root 4207671 2006-06-14 06:54 vmlinux-2.6.15-25-powerpc
lrwxrwxrwx 1 root root      25 2006-07-03 08:23 vmlinux.old -> vmlinux-2.6.15-23-powerpc
```

The lines beginning with "l" are the symbolic links or pointers to the actual kernel files.

Now, when you reboot and it comes to the second stage in the yaboot process, you can do nothing and it will default to the label "Linux" and boot up the latest kernel (2.6.15-25).  Or you can press the Tab key and see the two label choices of "Linux" and "old".  Entering "old" will cause the older kernel to boot up (2.6.15-23).

This worked for me, but another option, do nothing and wait until an official fix is ready.

---

### Post by BoneKracker on 2006-07-03
There are scripts that are supposed to do this automatically when the kernel is upgraded, but they apprarently did not do their job.  The approach you used, which leaves the generic symlinks and yaboot.conf in place, is best (because I would expect the kernel upgrade scripts to start functioning again at some point).

---


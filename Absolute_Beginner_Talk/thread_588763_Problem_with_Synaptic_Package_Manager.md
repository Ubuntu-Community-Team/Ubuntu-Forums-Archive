---
title: "Problem with Synaptic Package Manager"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by skier on 2007-10-23
This is better explained with the attached picture but I have a package marked for deletion that is interfering with me being able to install packages.  I don't believe that I marked it for deletion and I cannot de-select it.  I keep getting error messages.  Anyone know how to fix this?

---

### Post by rudeboyskunk on 2007-10-23
Go to a command line and type in this:

```
sudo apt-get update
```

It should give you instructions on how to fix it.

I think the fact that it's a modules package means it should not be removed...

---

### Post by ItsMitsHere on 2007-10-23
click on the olive green box with red cross mark, it should let you dis-select the module from remove list, however, as it is marked red, it might be redundant. that may be so, donot remove before a proper update from terminal. for that you should type **sudo apt-get update** and then **sudo apt-get upgrade** in the terminal. if you encounter any problem first try **sudo apt-get clean** and then again above said two comands for update and upgrade. in any case even if you remove the selected module by chance, do-not let your comp shutdown before upgrade and update!!!

---

### Post by skier on 2007-10-23
After running:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

This is the output...

Fetched 171MB in 32m20s (88.1kB/s)                                                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 149855 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ItsMitsHere on 2007-10-24
ok boy! now do some of the following things as applicable...

1. run **sudo apt-get --fix-missing** this is suppossed to fix the missing/broaken dependencies/installations
2. run **clean, update, upgrade** cycle once more as you did it previously
3. if the error still persists, try to start in erlier kernal when booting eg. 2.6.18.* or so if any erlier kernel is available.
4. check which kernel are you right now running by **uname -r** in terminal if it gives something like 2.6.23.* (only if there is 23) then you can safely remove older broaken kernel and modules by **apt-get autoremove**and again **clean, update, upgrade** cycle once more...

post back if any more problems...

---

### Post by skier on 2007-10-24
None of this is working.  I've wasted enough time trying to fix this.  I am going to do a clean install of Gutsy this weekend.  I was going to do an upgrade in the future anyway.

Thanks anyway to people that responded...

---


---
title: "nautilus utilization after fsck"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Adahn on 2007-12-09
I was sorting out some stability/RAM timing issues and had to run fsck after a failed boot.

I got into my desktop, but now Nautilus is hogging the cpu and I can't open any folders or run update manager or synaptic to check on things.
Firefox works fine, other than being a bit slower because of the cpu  usage.

help please!

(running Gutsy x86)

---

### Post by bsell on 2007-12-09
Open a terminal and type
```
nautilus --check
```
for Nautilus to run a self-check

Run the top command to see what processes are hogging the CPU.

---

### Post by Adahn on 2007-12-09
> **bsell said:**
> Open a terminal and type
```
nautilus --check
```
for Nautilus to run a self-check

Run the top command to see what processes are hogging the CPU.

that command gives this:

running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory

---

### Post by bsell on 2007-12-09
Run 
```
top
```

and post the display.

---

### Post by Adahn on 2007-12-09
> **bsell said:**
> Run 
```
top
```

and post the display.

I can't copy and paste from the terminal with top running.
suggestions?

---

### Post by bsell on 2007-12-09
> **Adahn said:**
> I can't copy and paste from the terminal with top running.
suggestions?
Post a PNG screenshot as an attachment.

---

### Post by Adahn on 2007-12-09
> **bsell said:**
> Post a PNG screenshot as an attachment.

I can't actually see this file on my desktop, but it shows up in the 'upload file' dialogue in firefox.

---

### Post by bsell on 2007-12-09
While running the top command, press k to kill nautilus. Use the PID of 5925 and the kill signal of 1. This will kill and restart Nautilus. Post the screenshot of the terminal window (Alt+Prnt Scrn).

---

### Post by Adahn on 2007-12-09
here:

any attempt to open 'home' or any other folder, or to access update manager is unsuccessful and  restarts nautilus

---

### Post by bsell on 2007-12-09
Bear with me, I noticed Nautilus did not restart. Can you open your /home directory and see if Nautilus hogs the CPU again? Can you post another screenshot? You may need to run fsck -a to automatically repair any filesystem errors it finds.

---

### Post by Adahn on 2007-12-09
here:

I did try running fsck, but saw the warning about corrupting the filesystem on a mounted drive, and chickened out.

---

### Post by bsell on 2007-12-09
Thanks, I noticed Nautilus isn't hogging as much of the CPU, but it is still slow. The filesystem must be unmounted for fsck to work properly. You will have to run the fsck in single-user mode to check the / filesystem. 

You can do this by changing the runlevel. The ```
runlevel
``` command will show your runlevel. 2 is the default for Debian systems. To change this you need to run the init command as root: ```
sudo init 1
``` You will be at a text console where you will enter the command ```
umount /
``` Run the command ```
fsck -a
``` Write down what it finds. Change the runlevel back to 2 and restart X or reboot if necessary. Post your findings. Be patient when dropping to runlevel 1, it takes some time to kill some processes.

---

### Post by Adahn on 2007-12-09
fsck -a came up 'clean'

The problem is the same after reboot.

---

### Post by bsell on 2007-12-09
It may a bug in Nautilus. Read the posts on this at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471)

Youi might try some of the solutions there. Best of luck.

---

### Post by Adahn on 2007-12-09
thanks for the assistance.

The cpu utilization aside, I still cannot access my home folder, synaptic, update manager, add/remove, etc.

---


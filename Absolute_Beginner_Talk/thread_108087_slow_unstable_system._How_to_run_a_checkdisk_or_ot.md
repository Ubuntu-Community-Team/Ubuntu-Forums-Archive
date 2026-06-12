---
title: "slow unstable system. How to run a checkdisk or other tool?"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2005-12-25
My ubuntu is really slow.
(intel celeron 800 Mhz, where can I find how much RAM this machine has?)

I don't dare to do a reboot again, because it froze last time. How do I create a recovery/boot floppy?

I tried to do a fsck, but the warning came up: never perform fsck on a mounted file system (my file system seemed to be mounted) what other tool can I use to inspect my hard drive?

---

### Post by auburn on 2005-12-25
I take it you dont' have a knoppix cd?

---

### Post by auburn on 2005-12-25
try typing "top" on the command line. That will give you amount of ram, and which processes are hogging all your horsepower. Hit q to quit.

---

### Post by towsonu2003 on 2005-12-25
```
free -m
``` to see RAM. In the output, look at the 'total'. the others are not the 'same' as in windows... Slowness might be because of swap use or too much CPU usage (or something else).  Check how much swap you are using. Also do the following for CPU eating program:

```

top
shift+F
k <enter>
q
```
Usually the first four programs are culpable... check out their CPU usage %. As for checking the memory usage from top, I am still so confused about the memory usage in linux that I cannot advice on that sorry...

You could post the output here for someone to comment though.

---

### Post by Herman on 2005-12-25
To cause it to do a file-system check during the next boot-up, type this into your terminal: 
```
sudo touch /forcefsck
``` Also, today I was playing around with my small test computer, (it's just a little 400mhz celeron 'Book PC', and I was doing some crazy things with it as usual ,and for some reason Ubuntu started running reeeeallly sllooow , as you describe. The filesystem check didn't help much, but what has fixed it was running the Ubuntu install disk, and mounting my Ubuntu partitions, and reformatting the swap area.
I don't know if that will help in your case or not, but it has worked for me once or twice before. The problem I had would have had to do with shutting the computer down wrong after an attempted install of another Linux system went wrong and I got stuck, so probably the RAM and swap were loaded with stuff off the CD, and it didn't get erased because of the improper shut-down. I don't think your problme would be the same as mine, but nevertheless, I thought that cure was worth mentioning just in case. It might be worth a try. (Herman)

---

### Post by Herman on 2005-12-25
Let me know if you need instructions before you try that second idea, because it is a little bit tricky, and it will take me some time to explain it properly, but I will if anyone wants to know how to do that. (Re-format the swap area usung the partitioner), likely someone will have a command for that for the terminal that will do the same thing a lot easier. (Herman).

---

### Post by auburn on 2005-12-25
Herman, I like the touch /forcefsck trick. I'll try that sometime.

---

### Post by stroopwafel on 2005-12-26
[QUOTE=auburn]I take it you dont' have a knoppix cd?[/QUOTE]
Why would I need a Knoppix cd? Isn't knoppix another distro?

I am actually looking for a distro that runs well on older computers.

---

### Post by BatsotO on 2005-12-26
well, you can run fsck safer with knoppix cd or slack cd or ubuntu live cd. maybe that's why he ask for knoppix cd. Just boot from the cd and run fsck.
As for older pc with low ram, you can try ubuntu with xfce (xubuntu), gnome eats up memory, and kde is out of the question with old low ram pc.

---

### Post by Herman on 2005-12-26
stroopwafel, just try this trick and see if it does any good or not:
Open up a terminal and type in the command:
```
free -m
``` Then check to see if your swap and memory are choked full.

To clear it do these two commands:
```
sudo swapoff -a
``` ```
sudo swapon -a
``` Then do again:
```
free -m
``` To see whether it worked or not. That's the answer , I think, that I was looking for.
That should clear your swap, but even if it doesn't work it won't hurt to try it.
I hope that helps you! :D (Herman)

---

### Post by stroopwafel on 2005-12-26
[QUOTE=Herman]To cause it to do a file-system check during the next boot-up, type this into your terminal: 
```
sudo touch /forcefsck
``` [/QUOTE]

How can this work if "sudo fsck" from the Command Line doesn't work (error: mounted file system)?

---

### Post by stroopwafel on 2005-12-26
Herman,

swapoff -a gives:
swapoff: dev/hda5/swap: cannot allocate memory

Any solutions?

(EXTRA QUESTION: How can I copy and paste output from the terminal, in order show you guys the oupput?)

---

### Post by Herman on 2005-12-26
stroopwafel, Ubuntu does a fsck during boot-up once every thirty starts by itself anyway, this command ([COLOR=Sienna]sudo touch /forcefsck[/COLOR]) just brings it on sooner. Your post is titled 'How to run a checkdisk or other tool?'.
Now your question:
> How can this work if "sudo fsck" from the Command Line doesn't work (error: mounted file system)? I don't know, it just does. Watch carefully during your next boot-up after entering the said command in your terminal, and you will see. Whether it solves your problem or not is another matter, but it might help and shouldn't do any harm. :D (Herman)

---

### Post by towsonu2003 on 2005-12-27
if problem is persisting, could you post the output of ```
free -m
top
``` thanks

for extra question: using gnome-terminal (thus using gnome), copy output (select text with mouse, right click, copy, paste here - do not close gnome-terminal before you are done copying). 

also, ```
sudo touch /forcefsck
``` creates a new file called forcefsck under / , which I guess forces fsck to run on next boot. have no idea about details, never tried, heard it here first :) 
fsck needs partitions to be _not_ mounted. As / can not be unmounted while you are running the computer, a live cd (thus knoppix suggestions) or running fsck at boot before / is mounted are remedies.

---

### Post by stroopwafel on 2005-12-27
Hi guys,

My christmas holidays here in Vermont are coming to an end and so is my "Linux experimenting time" on this IBM machine. I'm going back to Ontario and will try to install Linux on a PII lap top. Since GNOME is too big I'm going to try the following:

XUbuntu
Damn Small Linux
Flonix
Vector

Any suggestions which one would run best on an old PII laptop?

Herman: the fsck at boot up worked (although I used shutdown -rF) thanks
It didn't solve anything. I think my machine is just too slow.
I'm constantly using 120 of my 123 Mb RAM.

Towsonu2003: Here is the output of the terminal: (top and free -m):

```
str@ubuntu:~$ top

top - 12:31:54 up 9 min,  2 users,  load average: 0.47, 0.74, 0.44
Tasks:  73 total,   1 running,  70 sleeping,   2 stopped,   0 zombie
Cpu(s): 20.6% us,  6.1% sy,  0.1% ni, 49.2% id, 23.6% wa,  0.4% hi,  0.0% si
Mem:    125976k total,   118836k used,     7140k free,     1452k buffers
Swap:   361420k total,    54980k used,   306440k free,    37152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6331 root      15   0 85440  10m 3792 S 13.7  8.9   0:25.74 Xorg
 6882 dan       16   0 31264  11m 7488 S  3.9  9.3   0:08.51 gnome-terminal
 7085 dan       15   0  2124  980  752 R  2.0  0.8   0:00.02 top
    1 root      16   0  1564  532  460 S  0.0  0.4   0:01.72 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.03 khelper
    5 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   69 root      10  -5     0    0    0 S  0.0  0.0   0:00.15 kblockd/0
   96 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
   97 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
   99 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   98 root      15   0     0    0    0 S  0.0  0.0   0:00.51 kswapd0
  684 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1824 root      19   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2874 root      15   0     0    0    0 S  0.0  0.0   0:00.05 kjournald
 3000 root      11  -4  1660  556  484 S  0.0  0.4   0:00.24 udevd
 5593 dhcp      15   0  2328 1032  744 S  0.0  0.8   0:00.00 dhclient3
 6156 root      16   0  1820 1020  556 S  0.0  0.8   0:00.02 acpid
 6171 syslog    16   0  1760  756  636 S  0.0  0.6   0:00.02 syslogd
 6188 root      15   0  1564  400  328 S  0.0  0.3   0:00.02 dd
 6190 klog      15   0  2456  592  468 S  0.0  0.5   0:00.20 klogd
 6203 messageb  16   0  2140  788  752 S  0.0  0.6   0:00.03 dbus-daemon
 6216 hal       16   0  5052 2336 1480 S  0.0  1.9   0:00.81 hald
 6221 hal       18   0  1860  588  504 S  0.0  0.5   0:00.00 hald-addon-acpi
 6230 hal       16   0  1864  556  540 S  0.0  0.4   0:00.07 hald-addon-stor
 6269 root      15   0 10604 2048 1900 S  0.0  1.6   0:00.00 gdm
 6273 root      16   0 10932 2464 2160 S  0.0  2.0   0:00.07 gdm
 6342 cupsys    16   0  6284 1496 1120 S  0.0  1.2   0:00.76 cupsd
 6366 hplip     16   0 12608  880  876 S  0.0  0.7   0:00.00 hpiod
 6383 hplip     16   0  8824 1988 1432 S  0.0  1.6   0:00.02 python
str@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           123        115          7          0          1         36
-/+ buffers/cache:         78         44
Swap:          352         53        299
```

---

### Post by towsonu2003 on 2005-12-27
[QUOTE=stroopwafel]I think my machine is just too slow.
I'm constantly using 120 of my 123 Mb RAM.
[/QUOTE]
Your diagnosis seems to be correct. Looking at the CPU usage, it's not about the machine but the demands of the Gnome I think... If you ```
sudo apt-get install xubuntu-desktop
``` and use xfce, you shouldn't have any performance issues... Also, take a look at the forums on advice about **easy** performance tweaks (such as shutting off 2-3 of the virtual terminals etc, to minimize RAM usage. In gnome, using a simple browser (=not firefox) such as epiphany might help as well. 

As for the PII machine, I am running Xubuntu nicely on a Intel Celeron 300A Mhz (to be, that means very old :) ) with 64MB RAM very nicely (uses swap). 

Slackware (~), Damn Small Linux and also Puppy Linux are well known for 'old' machines. I never heard of Vector and Flonix before (here I go to distrowatch). Here is a list of distros distrowatch thinks are good for old computers: 
[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

It's a pity that the 'user-friendly' (sic) distros keep asking for newer hardware as well (although not as wildly as Microsoft).

---


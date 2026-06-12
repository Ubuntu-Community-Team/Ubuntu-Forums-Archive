---
title: "I accidentally installed ALSA driver to my desktop!"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-23
Oh, crap! Please help!
 
I just installed an M-Audio Revolution 5.1 according to these directions on this thread:

[http://ubuntuforums.org/showthread.php?t=400268&highlight=alsa+oss](http://ubuntuforums.org/showthread.php?t=400268&highlight=alsa+oss)

> Installing the latest Alsa drivers

I'll show you how to install Alsa properly. First of all you should run
Code:

sudo /etc/init.d/alsa-utils stop

This stops the Alsa machinery. I didn't do this first time I installed the Alsa drivers, and got some severe problems because of it. It's important that you do not forget the above command. Now, download the latest development release of alsa-driver, alsa-lib and alsa-utils from the Alsa webpage, and do the following with all the tarballs in the order I listed the three tarballs:
Code:

tar xvf <filename>.tar.bz2
cd <filename>
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo make
sudo make install

If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
Code:

cat /proc/asound/version

to check if you successfully upgraded Alsa. The first time you reboot after upgrading Alsa or installing a new system, you must increase the volume of all channels in alsamixer.

But I screwed up! I downloaded the tarballs to my desktop and installed the packages in /home/(my name)/Desktop/ !

Now I get this:

> anthony@anthony-desktop:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
anthony@anthony-desktop:~$ sudo /etc/init.d/alsa-utils restart
Password:
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
anthony@anthony-desktop:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
anthony@anthony-desktop:~$ ls /proc/
1     2396  4618  4832  6123  6347         ide         self
10    2397  4639  4875  6124  6533         interrupts  slabinfo
11    2547  4655  4899  6128  7            iomem       stat
135   3     4656  4907  6131  798          ioports     swaps
164   3491  4662  5     6134  8            irq         sys
165   35    4663  5041  6140  9            kallsyms    sysrq-trigger
166   36    4670  5861  6142  acpi         kcore       sysvipc
167   37    4679  5862  6144  buddyinfo    key-users   tty
168   38    4682  5905  6146  bus          kmsg        uptime
2     3873  4696  5925  6152  cmdline      loadavg     version
2007  4     4709  5960  6156  cpuinfo      locks       version_signature
2008  4181  4724  5974  6158  crypto       meminfo     vmcore
2061  4182  4742  6     6159  devices      misc        vmstat
2062  4184  4743  6067  6160  diskstats    modules     zoneinfo
2063  4186  4759  6105  6180  dma          mounts
2106  4188  4772  6108  6183  driver       mtrr
2185  4189  4773  6109  6313  execdomains  net
2186  4447  4821  6111  6338  fb           opensound
2187  4558  4822  6114  6344  filesystems  partitions
2341  4616  4824  6116  6346  fs           scsi
anthony@anthony-desktop:~$ cat /proc/asound/
cat: /proc/asound/: No such file or directory
anthony@anthony-desktop:~$ cat /proc/
cat: /proc/: Is a directory
anthony@anthony-desktop:~$ 


Now all those folders are installed on my Desktop!

Can I fix this? What should I have done to install them correctly?

Thanks!

Edit: Should I have unpacked in /usr/src?

---

### Post by samuraiCat on 2007-06-23
Sorry to self-kick, but I'm totally hosed.

---


---
title: "[SOLVED] 250GB HD Full?????"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-17
I ran  ```
sudo qtParted
``` and my drive is reading as full. I know this is not possible but after looking through my whole file system I cannot find a reason for it. I first became aware of the problem when trying to copy a dvd to my  hd and it reeported that there was no room. 

Where do I start?? I neeed some help, please.

---

### Post by hyper_ch on 2008-01-17
please run:

```

sudo fdisk -l

```

and

```

df -l

```

and post the output.

---

### Post by stchman on 2008-01-17
> **kindafunnylookin said:**
> I ran  ```
sudo qtParted
``` and my drive is reading as full. I know this is not possible but after looking through my whole file system I cannot find a reason for it. I first became aware of the problem when trying to copy a dvd to my  hd and it reeported that there was no room. 

Where do I start?? I neeed some help, please.

You may have been bitten by the 137GB BIOS limitation.  Some slightly older motherboards the BIOS is incompatible with hard drives that larger than 137GB.

If this is the case you will need to see if the motherboard manufacturer has a BIOS flash.

Let us know.

---

### Post by Het Irv on 2008-01-17
In the Main Menu under Accessories there is a disk utility (I cannot remember the name of it).  It should show a circular graph showing how much space different files are using.  I think you have to double click to see the details.  Sorry about no being more specific, but I am not sitting at a Linux Computer at the moment.

---

### Post by kindafunnylookin on 2008-01-17
> **hyper_ch said:**
> please run:

```

sudo fdisk -l

```and

```

df -l

```and post the output.
OK here we go:```
peter@Gutsy7_10:~$ sudo fdisk -l
[sudo] password for peter:

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe47c63f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       19457   156288321   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
peter@Gutsy7_10:~$ 

```and```
peter@Gutsy7_10:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            234378684 218957268   3515648  99% /
varrun                 1037460        92   1037368   1% /var/run
varlock                1037460         0   1037460   0% /var/lock
udev                   1037460       104   1037356   1% /dev
devshm                 1037460         0   1037460   0% /dev/shm
lrm                    1037460     23908   1013552   3% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc1            153834852   6025504 139994932   5% /storage
peter@Gutsy7_10:~$ 

```

---

### Post by kindafunnylookin on 2008-01-17
Here is the qtpartedfile:///home/peter/Desktop/Screenshot.png

---

### Post by hyper_ch on 2008-01-17
ok, the 250 gb drive is recognized just fine....

now do this:

```

cd /
sudo du -Sh --max-depth=1 > /home/USER/Desktop/output.txt
sudo chown USER.USER /home/USER/Desktop/output.txt

```

Replace USER with your username.

That will create a output.txt on your Desktop and it will list how much space each subdirectory is... once you know which one it is, go in there and run the du -Sh --max-depth=1 again or set max-depth to another value.

That way you should find out what uses all the space

---

### Post by kindafunnylookin on 2008-01-17
Thanks for the reply but there is nothing like that on my main menu- accesories. Still looking though.

---

### Post by hyper_ch on 2008-01-17
I'm wrong on that code... let me get this straight...

---

### Post by blueridgedog on 2008-01-17
A slight alternative to hyper_ch would be to just pipe it to more and search for the big dir
```
cd /
sudo du -Sh --max-depth=1 | more
```

Then cd to the offending dir and repeat.

---

### Post by hyper_ch on 2008-01-17
leave the --max-depth=1 away... just use:

sudo du -mS  > /home/USER/Desktop/output.txt

That will also output in Megabytes (approximately)... so you could import that then to a spreadsheet and sort it.

---

### Post by kindafunnylookin on 2008-01-17
> **blueridgedog said:**
> A slight alternative to hyper_ch would be to just pipe it to more and search for the big dir
```
cd /
sudo du -Sh --max-depth=1 | more
```Then cd to the offending dir and repeat.
OK that gave me:
```
peter@Gutsy7_10:~$ cd /
peter@Gutsy7_10:/$ sudo du -Sh --max-depth=1 | more
[sudo] password for peter:
8.0M    ./opt
4.0K    ./media
0       ./dev
12K     ./tmp
4.0K    ./mnt
4.0K    ./storage
16K     ./lost+found
0       ./sys
50M     ./boot
596K    ./root
4.0K    ./srv
6.3M    ./lib
4.0K    ./initrd
6.3M    ./sbin
4.0K    ./var
1.1M    ./etc
0       ./proc
4.0K    ./home
4.7M    ./bin
4.0K    ./usr
16G     .
peter@Gutsy7_10:/$ 
```

---

### Post by kindafunnylookin on 2008-01-17
> **hyper_ch said:**
> leave the --max-depth=1 away... just use:

sudo du -mS  > /home/USER/Desktop/output.txt

That will also output in Megabytes (approximately)... so you could import that then to a spreadsheet and sort it.

that gave me no result:
```
peter@Gutsy7_10:~$ cd /
peter@Gutsy7_10:/$ sudo du -mS > /home/peter/Desktop/output.txt
peter@Gutsy7_10:/$ 

```

---

### Post by kindafunnylookin on 2008-01-17
OK - I got the output text, I'll work on that for a while and let you know how I get on.

---

### Post by kindafunnylookin on 2008-01-17
> **Het Irv said:**
> In the Main Menu under Accessories there is a disk utility (I cannot remember the name of it).  It should show a circular graph showing how much space different files are using.  I think you have to double click to see the details.  Sorry about no being more specific, but I am not sitting at a Linux Computer at the moment.
I found it. Its called Disk Usage Analyzer. It's telling me that  vmware-server is using 116.8GB and the Windows XP that it runs is using another 90GB. I did have that installed but I thought I got rid of it. I have searched my whole file system for vmware-server and it will not come up.

Anyone out there have any ideas?

---

### Post by Aelfric5578 on 2008-01-18
I am, for all intents and purposes still very much a beginner, so I have no idea if this will work.  A few years ago, I had some weird problem where a single program that did not install correctly...and consequently did not uninstall correctly...managed to convince Ubuntu that my 40 GB hard drive was full despite the fact that this was essentially a fresh install at the time.  What ended up happening is there was something stuck in memory that was telling Ubuntu my hard drive was full even though it wasn't.  No one was able to help me on the forums, but a simple restart (actually turning the computer off before booting it) fixed all of my problems.

For all I know, you've restarted many times since this has happened, but I figured I'd suggest it anyway just in case it could help.  I know sometimes, users tend to never restart Linux since it doesn't require it as frequently as Windows does.

---

### Post by hyper_ch on 2008-01-18
```

sudo updatedb
locate vmware

```

That should give you a hint where it is... very likely it's not "vmware" itself but a virtual machine.

if the above doesn't return anything, do:

```

locate vmdk

```

---

### Post by kindafunnylookin on 2008-01-18
> **Aelfric5578 said:**
> I am, for all intents and purposes still very much a beginner, so I have no idea if this will work.  A few years ago, I had some weird problem where a single program that did not install correctly...and consequently did not uninstall correctly...managed to convince Ubuntu that my 40 GB hard drive was full despite the fact that this was essentially a fresh install at the time.  What ended up happening is there was something stuck in memory that was telling Ubuntu my hard drive was full even though it wasn't.  No one was able to help me on the forums, but a simple restart (actually turning the computer off before booting it) fixed all of my problems.

For all I know, you've restarted many times since this has happened, but I figured I'd suggest it anyway just in case it could help.  I know sometimes, users tend to never restart Linux since it doesn't require it as frequently as Windows does.

Thanks for the reply. I followed you suggestion to no avail, but it was a good suggestion that I had overlooked.

---

### Post by kindafunnylookin on 2008-01-18
> **hyper_ch said:**
> ```

sudo updatedb
locate vmware

```That should give you a hint where it is... very likely it's not "vmware" itself but a virtual machine.

if the above doesn't return anything, do:

```

locate vmdk

```

[COLOR=Red]That worked!! Progress [COLOR=Black]Thank you. Here is the output and rather than go into /var/lib as root and start deleting all the vm files, is there a safer, (better) way using the terminal ?
[/COLOR][/COLOR][html]peter@Gutsy7_10:~$ locate vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f011.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f010.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f006.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f001.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f003.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f007.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f009.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f008.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f002.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f005.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional 2/Windows XP Professional 2-f004.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f041.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f010.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f044.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f025.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f034.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f036.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f002.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f014.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f021.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f032.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f050.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f027.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f046.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f051.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f030.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f018.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f039.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f012.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f042.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f045.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f017.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f026.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f007.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f011.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f013.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f015.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f033.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f003.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f049.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f001.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f016.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f004.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f037.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f031.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f006.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f048.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f005.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f020.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f024.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f047.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f035.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f029.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f022.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f043.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f040.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f038.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f008.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f019.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f023.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f009.vmdk
/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-f028.vmdk
peter@Gutsy7_10:~$ [/html]

---

### Post by hyper_ch on 2008-01-18
if you want to get rid of all those (why do you have so many???), do this:

```

sudo rm -Rf /var/lib/vmware-server/Virtual Machines/*

```

That will delete all of the virtual machines.

---

### Post by monte48lowes on 2008-01-18
> **Het Irv said:**
> In the Main Menu under Accessories there is a disk utility (I cannot remember the name of it).  It should show a circular graph showing how much space different files are using.  I think you have to double click to see the details.  Sorry about no being more specific, but I am not sitting at a Linux Computer at the moment.

I found the program 'filelight'. This program is very cool. If you don't have it, it's availlable in the repos.

```
sudo apt-get install filelight
```

Mike

---

### Post by kindafunnylookin on 2008-01-18
I have learned more about Linux and Ubuntu during this problem than I thought possible. Thanks for your help and your willingness to share your knowledge.
Peter

---

### Post by fuseblower1123 on 2008-01-19
can't you just use Disk Usage Analyzer?

---

### Post by kindafunnylookin on 2008-01-20
> **fuseblower1123 said:**
> can't you just use Disk Usage Analyzer?
That's what I did. See post #15 in this thread.

---


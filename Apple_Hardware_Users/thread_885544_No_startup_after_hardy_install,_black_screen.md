---
title: "No startup after hardy install, black screen"
date: 2008-08-10
forum: Apple Hardware Users
---

### Post by vegenalle on 2008-08-10
Hello, hoi, heisan,


Mac mini PPC 1.5 Ghz, 512 MiB RAM, Airport Express

I tried a dual boot install on my PowerPC mini with Hardy 8.0.4.0, PPC alternate installer cd.

I built the important partitions in OS X using iDefrag and iPartition. I choosed about 50 GiB for OS X, 1 GB for swap, 100 Mb for New World Boot, about 15 GiB for Kubuntu and nearly 1 GiB free space. The partitions were in HFS+. Then I installed Kubuntu, partitioned manually (The 15 GiB as root, swap as swap, the New World Boot partition you guess it - boot flags on). I didn't format the partitions because there is a reminder that i would lose all data anyway, so I thought it's not necessary or will happen automatically. During the install I was able to download the language package I need (and the update files to 8.0.4.1 I guess?).

In some older posts i can read that the ubuntu partition has to be the first partition. Is this really (still) an issue?

Anyway. 

On startup i get the message:
 Cannot allocate ressource region 0 of device 1001.10.18.0 - 1001.10.19.0 …
The second boot stage is followed by a black screen.


Linux nosplash
Linux nosplash video=ofonly
Linux nosplash powerpc video=ofonly  
Linux nosplash video=radeonfb

didn't help.


What can I do?
Desperately waiting for a working Ubuntu …

---

### Post by tiresia on 2008-08-10
You are making things a bit too complicated!
Start the computer with your OSX Installer CD, make TWO Partitions with Apple Disk Utiliy. 
Just as example: if your HD is 80 GB you can make 30 GB Free Space and 50 GB HFS+ for Mac OSX. Install OSX.

When you are finished, start your Computer with the Ubuntu-CD. Hit TAB at the first Prompt and choose Linux-nosplash-ppc). When you are asked to make partitions, choose the option "guided- using free space" to install Ubuntu on the available free space. Parted will do the job for you. You must accept the option to format the partition (you can't loose anything, since the new partition is just empty&#8230; It won't touch your MacOSX partition). Well, you are done.

PS: If you wish more extra space to exchange data between Ubuntu and OSX make with the Apple Disk Utility, at the beginning of the process, THREE Partition. Let's say, as in example before: 25GB + 5GB + 50GB. 
You can choose to leave the 5GB unformatted, to format it as FAT32 (Both Systems can read and write FAT32, but there is a file limitation of 4GB), or to format it as HFS+ *not Journaled*. 
Ubuntu can access HFS and HFS+ (but it won't write to HFS+ *Journaled*). Ubuntu uses ext2 and ext3 filesystem. MacOSX can't access this fileSystem.  
So, if you wish a space to write and read from both Systems use FAT32 or *not-Journaled* HFS+

---

### Post by stream303 on 2008-08-10
Agree with Tiresia on this one - it is just simpler when installing Ubuntu to allow it to handle all the partitioning for you.  All you need to do in this case is to allow Ubuntu to install to "free space" and it will work out the rest.  No need for manual partitioning unless you have some specific needs.

The second thing you are facing is manually editing your /etc/X11/xorg.conf file after installation with rescue techniques to use the  video driver, and horizontal and vertical frequencies of your monitor.  Unfortunately, the ppc hardware doesn't always report back the right values to Linux probing.

---

### Post by vegenalle on 2008-08-11
> **stream303 said:**
> 
The second thing you are facing is manually editing your /etc/X11/xorg.conf file after installation with rescue techniques to use the  video driver, and horizontal and vertical frequencies of your monitor.  Unfortunately, the ppc hardware doesn't always report back the right values to Linux probing.

I was searching a lot of uu-threads and the web related to rescue mode and  /etc/X11/xorg.conf but could not find out how it would work. I'd need an exact description ;). I simply decided to install Kubuntu 7.0.4 then, and it is booting up as expected. No black screen. The problem is 

one - the external devices (USB stick e.g.) do not mount, if I'm lucky Ubuntu asks whether I want it to open in a new window. Afterwards exactly nothing happens.
two - I can't configure the WiFi successfully, could not during the installation process, even not now. Trying to configure manually I can only set a WEP password. Our WiFi is locked by a WAP pw.
This means also I cannot upgrade to 7.10/8.04. 
I'm stuck again …

---

### Post by stream303 on 2008-08-11
The good news is that now that 7.04 is installed, the values in the xorg.conf file can be used as a guide if you have to manually put them in yourself for 8.04.1.  What I'd do right now is to copy or print out these two files from 7.04 for safekeeping:

/etc/X11/xorg.conf
and
/etc/yaboot.conf

Now, if you decide to start over with 8.04.1, which is supposed to have much better wifi support (I'm not into wifi, so I can't really comment), as long as you can get to a command prompt you can edit xorg.conf to include the most important values such as your vertical and horizontal frequencies, and perhaps your video driver using the lines listed in the 7.04 install.  Hardy and most newer distros these days have very bare xorg.conf files, and it can be confusing to a beginner with nothing much inside it.  Fortunately those files from 7.04 can come to the rescue.

The key to modifying those files is to get to a command prompt somehow.  To make it easier, I usually recommend the "alternate" installer to at least get the system on the disk, where sometimes the live-cd desktop fails.

If the system boots, but drops you to a command prompt, don't worry.  If it doesn't drop you to a command prompt, try a virtual terminal, ie CTRL-ALT-F1.  If that doesn't work, you can go into rescue mode, which means that when you see the second-stage of the yaboot boot: prompt show up in the upper left, hit -tab- key.  This will stop the automatic countdown and you can now enter in some kernel parameters such as:

```
Linux rescue-powerpc
or
Linux rescue-powerpc64  <---(for G5's)

```

Once at a prompt, to edit the file, you can:

```
sudo nano -w /etc/X11/xorg.conf
```
Use CTRL=O to write out your changes, and CTRL-X to quit the editor.

You know that 7.04 works for the most part so you can return to it if you want.

Something to think about anyway...

---

### Post by vegenalle on 2008-08-12
> **stream303 said:**
> The good news is that now that 7.04 is installed, the values in the xorg.conf file can be used as a guide if you have to manually put them in yourself for 8.04.1.  What I'd do right now is to copy or print out these two files from 7.04 for safekeeping:

/etc/X11/xorg.conf
and
/etc/yaboot.conf

Now, if you decide to start over with 8.04.1, which is supposed to have much better wifi support (I'm not into wifi, so I can't really comment), as long as you can get to a command prompt you can edit xorg.conf to include the most important values such as your vertical and horizontal frequencies, and perhaps your video driver using the lines listed in the 7.04 install.  Hardy and most newer distros these days have very bare xorg.conf files, and it can be confusing to a beginner with nothing much inside it.  Fortunately those files from 7.04 can come to the rescue.

The key to modifying those files is to get to a command prompt somehow.  To make it easier, I usually recommend the "alternate" installer to at least get the system on the disk, where sometimes the live-cd desktop fails.

If the system boots, but drops you to a command prompt, don't worry.  If it doesn't drop you to a command prompt, try a virtual terminal, ie CTRL-ALT-F1.  If that doesn't work, you can go into rescue mode, which means that when you see the second-stage of the yaboot boot: prompt show up in the upper left, hit -tab- key.  This will stop the automatic countdown and you can now enter in some kernel parameters such as:

```
Linux rescue-powerpc
or
Linux rescue-powerpc64  <---(for G5's)

```

Once at a prompt, to edit the file, you can:

```
sudo nano -w /etc/X11/xorg.conf
```
Use CTRL=O to write out your changes, and CTRL-X to quit the editor.

You know that 7.04 works for the most part so you can return to it if you want.

Something to think about anyway...

Thank you stream303

Almost all text I wrote is gone. I don't know why.

---


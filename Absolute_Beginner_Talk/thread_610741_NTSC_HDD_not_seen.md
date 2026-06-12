---
title: "NTSC HDD not seen"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by pacmunchkin on 2007-11-12
I have read other threads and still can't get this to work.

Yesterday, I installed ubuntu on my laptop, over windows. Before I did this, I moved all of my documents onto a Toshiba External Hard Drive. 

After I had installed ubuntu, I plugged in the hard drive via usb and...nothing happened. Absolutely nothing. 

Please help.

edit: NTFS. not ntsc, wasn't thinking, sorry

---

### Post by phr0ze on 2007-11-12
Did you install Gutsy? It should auto-mount the drive when you plug it in, but I guess something is not working. If you browse through places -> Computer, can you see the drive?

Thanks,
John

---

### Post by Duck2006 on 2007-11-12
If you run

fdisk -l

from the terminal, can you see the usb drive?

---

### Post by pacmunchkin on 2007-11-12
Yes, i installed gusty.

If I go to places, it's not there.

---

### Post by Motorhead Kaze on 2007-11-12
Hi there.  I have an external NTFS and had problems with it not showing up before too.

1.  When my PC first got Ubuntu I had to configure my NTFS external HD.
Running Feisty at that time, I went to the Synaptic Package Manager, Searched for "Ntfsconfig", selected it, and applied it.  Next, I opened applications/system tools/ntfs configuration tool and ticked off the boxes to give me write support. Then I restarted the computer! Ctrl+Alt+Bksp isn't enough.  

Another problem?  I found this too:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

2.  Another episode I had was like this: 

Do you use another computer with that drive as well?  Maybe Windows?
When I used my external drive with XP then unplugged it (while running) and plugged it into my PC with Ubuntu it didn't appear.  I shutdown both computers, plugged it back into the laptop, shutdown properly, plugged it into my PC with Ubuntu, started up properly, and it was okay.

That's all I did, and was okay so I hope that's all you need.

---

### Post by pacmunchkin on 2007-11-12
> **Duck2006 said:**
> If you run

fdisk -l

from the terminal, can you see the usb drive?


```
cootey@cootey-laptop:~$ fdisk -l
cootey@cootey-laptop:~$ fdisk -l
cootey@cootey-laptop:~$ 

```

That's what happens when I type that in...

The Synaptic Package Manager, Searched for "Ntfsconfig", thing hasn't worked, so I'm going to plug it into a MS laptop and then remove it to see if that works... I assume you mean remove it rather than shut the computer down (or doesn't it matter)?

---

### Post by Duck2006 on 2007-11-12
Sorry it sould have been

sudo fdisk -l

---

### Post by pacmunchkin on 2007-11-12
```
cootey@cootey-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcabb571

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris
cootey@cootey-laptop:~$ 

```

This is what it has come up with

---

### Post by SpiritIsReality on 2007-11-14
howdy
could you se if there's any help here?
[http://ubuntuforums.org/showthread.php?t=603681](http://ubuntuforums.org/showthread.php?t=603681)

[http://www.google.ca/search?hl=en&q=+%22usb+hard+drive%22+site%3Aubuntuforums.org&as_qdr=m2&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=+%22usb+hard+drive%22+site%3Aubuntuforums.org&as_qdr=m2&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&as_qdr=m2&q=+%22usb+hard+drive%22+site%3Aubuntuforums.org&as_q=%28%22not+seen%22+OR+%22not+in+places%22&btnG=Search%C2%A0within%C2%A0results](http://www.google.ca/search?hl=en&as_qdr=m2&q=+%22usb+hard+drive%22+site%3Aubuntuforums.org&as_q=%28%22not+seen%22+OR+%22not+in+places%22&btnG=Search%C2%A0within%C2%A0results)

3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

trails

---


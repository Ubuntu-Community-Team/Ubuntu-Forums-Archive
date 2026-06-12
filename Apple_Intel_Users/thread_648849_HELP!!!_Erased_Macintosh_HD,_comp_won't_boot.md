---
title: "HELP!!! Erased Macintosh HD, comp won't boot"
date: 2007-12-24
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2007-12-24
Hi all.

Rather urgent situation. I recently purchased an new black MacBook, 160 GB HDD, 1 GB RAM, 2.2 GHz Processor. I wiped the HDD (Macintosh HD) using the Disk Util on the Leopard installation CD, thinking that I could then reinstall whatever I needed to. Apparently I thought wrong; now my computer won't even boot from CD - the Leopard install disk or Ubuntu live CD. Frankly, I'm lost. Any information pointing me in the right direction would be more than appreciated. If it helps any, I formatted the hard drive as FAT.

Thanks in advance.

(And really, I could use any help I can get. It doesn't have to be coherent, just as long as it's an idea) :)

---

### Post by lgambett on 2007-12-24
Try to keep pressed the C key (or Apple + C, I cannot remember) to boot from the original CD.

---

### Post by Aranel on 2007-12-24
And if that doesn't work, try holding down the Command key before you turn it on (and hold it down until something happens).

---

### Post by benanzo on 2007-12-24
and if either of those don't work just remove the hard disk, boot the ubuntu disc, then once the livecd is fully up replace the hard disk and re-format it.  Something tells be the GPT didn't get erased when disk util formatted the drive the first time, causing an endless loop as it reads/re-reads the GPT.

---

### Post by DGortze380 on 2007-12-25
Try holding "c" to boot from a disk, 
or hold "option" to choose where to boot from.

If that doesn't work, boot while holding "Command+v" and look for any errors or hold ups and post here.

---

### Post by RelativelyQuantum on 2007-12-26
Wow; thanks for all the help. I seem to be able to boot into Dapper by holding "option" before turning the computer on. That was a big improvement, since I was unable to boot into live CD by holding "C." Now all I need to do is get around the x server glitch, and I'll be set...

Again, thanks :)

---

### Post by RelativelyQuantum on 2007-12-27
This is a little strange: I am attempting to reconfigure my x server to communicate with the macbook screen (using Dapper, mind you). When I type "sudo nano /etc/x11/xorg.conf," I simply create a new document. Am I doing anything wrong?

---

### Post by stalefries on 2007-12-28
Do you have X installed? Try running 
```
sudo aptitude install x-window-system-core
```

---

### Post by RelativelyQuantum on 2007-12-28
I seem to have X installed already...might this work?

```
sudo dpkg-reconfigure xserver-xorg
```

I've tried a few combinations within the menus made available by running it, but with absolutely no luck. I don't think my video card is listed in the options the server presents, so I don't know what else to do.

Has anyone had similar issues on the Ubuntu install? Obviously it does work for macs...I just can't figure out how ](*,)

---

### Post by alpinesatan on 2007-12-28
lol, yes only hours ago!
i started from scratch as a resualt.
after inserting os x and pressing c you get to the install screen, and at the top there is a utility drop down.
Select disk util and set up a partition, the size is up to you. 
Follow through the install.
I then install rEFIt and install that.
Rebooted my macbook while inserting my ubuntu cd.
selected to boot from the cd at start up.
when ubuntu had loaded up navigated to partition editor/manager, here you will see your hard drive partitioned. on the second half or another partition that is empty i then formatted it using ext3.
when done install to the ext3 partition.
during the install there is a custom partition section i decided to just leave this alone.
i can now dual boot with no issues.

Hope this helps

---

### Post by alpinesatan on 2007-12-28
you find that you need to erase your discs and start again as if you did what i did which was install ubuntu on the entire disc, your whole hard drive will be using ext3 or 2 or whatever.

---

### Post by benanzo on 2007-12-28
> **RelativelyQuantum said:**
> This is a little strange: I am attempting to reconfigure my x server to communicate with the macbook screen (using Dapper, mind you). When I type "sudo nano /etc/x11/xorg.conf," I simply create a new document. Am I doing anything wrong?

The path should be **/etc/X11/xorg.conf** not **/etc/x11/xorg.conf**

Notice the capital X in X11

---

### Post by RelativelyQuantum on 2007-12-29
Thanks. I finally abandoned my attempts to install the older distros, though, and settled with Gutsy. The install went smoothly - no x server error this time - though I think the problem may have come from my trying to install an i386 ISO instead of an amd64/Intel. I downloaded the new image from Ubuntu.com, and off I went :)

---

### Post by RelativelyQuantum on 2007-12-29
> **benanzo said:**
> The path should be **/etc/X11/xorg.conf** not **/etc/x11/xorg.conf**

Notice the capital X in X11

Wow...I can't believe I let something like that go. Oh well. I guess I'll use Gutsy for awhile anyhow...

---


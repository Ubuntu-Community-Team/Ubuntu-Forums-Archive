---
title: "No boot options available"
date: 2009-12-04
forum: Apple Hardware Users
---

### Post by Greevous on 2009-12-04
A few days ago I was having some issues with my Macbook Pro (5,1), in that I wasn't able to reach the OS X login screen. At that time my Ubuntu partition was working fine, rEFIt was fine, and the boot loader was O.K.

I was trying things both in Ubuntu and the Mac installation cd (as in fsck and Mac disk utilities) to get OS X back to running condition, but to no avail. From this point on, the timeline is a little fuzzy because I didn't document anything, but basically rEFIt disappeared (at which point I was holding Alt/Option at startup to get to Ubuntu), then the Macintosh hard drive disappeared from the startup disk options altogether. I was able to use Ubuntu a little more until after a reboot it never got past choosing a video mode. Shortly after, my Ubuntu partition disappeared as well.

Through the live cd, I can still mount and browse both the Macintosh HD and my linux partitions (one for / and one for /home), so my personal files are safe for the time being. 

I thought I would be okay if I installed Ubuntu on an extra 5GB partition I had set aside, but even after a clean installation, I was presented with no boot options. I think that this is because there is no rEFIt any longer.

So, given that I can run a live cd and there are currently NO recognized disks capable of booting from, is it possible to get either the grub or rEFIt back? Thanks.

---

### Post by tom4everitt on 2009-12-05
You should put refit on a cd and boot from that: [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

When you've manage to get the refit menu, you should choose the refit partition manager, and let that sync your partition tables. 

Hopefully this will fix at least some of your problems. Let me know how it goes

---

### Post by Greevous on 2009-12-05
REFIt is back, showing both an Apple and Linux installation, but when I tried to boot into Ubuntu it didn't recognize any bootable disk. All I got was some white text on a black background telling me that and suggesting a restart.

---

### Post by tom4everitt on 2009-12-06
So OS X is working, and partition tables are synced?

In this case you probably just need to restore grub. Exactly how to do this depends on whether you have grub or grub2 installed, and your exact partition layout.

These are excellent guides on grub and grub2 respectively
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Or you can just tell me whether you have grub or grub2, and give me your output of 

sudo fdisk -l (in ubuntu), or
diskutil list (in os x)

and I can guide you.

---

### Post by Greevous on 2009-12-06
Yes, OS X is working (not recovered; out of necessity I did a clean reinstall), but I would really like to get back my Ubuntu installation without wiping the original.

I'm sorry, I don't know which grub I was using, but here's the output of diskutil list:

```
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *232.9 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            110.7 Gi   disk0s2
   3:         Microsoft Reserved                         5.1 Gi     disk0s3
   4:                 Linux Swap                         2.0 Gi     disk0s4
   5:       Microsoft Basic Data UNTITLED                10.0 Gi    disk0s5
   6:       Microsoft Basic Data home                    99.8 Gi    disk0s6
```

"Microsoft Reserved" is a blank FAT 32, and "Microsoft Basic... UNTITLED" is my root partition that I would like to boot into.

---

### Post by tom4everitt on 2009-12-06
And you did partition table syncing in refit? 

Now, if you installed ubuntu before October this year, it should be grub. 

So you should boot from a live cd with grub, which means any linux live cd except the latest ubuntu (karmic ie). 

Then open the terminal, and do:

```

sudo grub
root (hd0,4)
setup (hd0)
quit

```

this will reinstall grub to hd0, and point it towards your root partition hd0,4. Then you just reboot and everything should hopefully work :)

---

### Post by tom4everitt on 2009-12-06
You can of course just reinstall ubuntu and without wiping your home partition

---

### Post by Greevous on 2009-12-06
I followed those instructions, the grub is fixed, and I can boot into Ubuntu. Thank you so much for your help.

Tom - normally I would have reinstalled, but since everything was still intact I wanted to save myself the trouble of changing settings and installing software. But again, many thanks to you on behalf of the community as well.

---

### Post by tom4everitt on 2009-12-06
I'm glad it worked!

---


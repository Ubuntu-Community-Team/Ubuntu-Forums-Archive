---
title: "Fix rEFit start menu showing 3 icons for linux and how to sync GPT/MBR?"
date: 2014-01-18
forum: Apple Hardware Users
---

### Post by zircon_34 on 2014-01-18
I installed Ubuntu along MacOS X on MacBook Air 5,1, see [my thread]("http://ubuntuforums.org/showthread.php?t=2199210&p=12903758#post12903758"). I have a problem with my startup menu in rEFIt and need help to fix it.

Three icons show up for linux at startup, and I get default icons, no tux icon. It seems that the problem has to do because the [COLOR=#000000]GPT and MBR are not synced. Thats what I get in the rEFIT tool menu:[/COLOR]

[ATTACH=CONFIG]249571[/ATTACH]
 

[COLOR=#000000]I partitioned my [/COLOR][COLOR=#000000]hard disk in MacOSX but during installation I went to Gparted in Ubuntu and am wondering if thats the cause that rEFIT does not recognize linux in the GPT table?How can I fix this?

thanks for any help[/COLOR]:)[COLOR=#000000].[/COLOR]

---

### Post by zircon_34 on 2014-01-18
Has anyone installed a dual boot MacOS/linux with a extra /home partition in linux?

In this [thread]("http://www.tuxation.com/linux-on-mac.html") I saw its only possible to have 4 partition in a hybrid MBR/GPT table, 2 are gone for MacOSX, two left for linux. Since, I installed 3 partitions for linux: a SWAP, /(root) and /home I guess this is why I can't sync the table.

---

### Post by zircon_34 on 2014-01-22
Any help please?

---

### Post by Quackers on 2014-01-23
Hi could you please boot in to OSX and open a terminal and include in your next post the outputs from the following
```
sudo fdisk /dev/disk0
``` and
```
sudo gpt -r -vv show disk0
```

---

### Post by zircon_34 on 2014-01-23
```
[FONT=Menlo]Disk: /dev/disk0[/FONT][FONT=Menlo]geometry: 14751/255/63 [236978176 sectors][/FONT][FONT=Menlo]Signature: 0xAA55[/FONT]
[FONT=Menlo]         Starting       Ending[/FONT]
[FONT=Menlo] #: id  cyl  hd sec -  cyl  hd sec [     start -       size][/FONT]
[FONT=Menlo]------------------------------------------------------------------------[/FONT]
[FONT=Menlo] 1: EE    0   0   1 - 1023 254  63 [         1 -     409639] <Unknown ID>[/FONT]
[FONT=Menlo]*2: AF 1023 254  63 - 1023 254  63 [    409640 -  195549456] HFS+        [/FONT]
[FONT=Menlo] 3: 82 1023 254  63 - 1023 254  63 [ 195960832 -    7811072] Linux swap  [/FONT]
[FONT=Menlo] 4: 83 1023 254  63 - 1023 254  63 [ 203771904 -   13672448] Linux files*[/FONT]
```

```
[FONT=Menlo]gpt show: disk0: mediasize=121332826112; sectorsize=512; blocks=236978176[/FONT][FONT=Menlo]gpt show: disk0: Suspicious MBR at sector 0[/FONT]
[FONT=Menlo]gpt show: disk0: Pri GPT at sector 1[/FONT]
[FONT=Menlo]gpt show: disk0: Sec GPT at sector 236978175[/FONT]
[FONT=Menlo]      start       size  index  contents[/FONT]
[FONT=Menlo]          0          1         MBR[/FONT]
[FONT=Menlo]          1          1         Pri GPT header[/FONT]
[FONT=Menlo]          2         32         Pri GPT table[/FONT]
[FONT=Menlo]         34          6         [/FONT]
[FONT=Menlo]         40     409600      1  GPT part - C12A7328-F81F-11D2-BA4B-00A0C93EC93B[/FONT]
[FONT=Menlo]     409640  195549456      2  GPT part - 48465300-0000-11AA-AA11-00306543ECAC[/FONT]
[FONT=Menlo]  195959096       1736         [/FONT]
[FONT=Menlo]  195960832    7811072      3  GPT part - 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F[/FONT]
[FONT=Menlo]  203771904   13672448      4  GPT part - 0FC63DAF-8483-4772-8E79-3D69D8477DE4[/FONT]
[FONT=Menlo]  217444352   19531776      5  GPT part - 0FC63DAF-8483-4772-8E79-3D69D8477DE4[/FONT]
[FONT=Menlo]  236976128       2015         [/FONT]
[FONT=Menlo]  236978143         32         Sec GPT table[/FONT]
[FONT=Menlo]  236978175          1         Sec GPT header[/FONT]
```

---

### Post by Lars Noodén on 2014-01-23
I had a problem like that a while back and it was caused by me having grub installed twice, once in the mbr for my hard disk (sda for me) and again in the actual Linux partition (sda4 for me).  I solved it by deciding which one to keep and then nuking the other with dd.  I'm not comfortable or knowledgeable enough to suggest details since dd can make quite a mess but only the first 446 bytes needed to be cleared.  

Be sure to have working backup copies before experimenting.

---

### Post by zircon_34 on 2014-01-23
yep thats what probably happened, first install I let Ubuntu choose default for installing GRUB in the advanced partition manager window because I had no clue. The system did not boot correctly, so I reinstalled Ubuntu with GRUB this time on the /(root) partition, then it worked, still works, but could not sync partition tables. So I guess this may be part of the problem. I checked some threads but am quite scared to mess around with this kind of thing, especially that I like to know before Im doing... 

Does anyone happen to know if using dd could then make even OSX unbootable anymore, or is there no fear of loosing OSX recovery partition and its "safe" to try this, worst case I would have to reinstall OSX from a USB stick?

---

### Post by Lars Noodén on 2014-01-23
A bigger mistake in dd could render things unbootable.  If I were more knowledgeable about grub, I could make a better recommendation.  Do a lot of searching and reading, there's also a way of using dd to back up what you erase so you could put it back later if you realise that it was the wrong one.

---

### Post by zircon_34 on 2014-01-24
I was wondering if it wouldn't be more safe (but more work) to delete rEFIt and the Ubuntu partition using disk utility, reinstall OSX, reinstall rEFIT and then Ubuntu with Grub on the root partition?

---

### Post by Quackers on 2014-01-26
I'm really sorry for not replying sooner. I wasn't notified of any replies - something I'll look into.
All I can really say is that your MBR and GPT agree. They are not out of sync. Obviously the GPT has one extra partition (5) but that's only because the MBR can only contain 4 as a maximum. The start and end sectors agree completely, so that is not causing you any problem.

---

### Post by zircon_34 on 2014-01-28
Thats ok, thanks for the answer. I tried again to install Ubuntu on another Mac by installing the boot loader directly to the root partition \, but that did not help, I still got the same. Actually my computer booted directly into grub, so I could go into Ubuntu, but I could not boot anymore into MacOSx, so I had to put in the install CD and reinstall rEFIT in MacOS X, reboot and again I got the rEFIT with 3 icons for linux. Maybe it goes better with rEFIND but did not try it yet.

---

### Post by zircon_34 on 2014-02-02
Ok I managed to fix it! This [thread]("http://www.rodsbooks.com/ubuntu-efi/index.html") was really useful with information on GPT vs. hybrid GPT/MBR partition tables. I followed "fixing the installation" till point 10 and I installed rEFIND instead of rEFIT,  and installed the 64bit ext4 driver from the rEFIND folder to the efi folder on my mac: MacHD/Efi/refind folder.

I have now one boot icon for Ubuntu (with Ubuntu logo) and one boot icon for MacOS (apple logo)!

---

### Post by Quackers on 2014-02-02
Ok, good. So you installed Ubuntu normally then changed the hybrid MBR with gdisk to a protective MBR.
So you didn't install grub?
Now you can boot everything through refind.

---

### Post by zircon_34 on 2014-02-02
First it boots through refind, if I choose Ubuntu it shows me the Grub menu, I just choose Ubuntu and thats it!

---


---
title: "iMac only boots into Ubuntu (dual install)"
date: 2018-03-02
forum: Apple Hardware Users
---

### Post by debdrex on 2018-03-02
[COLOR=#000000][FONT=Arial]I installed Ubuntu 16.04 on a 9,1 iMac, early 2009 in a dual boot with OS X El Capitan. I installed rEFInd before installing Ubuntu. The rEFInd boot screen showed up at startup a couple of times before it stopped. Ater that I was still able to boot into OS X by pressing option. The computer booted into Ubuntu if I did nothing but start the computer. After some time, that changed and I was to no longer able to access OS X.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Now I would like to remove Ubuntu and switch back to OS X. However, I've been unable to get any other system to boot the computer so that I can do this. I’ve  tried booting by pressing the option key at startup, and by pressing the keys to start recovery in the in OS X. I’ve also tried booting from a reliable live USB of Ubuntu 16.04 and a bootable backup of the OS X partition that's on an external drive. However, the computer only boots into Ubuntu that’s installed on the computer.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I can still see the HFS + partition when I’m in Ubuntu.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Is there a way for me to wipe this drive and reinstall OS X?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by odydoum on 2018-03-08
Hello, it is possible that the boot order was changed because of a GRUB update. Can you please run from a terminal :

```
$ efibootmgr
```

The output should look like this : 

```
BootCurrent: 0080
Timeout: 5 seconds
BootOrder: 0080,0000
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0081* Recovery OS
Boot0082* 
BootFFFF* 

```

So here for example, i have 0080 boot first (the 'BootOrder' field), which is also where refind is. If this was not the case, and the boot order was for example 0000, 0080, you can then use the command
```
sudo efibootmgr -o 0080, 0000
```

to specify another order. PLEASE replace the numbers with your Mac entry number followed by the ubuntu entry number from the list.  Restart and you are set.

Regarding completely wiping the disk and reinstalling mac os, you can use the recovery partition, by pressing Command + R immediately after powering on your computer. From there you can format the disk and do a clean install.

---

### Post by debdrex on 2018-03-11
Thanks for replying! Here's the output from that command:
```
$ efibootmgr
BootCurrent: 0000
BootOrder: 0000,0080,BB04,CDB4,BD60,23B0,BD61,D018,BB32,6ED0,BFA8,5647,BEBB,D018,BB32,B918,BD62,6ED0,BFA8,C48C,BEBB,6EA0,BFA8,0601,BEBC,0B80,BEBC,6ED0,BFA8,54D2,BEBB,BF18,BD62,B018,BD62,BE18
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0081* Mac OS X
BootFFFF*

```

What are all of those entities listed in the boot order?! Also, if I decide to keep Ubuntu along with OS X will I need to run this command to change the boot order each time I want to switch systems? Thanks.

---

### Post by debdrex on 2018-03-25
Hi! It took me a while to get around to trying this. Here's what I got when I tried to change the boot order:

```
$ sudo efibootmgr -o 0080, 0000
Malformed boot order: 0080,
                           ^

```I also tried this:

```
sudo efibootmgr -o 0080, 0081, 0000, FFFF 
Malformed boot order: 0080,
                           ^

```

I still don't know what all of those entities are in the boot order. Any help that anyone can give me I'd greatly appreciate. Thanks!

---

### Post by oldfred on 2018-03-25
I think you have to have an entry after the comma.

See this for details on using efibootmgr to remove entries in UEFI. 
I know it works on a PC, but not sure about a Mac
man efibootmgr

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

---

### Post by debdrex on 2018-03-25
Thank you, oldfred, for your quick reply! Here's the output from the more verbose command:


```
$ efibootmgr -v
BootCurrent: 0000
BootOrder: 0000,0080,BB04,CDB4,BD60,23B0,BD61,D018,BB32,6ED0,BFA8,5647,BEBB,D018,BB32,B918,BD62,6ED0,BFA8,C48C,BEBB,6EA0,BFA8,0601,BEBC,0B80,BEBC,6ED0,BFA8,54D2,BEBB,BF18,BD62,B018,BD62,BE18
Boot0000* ubuntu    HD(1,GPT,67e12234-806f-4d98-9d0b-540c08545e5b,0x28,0x64000)/File(\EFI\ubuntu\shimx64.efi)
Boot0080* Mac OS X    PciRoot(0x0)/Pci(0x4,0x1)/USB(0,0)/USB(0,0)/HD(2,GPT,6b016c9f-cf9a-4411-a5bc-e1e2615d9e9d,0x64028,0x1b4c090)
Boot0081* Mac OS X    PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,adb05731-35bc-428d-a1b6-63592f793e22,0x64028,0x4a6be340)
BootFFFF*     PciRoot(0x0)/Pci(0xb,0x0)/Sata(0,0,0)/HD(2,GPT,adb05731-35bc-428d-a1b6-63592f793e22,0x64028,0x13515040)/File(\System\Library\CoreServices\boot.efi)
```


At this point I'd just like to be able to start up from the Mac OS instead of Ubuntu. However I'm not clear which of these I should boot from. Can you or anybody else help me decipher what this is telling me? Thanks!

---

### Post by oldfred on 2018-03-25
Your 80 looks like an USB boot, have you tried 81 as that says SATA.

Your Ubuntu entry is similar to a PC. 

Not sure why you have so many entries in BootOrder, but not actual boot entries.

---

### Post by debdrex on 2018-03-26
Hot dog!!!!! I'm back in Mac OS after using this command:

  ```
$ sudo efibootmgr -o 0081,0080,0000,FFFF
```

Thank you, oldfred. I was afraid I was never going to find my way back to this system.

---

### Post by oldfred on 2018-03-26
Still do not know Mac, but glad you were able to figure it out.

---


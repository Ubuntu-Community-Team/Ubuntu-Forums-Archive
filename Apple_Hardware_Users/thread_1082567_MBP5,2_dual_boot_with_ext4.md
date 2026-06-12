---
title: "MBP5,2 dual boot with ext4"
date: 2009-02-27
forum: Apple Hardware Users
---

### Post by inphektion on 2009-02-27
Anyone try this yet?  I have MBP 5,2 with OSX installed.  then installed Jaunty Alpha5 with ext4.  Haven't gotten it to boot yet...
Have rEFIt installed and it shows OSX and Linux Penguin to boot but when I click on the penguin it sits there for a while (sometimes forever) and eventually comes back with no bootable device.  
I've booted back into the ubuntu live cd and reinstalled grub per another forum post about this issue but still no luck.  Wondering if grub could be having an issue with ext4 but maybe not since it should be supported with jaunty. 
I've also run the rEFIt partition inspector and synced the tables up.

Here is output of partition inspector now:
```


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     84033575  Mac OS X HFS+
 3      495339520    625141759  Basic Data
 4       84033576    100033576  Linux Swap
 5      100033577    495338264  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     84033575  af  Mac OS X HFS+
 3 *    495339520    625141759  0c  FAT32 (LBA)
 4       84033576    100033576  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 495339520:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA), active

Partition at LBA 84033576:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 100033577:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 5, type Basic Data


```

---

### Post by cyberdork33 on 2009-02-28
you can't boot a partition beyond #4 in legacy OS mode. It appears that your root partition is #5?

---

### Post by inphektion on 2009-02-28
> **cyberdork33 said:**
> you can't boot a partition beyond #4 in legacy OS mode. It appears that your root partition is #5?

yes it is.  #4 is swap so If i switch 4 to be the ext4 and #5 to be swap I'll be set?
#3 is bootcamp xp and #2 is maxosx #1 is the efi partition.

sound good then if it switch the two?

---

### Post by inphektion on 2009-02-28
Well I moved the ext4 / partition to be /dev/sda4 and then made swap /dev/sda5. 
Then the install popped up a msg saying it couldn't format or mount swap and to go back to partioning.  Nothing I did could get past it.  Eventually I gave up and left the 8192MB of free space, the install is going now but without swap.  
I'll see if after the install i can format it as swap.  If not maybe I can't even see more than 4 partitions in legacy>  so does that mean if you triple boot you can't have swap at all then?
I have 8GB of ram so I was going to set swappiness to like 20-40 anyway but don't like the idea of running without swap?
pointers? ideas?

I don't necessarily need to triple boot the XP i was going to run in virutal box most the time from ubuntu.

---

### Post by cyberdork33 on 2009-02-28
> **inphektion said:**
> yes it is.  #4 is swap so If i switch 4 to be the ext4 and #5 to be swap I'll be set? yes that ought to work better.

> **inphektion said:**
> Well I moved the ext4 / partition to be /dev/sda4 and then made swap /dev/sda5. 
Then the install popped up a msg saying it couldn't format or mount swap and to go back to partioning. Nothing I did could get past it. Eventually I gave up and left the 8192MB of free space, the install is going now but without swap. 
I'll see if after the install i can format it as swap. If not maybe I can't even see more than 4 partitions in legacy> so does that mean if you triple boot you can't have swap at all then?
I have 8GB of ram so I was going to set swappiness to like 20-40 anyway but don't like the idea of running without swap?
pointers? ideas?

I don't necessarily need to triple boot the XP i was going to run in virutal box most the time from ubuntu.

well the Linux kernel is capable of reading the GPT where all the partition are really described. It is GRUB that uses the MBR partition table to figure things out, and the MBR table is limited to 4 entries. I don't know why you were having issues. I would try after the install... with 8GB of RAM, I don't think you will have any problems though.

P.S. Does your Windows install still work?

---

### Post by inphektion on 2009-02-28
I never installed windows yet.  just made the partition for it originally with the bootcamp assistant in mac.  
I'm debating whether its worth the triple boot hassle cause I really just need windows in a VM just thought it would be nice to be able to boot it natively.

---

### Post by cyberdork33 on 2009-02-28
> **inphektion said:**
> I never installed windows yet.  just made the partition for it originally with the bootcamp assistant in mac.  
I'm debating whether its worth the triple boot hassle cause I really just need windows in a VM just thought it would be nice to be able to boot it natively.
oh. Well that is definitely something to consider upfront. I think you will be ok if you install it last as  long as you installed grub to the root partition rather than the MBR.

---

### Post by inphektion on 2009-03-01
Yea i'm in the testing phase of what i want to do.  I just killed the bootcamp partition now and have ubuntu in /dev/sda3 and swap in /dev/ds4.  
I booted the live cd and used the partition manager to format the ext4 and swap then I went through the installer and it worked.  Could be some bug in the installer with formatting and using partitions cause for 1. it wouldn't format/use swap and 2. after I booted into it, df -h showed it was installed in a 8gb parition which would only have been the swap one...  Weird.  
So I redid it all outside of the installer and just re-installed.  

Once I get this entire drive partitioned how I want any recommended way to clone it (entirely) or individual partitions for easy restore in case some upgrade messes it up later?

---

### Post by inphektion on 2009-03-01
Man, not going well.  
went to install the restricted drivers for the wireless... computer froze.  had to hold down power button to turn off, turned back on and now won't boot into ubuntu.  first message is ACPI something about a gzip and bad magic number and then a kernel panic about VFS not syncing.

Wonder if this is ext4 related...  Maybe I should make a /boot of ext3 then mount / on ext4.

---

### Post by inphektion on 2009-03-01
ok instead of solving this no boot issue with the kernel panic, which i'll do if it happens again, i'm just assuming its something with the new ext4 so here is what i'm doing now.
/boot , ext3, 128MB
/ , ext4, 50GB
/home, ext4, 200GB
swap, 4GB

Is 50GB good for /?  I usually never separate out partitions so not sure.  I think the generic install takes 6-8GB so I figure over time 50 should be fine... I do install a lot of stuff though.

---

### Post by cyberdork33 on 2009-03-01
> **inphektion said:**
> ok instead of solving this no boot issue with the kernel panic, which i'll do if it happens again, i'm just assuming its something with the new ext4 so here is what i'm doing now.
/boot , ext3, 128MB
/ , ext4, 50GB
/home, ext4, 200GB
swap, 4GB

Is 50GB good for /?  I usually never separate out partitions so not sure.  I think the generic install takes 6-8GB so I figure over time 50 should be fine... I do install a lot of stuff though.
yea 50 should be fine unless you go nuts installing software. That error sounds like a file read problem, and that would most likely be related to the filesystem...

---

### Post by inphektion on 2009-03-01
I feel like i'm thread crappin' on my own thread...
but anyway has anyone gotten usbhid-dkms to install on this with jaunty x86_64?  
I'm getting an error that it can't find /usr/src/usbhid-blah blah
and so just errors out.
This is preventing other packages from the mactel ppa from installing as they depend on it.

also in the sources.list I had to make it intrepid as jaunty came up with nothing though there looks like there is a jaunty...

---

### Post by cyberdork33 on 2009-03-01
> **inphektion said:**
> I feel like i'm thread crappin' on my own thread...
but anyway has anyone gotten usbhid-dkms to install on this with jaunty x86_64?  
I'm getting an error that it can't find /usr/src/usbhid-blah blah
and so just errors out.
This is preventing other packages from the mactel ppa from installing as they depend on it.

also in the sources.list I had to make it intrepid as jaunty came up with nothing though there looks like there is a jaunty...
yea none of the packages have been upgraded for jaunty yet. It looks like that package is only for the 5,x models and I don't have one to test. It may be that the changes it makes are already included in the new kernel though... what is the specific package you are trying to install that depends on it?

---

### Post by inphektion on 2009-03-01
compizconfig-settings-manager was the first.

Mainly I can't even get wifi connecting and the restricted driver is activated for the broadcom so i started installing the PPA stuff to see if it might have helped.  

thanks for all your replies.

---

### Post by cyberdork33 on 2009-03-02
> **inphektion said:**
> compizconfig-settings-manager was the first.
???
This should not have anything to do with the Mactel-Support PPA since it comes from the normal Repos.

> **inphektion said:**
> Mainly I can't even get wifi connecting and the restricted driver is activated for the broadcom so i started installing the PPA stuff to see if it might have helped.
Well, that is defintely not addressed in any of our PPA packages. 

Make sure that the b43 module is not loaded (and blacklist it in /etc/modprobe.d/blacklist), and add 'wl' to /etc/modules. Then reboot and see if it is working.

---

### Post by inphektion on 2009-03-02
Well in the office today wireless is working.  seems it just couldn't connect to the "hidden" wpa2 network I have at home.  
I guess a bug in the restricted driver...

---

### Post by cyberdork33 on 2009-03-02
> **inphektion said:**
> Well in the office today wireless is working.  seems it just couldn't connect to the "hidden" wpa2 network I have at home.  
I guess a bug in the restricted driver...
hidden SSIDs only cause problems on any hardware.

---


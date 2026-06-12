---
title: "Gearing up for first ubuntu install on removable disk"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by dfarce on 2007-04-07
Hi everyone,
Just joined the forums because I've been getting ready to install linux on to a removable USB hard drive I have lying around. I finally decided to take the challenge and see If I could do it. A few basic questions. I am going to do the install on a romovable USB hard drive which currently has two partitions, a 20GB backup partition for my windows PC and an 8.5GB partition which i am going to delete and install ubuntu on. 

Should I delete the partition before trying to install or leave the partition (currently formatted with FAT32) and ubuntu should recognise it? 

Second, will I be able to carry this with me? I want to be able to take this to a friends house and run my desktop on his computer. Will Ubuntu be able to handle switching computers frequently without too much trouble?

Third, I am completely and totally new to Linux and I need a little help nstaling Ubuntu and setting it up.

Fourth, I could just use the live CD but I want to try the install and see how it goes and if it goes awry then I can just delete the partition right? and I won't have to worry about screwing up the data on my or my friends pc?

my pc goes as follows:
ASUS M2N32-SLI DLX
AMD Athlon 4600+ AM2 
1GB kingston DDR2/800
Western Digital 250GB sata II (one partition with windows xp pro)
EVGA 7600GS 256mb
benq DVD LS DW1655
(no floppy)
External drive plug 'n' play usb external 3.5' holding maxtor 2 F030J0 (one 20GB backup partition one 8.6GB partition not holding anything)

My friend's PC is as follows:
Gigabyte board (not sure exact type)
Intel E6300
1GB OCZ DDR2/533
Seagate 160GB sata II (one xp home partition)
EVGA 7600GT 256mb
DVD Rw drive (not sure exact type)
CD-RW/ DVD ROM drive "          "
(no floppy)

will an external linux instalation work? and im debating whether or not to actually unplug my internal sata drive incase I royally screw up so I dont lose any data. would there be any chance of deleting whats on my old drive if I leave it hooked up? ALSO, could someone point me in the direction of a really good installation FAQ for beginners? I was thinking version 6.10 but is it stil in beta? or should I go for version 6.06.1?

Thanks some advice would be greatly appreciated

---

### Post by chewearn on 2007-04-07
> **dfarce said:**
> Hi everyone,
Just joined the forums because I've been getting ready to install linux on to a removable USB hard drive I have lying around.
Welcome to the community!:KS

>  I finally decided to take the challenge and see If I could do it. A few basic questions. I am going to do the install on a romovable USB hard drive which currently has two partitions, a 20GB backup partition for my windows PC and an 8.5GB partition which i am going to delete and install ubuntu on. 
Have you already installed ubuntu (or other linux distros) the regular way a number of times, i.e. on internal harddisk?  If you have, then great, you should probably be aware how grub/linux bootloader works and how to configure it, etc.  Else, if you have not, it might not be advisable to do this on your first try at linux.

> Should I delete the partition before trying to install or leave the partition (currently formatted with FAT32) and ubuntu should recognise it? 
I would suggest delete the partition, leave it unallocated, then instruct ubuntu installer to use the free space.

> Second, will I be able to carry this with me? I want to be able to take this to a friends house and run my desktop on his computer. Will Ubuntu be able to handle switching computers frequently without too much trouble?
As far as I understood it, you will have to create a "live usb", for this to work.  There are instructions/how-tos to do this.

Regular installation will involved specific drivers and such, which will break if you change the hardware.  E.g. you have nvidia card, and might install nvidia driver.  But if your friend PC don't have nvidia card, you will get xserver error.

> Third, I am completely and totally new to Linux and I need a little help nstaling Ubuntu and setting it up.
Ok, back-up to my response above.  Installing the regular way should be quite straight forward,  Installing on external usb drive is slightly more complicated, though there are plenty of how-tos around.  But if it messed up, it could get real frustrating.:(


My 2 cents summary:
Go ahead and try, but only on a PC you could afford to mess up.

Else, if you just want to try ubuntu (maybe looking to ditch Windows in the future :wink:), this might not be the easiest way to go about it.

---

### Post by dfarce on 2007-04-08
First, I have never done anthing to do with linux. No normal installs. Second, the dea of a live USB seems like a good idea, if it would work like a normal install but be able to switch computers. By that I mean that I should be able to save files and suc to the USB right? So I need how tos
to make a live USB and how to do a USB install. Can someone send me a few links? I was wondring if I could start with a USB install then convert it to a live USB after? 

I am ready to try a few installs to get it right because I am just going to completely disconnect my PC drive from my computer before tryin to install, so I cant possibly mess anything up.

---

### Post by dfarce on 2007-04-08
After A little research I have found three live USB ish ways of doing this.

[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)

that is a windows emulation of linux and would be the easiest to install and use

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

this is how to get a live USB running with an actual linux installation and the final solution would just be to plug my ide drive right into my computer and instal it like a normal version of linux. could I unplug my primary drive and install on the secondary then configure GRUB AFTER I've already installed linux? without too much trouble?

Now, I'm not so sure whether this means anything but my external harddrive isnt listed in removeable storage with my flash drives(when plugged in) they categorized with my other hard drive. Might this make an installation easier?

---

### Post by chewearn on 2007-04-08
> **dfarce said:**
> After A little research I have found three live USB ish ways of doing this.
[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)
that is a windows emulation of linux and would be the easiest to install and use
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)
this is how to get a live USB running with an actual linux installation and the final solution would just be to plug my ide drive right into my computer and instal it like a normal version of linux. could I unplug my primary drive and install on the secondary then configure GRUB AFTER I've already installed linux? without too much trouble?
Those links should be ok, though I have not personally tried them yet (but was planning to, once I could spare a 1GB flash drive). :)

Yes, it should be relatively simple to configure grub.  Normally, the biggest problem I see from new users (coming from Windows environment), is unfamiliarity with the linux command line, and how grub works.  I guess you have really done your research, so you should be ok (most of those new users don't even know what grub is :)).

> Now, I'm not so sure whether this means anything but my external harddrive isnt listed in removeable storage with my flash drives(when plugged in) they categorized with my other hard drive. Might this make an installation easier?
Not really sure if this will make a difference.

Well, good luck!  Wish you success.

---

### Post by dfarce on 2007-04-09
The install instructions for the USB disk are for Xubuntu and I downloaded the Ubuntu ISO and already burned it. (link [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/) ) Would the instructions still work for ubuntu instead of XUbuntu? Im hoping they will because Im not sure I have another CD laying around.

---

### Post by chewearn on 2007-04-09
If I read the article correctly, it was actually referring to "Ubuntu 6.10 LiveCD".  Don't know why the title says "XUbuntu".  Note though, the uppercase "U"; maybe it is saying it works for both Ubuntu and Xubuntu?

(Disclaimer: :) I can't really say with 100% conviction that it will work, because I haven't tried it myself.)

---

### Post by dfarce on 2007-04-09
Well, The VM worked amazingly. Took about 5 seconds just to extract the file and then ran it from my [internal] harddrive. The problem is that it's a little slow and freezes every once and a while. The USB install........A complete and utter faliure. I'm not sure what I did wrong. It could be a because of a few problems I encountered in the terminal, or it could be just that I used the wrong version, though I HIGHLY doubt it. First is that I had to do a couple of reboots to switch between linux and windows, but what I am thinking now is that I could use the terminal in my ubuntu VM to reedit the partitions on my drive so that I don't have to keep rebooting. Do you think this would work? now for my terminal problems:
I got to the formatting part of the guide. I partitioned the drive with two partitions one 700Mb etc. but whe I got to fomatting, I couldn't figure out what I was supposed to unmount (step 7).  Also, when I went to repartition the drive (step 7.-5.) I got a weird error message. not exactly error more of a message saying that I was doing something to the drive that would make it impossible to read by any DOS application, and that the changes would only be registered after ubuntu had restarted. So I tried un plugging the drive and re hooking it up to try to get ubuntu to recognize the changes I had made. So then I tried unmounting the drive in step 7(final step 7) by typing umount /dev/sdb1 (my drive) and it said it was unmounted. BUT I wasn't sure about it because the tutorial asks you to unmount the partition. So I tried umount /dev/sdb1p1 and it couldn't find the device. So I continued. when I tried to format the drive using mkfs.vfat -F 16 -n USB /dev/sdb1. Here's where I think the problem is, I got a message saying that the drive didn't have enough sectors to format it with fat 16, and if formatted with fat 12 it couldnt be mounted in linux :( so it would try to do an expanded format. I decided I had nothing to lose so I tried extracting the file from windows to the directory to the new partition on the USB drive. OBVIOUSLY my boot didnt work. I just got a message saying that it couldnt boot. So any Ideas? or should  try formatting the drive from my VM and I can get you some accurrate error messages (this is all from memory)?

OMG I cant believe I didnt notice this, I missed the last step, formatting the second half of the drive! anyways can you answer my question about the partitions?

---

### Post by dfarce on 2007-04-09
Aw, I followed the directions to the letter ( and figured out the partitions) and I couldn't boot properly from the drive. I think the problem is that its not a flash drive so is not listed as removable storage. Oh well, Now that I am aquainted with the terminal, I'm going to look for a more complicated live USB install.

---

### Post by chewearn on 2007-04-10
> **dfarce said:**
> First is that I had to do a couple of reboots to switch between linux and windows, but what I am thinking now is that I could use the terminal in my ubuntu VM to reedit the partitions on my drive so that I don't have to keep rebooting. Do you think this would work?  
I'm not sure; I have not tried VM installation.

> I got to the formatting part of the guide. I partitioned the drive with two partitions one 700Mb etc. but whe I got to fomatting, I couldn't figure out what I was supposed to unmount (step 7). Also, when I went to repartition the drive (step 7.-5.) I got a weird error message. not exactly error more of a message saying that I was doing something to the drive that would make it impossible to read by any DOS application, and that the changes would only be registered after ubuntu had restarted. So I tried un plugging the drive and re hooking it up to try to get ubuntu to recognize the changes I had made. So then I tried unmounting the drive in step 7(final step 7) by typing umount /dev/sdb1 (my drive) and it said it was unmounted. BUT I wasn't sure about it because the tutorial asks you to unmount the partition.
I don't see anything wrong here.  In simple terms, when you specify /dev/sdb1, it means your drive's primary partition 1.  /dev/sdb is the entire drive itself; /dev/sdb2 is the second partition.  Actual designation is alightly more complicated if you count extended and logical partitions.

>  So I tried umount /dev/sdb1p1 and it couldn't find the device.
As explained above; sdb1p1 is not a correct way to refer to a partition.

>  when I tried to format the drive using mkfs.vfat -F 16 -n USB /dev/sdb1. Here's where I think the problem is, I got a message saying that the drive didn't have enough sectors to format it with fat 16, and if formatted with fat 12 it couldnt be mounted in linux :( so it would try to do an expanded format.
Unfortunately, I'm as clueless as you are here.  All my formatting is done via Windows, or GParted.

If the command line formatting still gave the strange error message, you can try using GParted.  It should be in the LiveCD Panel Menu.

---

### Post by ubuntukid on 2007-04-10
I once tried to install ubuntu to an external drive, with little success. My experience is that the kernal panicked because the transfer rate on the usb device was just to slow. Ubuntu 6.06 worked fine on an external hd for me, but not 6.10. Since then I've just decided to install Xubuntu on my main hd which dual boots with vista.

---

### Post by dfarce on 2007-04-13
I've been trying a few different things. I really want to have a 15GB FAT32 Partition on my external hard drive for windows downloads. I started using the persistent how to:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
First I tried using a USB flash drive with the casper-rw folder on my external drive and the boot folder on my usb flash drive. And I just got an error saying that the USB key wasnt bootable. Then I tried doing a triple partition on my external. one 750M boot FAT32, one ~14G casper-rw ext2 and one ~15G FAT32. I got the same error when tring to boot. I followed the instructions to the letter. Do you think this might be a problem with the boot record of the hard drive or maybe because I had three partitions instead of two?

---

### Post by dfarce on 2007-04-14
Maybe the problem is that I used syslinux 3.35?

---

### Post by dfarce on 2007-04-15
ITS ALIVE!!! I got it running After using the ubuntu installation rather than windows I managed to get it to work perfectly. Now all I need is to set up my modem to work and I wil be off to a good start.

PS the four in a row game is IMPOSSIBLE to beat on easy!

---

### Post by dfarce on 2007-04-16
I managed to do a really stpid thing. I created a new account, set it default to log in as and made in a non administrator. NOW I CANT CHANGE ANYTHING is there any way to get into an administrator account from a non administrator one? IE maybe a username and password that works in a preconfigured administrator. Unfortunately i did this before I got the internet running DOH!

---


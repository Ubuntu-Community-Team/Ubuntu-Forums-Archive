---
title: "Alternate CD and GRUB install"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by DigitalRanger on 2007-05-05
I was having a look at the Ubuntu Alternate CD because according to release notes one reason to use it rather than Live CD is if you want GRUB installing somewhere other than the MBR. I was hoping to put GRUB at the start of my root partition and use Windows boot manager.

However, I've gone through the alternate CD install on a virtual machine, and at no point did I get an option on where to put GRUB. I even did an experimental set up of installing Win98 on a virtual machine first, then running the Ubuntu Alternate installer, still no GRUB options.

Could someone advise me, please ?

Thanks for reading.

---

### Post by mikewhatever on 2007-05-05
There is a very good guide on how to use the ALT CD [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
I am quoting the following from there (nearly bottom of the page)
> The GRand Unified Bootloader will overwrite your old boot sector in the first sector of your hard disk. This is just to make it point to GRUB in Ubuntu rather than NTLoader  in Windows.
 
I am adding some information in the 'MBR Page'  of this web site for a more detailed explanation of what actually happens here.

If you choose <No> (not to install to MBR), you will be given an opportunity to specify where else you might like GRUB installed..................................GO

---

### Post by DigitalRanger on 2007-05-05
Okay thank you!
I guess that page didn't come when I tried it given I was doing a virtual. As I mentioned, I tried it with Win98, but I guess Ubuntu doesn't detect Win98 or there was a glitch with my virtual set up.

Anyway, thanks for the proof the option exists, if/when I get to installing Ubuntu, I shall take the leap of faith :)

---

### Post by Benoone on 2007-08-13
If you use the the alt cd and want not to install grub in the mbr...

At the start of the install, while setting up the partitions, be sure to set the /root as bootable - It will show a B in the list.

Then at the very end of the install...
A screen will appear and ask you where you want grub.  If you do nothing it will install to the mbr.  Otherwise fill in the blank line with a location.  Be sure you count the partitions and then follow the examples to tell grub exactly where to live.

i.e. (hd0,3) [and use the ( )'s] is the third primary partion on disk 0 (or 1 if you are not geek)

Disks start with zero but partitions start with one?  GeekTalk?

If you don't get it right the first time do a repair and change the location until it works. 

FYI Grub is blind to any fat12 dos partitions on your disk so don't use them in the count.  It also has many other bugs that are undocumented.   I fight with it all the time and try not to use it except in the simple installs..

For the last install I did, my partition# for root was 13 ( and remember that the extended is always counted as partition #4 so the first logical partition will be #5) located in the extended partition.

-----------------------------------------------------------------------------------------------------

Again, I'm re-installing off of that partition #13 and want to use a /boot partition.  So far I've figured out to size it 32 - 200mb and put grub there which is not a problem but...

Do you set the /root as bootable or do you set the /boot as bootable?
[edit] Wherever GRUB will be installed is the partition you must set "bootable" during the partition setup.  If it's /boot then the mbr points to /boot where it finds GRUB which then directs the boot process to  /.  

Thanks in advance

Benoone

---


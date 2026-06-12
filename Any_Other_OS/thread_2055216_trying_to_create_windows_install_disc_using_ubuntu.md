---
title: "trying to create windows install disc using ubuntu"
date: 2012-09-08
forum: Any Other OS
---

### Post by MasterJimmy on 2012-09-08
a friend gave me his Gateway laptop after replacing it. the HDD was shot so i replaced it with a working HDD from an Acer netbook. i know hardware wise its not importrant and the HDD will work fine. my issue is that because of the swap i cant get it to start up. i have the windows 7 .iso and im trying to create a usb installer so i can get the laptop up and running. how do i go about doing this using ubuntu 12.04? im trying to reinstall windows 7 on the laptop so i can have a working webcam. if ubuntu could use the integrated webcam i would probably just install that and be done with it but as we all know linux and cameras dont get along and i really need a working webcam for my various projects like youtube etc.

---

### Post by flipper T on 2012-09-08
so your question is ¨how do i install windows¨ ?

..on a linux forum ?

oh.

---

### Post by cryptotheslow on 2012-09-08
I've not tried it with a Windows iso but give Startup Disk Creator a try (find it via the Dash). I'm not at all sure it will work, but worth a shot.

Would probably be a lot easier if you could get hands on a DVD burner, then you could just use any number of applications to burn the iso to disk (Brasero etc.).

What have you tried to get the camera working?

---

### Post by MasterJimmy on 2012-09-08
pretty much. i wouldnt use winblows at all if it wasnt for the fact i need a working webcam and i dont want to take the chance of installing ubuntu onto the gateway laptop and losing the webcam. i use ubuntu 12.04 for pretty much everything. i just need to make sure i have a working webcam and the gateway has an integrated webcam

---

### Post by MasterJimmy on 2012-09-08
> **cryptotheslow said:**
> I've not tried it with a Windows iso but give Startup Disk Creator a try (find it via the Dash). I'm not at all sure it will work, but worth a shot.

Would probably be a lot easier if you could get hands on a DVD burner, then you could just use any number of applications to burn the iso to disk (Brasero etc.).

What have you tried to get the camera working?
tried starup disc creator. cant get it to select the .iso

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> tried starup disc creator. cant get it to select the .iso
i dont have a dvd burner. the desktop im using is so old it had xp preloaded. havent done anything with the laptop other than install the HDD

---

### Post by wojox on 2012-09-08
Something like:
```
sudo dd if=windows.iso of=/dev/sdb
```
for the if (in file) change the path and the of (out file) change the drive.

Chech for your drive with:
```
sudo fdisk -l
```

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> Something like:
```
sudo dd if=windows.iso of=/dev/sdb
```
i have a new usb disc inserted, i just type that command string into the terminal?

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> Something like:
```
sudo dd if=windows.iso of=/dev/sdb
```
for the if (in file) change the path and the of (out file) change the drive.

Chech for your drive with:
```
sudo fdisk -l
```
im kind of clueless when it comes to alot of terminal stuff. most of the time i never have to use it.

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> im kind of clueless when it comes to alot of terminal stuff. most of the time i never have to use it.
can someone pleae give me a step by step on this one?

---

### Post by uRock on 2012-09-08
> **MasterJimmy said:**
> as we all know linux and cameras dont get along

Really?

Moved to ***Other OS/Distro Talk***

---

### Post by uRock on 2012-09-08
> **MasterJimmy said:**
> can someone pleae give me a step by step on this one?

Open Disk Utility, find your USB Drive on the leftside menu, then find the drive location which I have circled in the screenshot, then enter that into the first command in the above post by **wojox**.

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> Something like:
```
sudo dd if=windows.iso of=/dev/sdb
```
for the if (in file) change the path and the of (out file) change the drive.

Chech for your drive with:
```
sudo fdisk -l
```
i dont know anything about paths and such. mostly i just use ubuntu and never run into any of the issues that need me to use terminal

---

### Post by MasterJimmy on 2012-09-08
> **uRock said:**
> Open Disk Utility, find your USB Drive on the leftside menu, then find the drive location which I have circled in the screenshot, then enter that into the first command in the above post by **wojox**.
ok i get how to get starup creator to put the winblows .iso onto the thumb drive...how do i get it to find the .iso?  i get this message
james@Andriod:~$ sudo dd if=windows.iso of=/dev/sdc1
[sudo] password for james: 
dd: opening `windows.iso': No such file or directory
james@Andriod:~$

---

### Post by uRock on 2012-09-08
> **MasterJimmy said:**
> ok i get how to get starup creator to put the winblows .iso onto the thumb drive...how do i get it to find the .iso?  i get this message
james@Andriod:~$ sudo dd if=windows.iso of=/dev/sdc1
[sudo] password for james: 
dd: opening `windows.iso': No such file or directory
james@Andriod:~$

Where do you have the Windows ISO? What directory, such as Home, Downloads or something like that? I will help you with the change directories command once you answer the above question.

---

### Post by MasterJimmy on 2012-09-08
> **uRock said:**
> Where do you have the Windows ISO? What directory, such as Home, Downloads or something like that? I will help you with the change directories command once you answer the above question.
i have it in downloads

---

### Post by cryptotheslow on 2012-09-08
*sudo dd if=~/Downloads/windows.iso of=/dev/sdc1*

or

*cd Downloads*

then

*sudo dd if=windows.iso of=/dev/sdc1*

---

### Post by uRock on 2012-09-08
^^^ what he said.

---

### Post by MasterJimmy on 2012-09-08
> **cryptotheslow said:**
> *sudo dd if=~/Downloads/windows.iso of=/dev/sdc1*

or

*cd Downloads*

then

*sudo dd if=windows.iso of=/dev/sdc1*
tried that and still not working. even renamed the ISO "windows.iso" as it was "windows 7 home premium 64 bit.iso" before just in case that was why it was not working. moved the .iso to the desktop so maybe it will be easier.

---

### Post by MasterJimmy on 2012-09-08
> **cryptotheslow said:**
> *sudo dd if=~/Downloads/windows.iso of=/dev/sdc1*

or

*cd Downloads*

then

*sudo dd if=windows.iso of=/dev/sdc1*
hold on a sec going to try something

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> hold on a sec going to try something
ok that didnt work. for some reason my downloads folder has gotten some weird association and it wont link correctly, not sure how it happenned. putting the iso back on the desktop.

---

### Post by MasterJimmy on 2012-09-08
> **uRock said:**
> Where do you have the Windows ISO? What directory, such as Home, Downloads or something like that? I will help you with the change directories command once you answer the above question.
long story short somehow my download folder is associated with the desktop and i cant get the path to correct itself. i put the .iso file on the desktop itself now.

---

### Post by uRock on 2012-09-08
Use ```
cd Desktop
```

---

### Post by wojox on 2012-09-08
Ctrl+Alt+T opens a terminal and run this and post it back:
```
sudo fdisk -l
```

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> Ctrl+Alt+T opens a terminal and run this and post it back:
```
sudo fdisk -l
```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d845

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    76031999    38014976   83  Linux
/dev/sda2        76034046    78123007     1044481    5  Extended
/dev/sda5        76034048    78123007     1044480   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       64259       32098+  de  Dell Utility
/dev/sdb2   *       64260    80276804    40106272+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 8103 MB, 8103395328 bytes
250 heads, 62 sectors/track, 1021 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15825499     7912719    c  W95 FAT32 (LBA)
james@Andriod:~$ 
james@Andriod:~$

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d845

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    76031999    38014976   83  Linux
/dev/sda2        76034046    78123007     1044481    5  Extended
/dev/sda5        76034048    78123007     1044480   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       64259       32098+  de  Dell Utility
/dev/sdb2   *       64260    80276804    40106272+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 8103 MB, 8103395328 bytes
250 heads, 62 sectors/track, 1021 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15825499     7912719    c  W95 FAT32 (LBA)
james@Andriod:~$ 
james@Andriod:~$
im not sure what happenned but it looks like it did copy the iso to the disc, but i didnt see that before i relocated the iso and reentered the command string with desktop instead of downloads. it said it copied again and now im not sure if i should reformat the thumb drive and try it again just to make sure i dont have two copies on it and screw up the install somehow

---

### Post by wojox on 2012-09-08
> **MasterJimmy said:**
> im not sure what happenned but it looks like it did copy the iso to the disc, but i didnt see that before i relocated the iso and reentered the command string with desktop instead of downloads. it said it copied again and now im not sure if i should reformat the thumb drive and try it again just to make sure i dont have two copies on it and screw up the install somehow

Yes format and do it again. It probably won't boot since its installed on a partition and not the whole drive. You want to install it at:
```
/dev/sdc
```

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> Yes format and do it again. It probably won't boot since its installed on a partition and not the whole drive. You want to install it at:
```
/dev/sdc
```
it wont let me format. says the device is mounted.

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> it wont let me format. says the device is mounted.
the 8 gb drive is the thuimb drive. the 40 and 41 are my HDD's im just trying to format the 8gb so i can put the iso on it and plug it into the laptop and install windows. plaes help me before i start screaming!!!!

---

### Post by wojox on 2012-09-08
> **MasterJimmy said:**
> the 8 gb drive is the thuimb drive. the 40 and 41 are my HDD's im just trying to format the 8gb so i can put the iso on it and plug it into the laptop and install windows. plaes help me before i start screaming!!!!

i know math thanks. unmount the usb stick.

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> i know math thanks. unmount the usb stick.
ok FINALLY got it to unmount. format it ntfs?

---

### Post by uRock on 2012-09-08
> **MasterJimmy said:**
> ok FINALLY got it to unmount. format it ntfs?

fat32

---

### Post by wojox on 2012-09-08
> **MasterJimmy said:**
> ok FINALLY got it to unmount. format it ntfs?

okay format no partition

---

### Post by MasterJimmy on 2012-09-08
> **uRock said:**
> fat32
ok formatted FAT now. will it being a FAT32 affect the fact im installing a 64 bit os?

---

### Post by uRock on 2012-09-08
> **MasterJimmy said:**
> ok formatted FAT now. will it being a FAT32 affect the fact im installing a 64 bit os?

no

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> ok formatted FAT now. will it being a FAT32 affect the fact im installing a 64 bit os?
ok its formatted FAT32 with no partitions.

---

### Post by wojox on 2012-09-08
> **MasterJimmy said:**
> ok its formatted FAT32 with no partitions.

try the commands again. post back the response. you can copy and paste from the terminal.

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> try the commands again. post back the response. you can copy and paste from the terminal.
james@Andriod:~$ sudo dd if=~/Desktop/windows.iso of=/dev/sdc
[sudo] password for james: 

sudo dd if=~/Desktop/windows.iso of=/dev/sdc1
6585576+0 records in
6585576+0 records out
3371814912 bytes (3.4 GB) copied, 1129.64 s, 3.0 MB/s

---

### Post by wojox on 2012-09-08
> **MasterJimmy said:**
> james@Andriod:~$ sudo dd if=~/Desktop/windows.iso of=/dev/sdc
[sudo] password for james: 

sudo dd if=~/Desktop/windows.iso of=/dev/sdc1
6585576+0 records in
6585576+0 records out
3371814912 bytes (3.4 GB) copied, 1129.64 s, 3.0 MB/s

reboot and cross your fingers. :p 
remember to boot of the usb drive first.

---

### Post by MasterJimmy on 2012-09-08
> **wojox said:**
> reboot and cross your fingers. :p 
remember to boot of the usb drive first.
ok about to plug the usb drive into the laptop and pray. after this it should be a pretty straightforward install. the issue i was having was how to use linux to create the winblows install disc. the concepts from this are very helpful for solving a few other issues i was having. thanks. stand by, will post results here

---

### Post by MasterJimmy on 2012-09-08
> **MasterJimmy said:**
> ok about to plug the usb drive into the laptop and pray. after this it should be a pretty straightforward install. the issue i was having was how to use linux to create the winblows install disc. the concepts from this are very helpful for solving a few other issues i was having. thanks. stand by, will post results here
"this is not a bootable disc. please insert a bootable disc and press any key to try again"

---

### Post by MasterJimmy on 2012-09-08
question: if i install ubuntu onto the laptop can i use the iso file to install winblows onto the laptop?

---

### Post by uRock on 2012-09-09
> **MasterJimmy said:**
> "this is not a bootable disc. please insert a bootable disc and press any key to try again"
You should burn the ISO to a CD/DVD.> **MasterJimmy said:**
> question: if i install ubuntu onto the laptop can i use the iso file to install winblows onto the laptop?

Do you mean you want to partition the HDD using the Windows partitioner? I believe you will have to first reformat the HDD to NTFS using an ubuntu or [gparted]("http://gparted.sourceforge.net/") live image.

---

### Post by cpatrick08 on 2012-09-09
> **MasterJimmy said:**
> "this is not a bootable disc. please insert a bootable disc and press any key to try again"

follow directions from [http://ms-sys.sourceforge.net/]("http://ms-sys.sourceforge.net/") to make the usb bootable

---

### Post by mips on 2012-09-09
People from what I recall you can't simply write a windows iso to usb stick and make it work, this is not linux we are dealing with.


@MasterJimmy,

Here are 3 easy ways (although maybe a bit long winded) to do this:

1. [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) I think this worked for me once but I had to download the older 494 version as mentioned in the article (they provide a link)



2. Do you have access to another PC with windows (XP or 7, XP requires .Net to be installed) on it?

If the answer to the above is 'yes' then,

Format your memory stick to NTFS. FAT32 has a 4GB file size limitation so to be on the safe side I said NTFS but if the image is smaller than 4GB then FAT32 will also be fine.

Next copy the image to the memory stick and then onto the windows pc.

Next download the [Windows 7 USB/DVD Download Tool]("http://images2.store.microsoft.com/prod/clustera/framework/w7udt/1.0/en-us/Windows7-USB-DVD-tool.exe") from [http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool) and install/run it on the windows pc and follow the instaructions on that page.



3. If you don't have access to a windows pc to perform the above then install virtualbox on ubuntu and then install windows 7 in virtualbox from your iso. Once you have windows 7 installed in virtualbox and your USB ports are enable in virtualbox then follow the last step in the above (2) procedure to write the image to your memory stick for installation.


There is also a 4th method but that is even more work.

---

### Post by Cheesemill on 2012-09-09
I just use the WinUSB application:

[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by mips on 2012-09-09
> **Cheesemill said:**
> I just use the WinUSB application:

[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

/insert homer simpson 'duh' sound here.

Now how could I forget about that one, much easier!

---

### Post by MasterJimmy on 2012-09-09
i totally forgot about VB! not sure if i can run windows 7 on this machine...it had XP preloaded but hopefully it can handle a temporary install so i can use the creator tool i found. my goal was to use unubtu only because my friend said Tux couldnt do it. based on what all i read it aint linux that is the isue but my lack of skill so far. going to review the specs and see if i can do a temporary install and go from there but will also try the other hints. thank you for the advice and any other  hints are welcome.

---

### Post by C.S.Cameron on 2012-09-09
To make a Windows 7 installer USB using Ubuntu:
Format the USB NTFS using gparted and set boot flag.
Using Archive Manager, extract the W7 iso to the USB.
Set the USB as first hard drive in the computer bios.

---

### Post by mips on 2012-09-09
> **MasterJimmy said:**
> i totally forgot about VB! not sure if i can run windows 7 on this machine...it had XP preloaded but hopefully it can handle a temporary install so i can use the creator tool i found. my goal was to use unubtu only because my friend said Tux couldnt do it. based on what all i read it aint linux that is the isue but my lack of skill so far. going to review the specs and see if i can do a temporary install and go from there but will also try the other hints. thank you for the advice and any other  hints are welcome.

See post#46 !

---

### Post by MasterJimmy on 2012-09-10
> **Cheesemill said:**
> I just use the WinUSB application:

[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)
DL'd winusb. cant get it to work right. i clicked "install" after setting the target drive etc correctly but it says "mounted read only" in the error report. going to try to use disc utility to format it NTFS and see if that works then try formatting it FAT if that dont work. if THAT doesnt work i will post and ask for advice after i finish throwing my computer against a wall and see if THAT helps.

---

### Post by MasterJimmy on 2012-09-10
think i solved it. did a full basic blank format and unmounted it and now it seems to be working. in the process of copying so keep your fingers crossed.:D

---

### Post by MasterJimmy on 2012-09-10
ALL HAIL THE GREAT AND MIGHTY LORD TUX!!!!!!!!!! thank you everyone for your advice and help. installing win7 onto the laptop now. specific thanks and accolades to the one who suggested winusb. once i get a better laptop, (this one is physically in a slightly dinged up condition due to my friends kid tearing up the keyboard) i will install ubuntu onto it and figure out how to get the webcam working.:p

---

### Post by MasterJimmy on 2012-09-10
i did try gparted but cant get it to work. any advice on this would be welcome so i can expand my knowledge base and skillset. winusb did the job but learning to use gparted is also on my agenda now just for pure knowledge reasons. i cant get it to do pretty much anything and just about every menu item is greyed out and not selectable.

---

### Post by Chaoky on 2012-09-17
Try UNETBootin. Get it and burn it onto the USB from there.

---


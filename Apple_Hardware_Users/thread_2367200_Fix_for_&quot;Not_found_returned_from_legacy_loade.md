---
title: "Fix for &quot;Not found returned from legacy loader&quot;"
date: 2017-07-27
forum: Apple Hardware Users
---

### Post by shantiq on 2017-07-27
*When you get this error trying to install Ubuntu on a Mac [in this case Macbook 2005]*

```
**"Error: Not found returned from legacy loader" **
```   and something about efi
where basically the mac is complaining about not being able to deal with a legacy usb and wanting efi

I have arrived at an interesting workaround cobbled from many sources and 20 hours
of trials....   

&#10122;  To burn [SuperGrub2]("http://www.supergrubdisk.org/super-grub2-disk/") to a usb stick ... 

  [COLOR=#800000][I]This is the crucial difference and rEFInd on its own will not do it 
ALSO  ensure you burn [SuperGrub2]("http://www.supergrubdisk.org/super-grub2-disk/")  using info below[/I][/COLOR] **[COLOR=#800000]*on the mac!*[/COLOR]**

&#10123;  To get your [version of Ubuntu 14.04]("http://old-releases.ubuntu.com/releases/")    Later Versions on my 2005 Macbook did not work; not sure if it depends on age of machines or changes made to the later distro iso
[URL="https://www.lewan.com/blog/2012/02/10/making-a-bootable-usb-stick-on-an-apple-mac-os-x-from-an-iso"]
from[/URL] :

    *First [and not sure if this stage crucial or if one could simply use the iso]*:
    Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
    Convert the .iso file to .img using the convert option of hdiutil:
```
     hdiutil convert -format UDRW -o /path/to/target.img /path/to/source.img   /path/to/target.img /path/to/source.iso
```
    Note: OS X tends to put the .dmg ending on the output file automatically. Rename the file by typing:
```
     mv /path/to/target.img.dmg /path/to/target.img
```
    =======
    
    Run```
 diskutil list
``` to get the current list of devices
    Insert your flash media
    Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
    Run ```
diskutil unmountDisk /dev/diskN
``` (replace N with the disk number from the last command - in the previous example, N would be 2)
    Execute```
 sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m
``` (replace /path/to/downloaded.img with the path where the image file 
    is    located; for example, ./ubuntu.img or ./ubuntu.dmg).
    Note: Using /dev/rdisk instead of /dev/disk may be faster.
    Note: If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
    Note: If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and 
    unmount (don't eject) the drive.
    Run diskutil eject /dev/diskN and remove your flash media when the command completes

&#10124;   install rEFInd on mac


&#10125;  When all this is ready to place both usbs in your mac and fire up computer
[[IMG]https://s22.postimg.org/rnrtbynhp/IMG_2190.jpg[/IMG]]("https://postimg.org/image/rnrtbynhp/")
Pick the three balls option
[[IMG]https://s22.postimg.org/46vczgcj1/IMG_2181.jpg[/IMG]]("https://postimg.org/image/46vczgcj1/")

All from now all will be done through grub and will remain in grub until last stage
First pick this [Detect and show boot methods]
[[IMG]https://s22.postimg.org/8rhjedw8d/IMG_2182.jpg[/IMG]]("https://postimg.org/image/8rhjedw8d/")
leading to this [Operating systems]
[[IMG]https://s22.postimg.org/viqm0sh9p/IMG_2183.jpg[/IMG]]("https://postimg.org/image/viqm0sh9p/")
And scroll down to Install or try Ubuntu  [towards the bottom of list on mine]
When install completed Remove both usb.

&#10126; Once installed when you reload you will now find you are in Grub straightaway so you need to use
**efibootmgr **to find rEFInd again as original greeter ... ie change the booting order
This [URL="https://askubuntu.com/questions/325048/cleaning-up-and-changing-the-efi-boot-order-permanently-using-eifbootmgr"]link 
[/URL]explains all

find out your current boot order ```
sudo efibootmgr -v
```
then it will require something like this to reestablish rEFInd
```
sudo efibootmgr -o  FFFF , 0000 , 0082

```

and then >>
[[IMG]https://s22.postimg.org/46vczgcj1/IMG_2181.jpg[/IMG]]("https://postimg.org/image/46vczgcj1/")   greeted by the rEFInd greeter again



All done!


ADDED NOTE:[summer 2018]

been horsing around for a week  trying to dual boot Slackware and Snow Leopard Mac but got nowhere fast and to do this had to knock off my existing Buntu partition; not always a plain sailing endeavour to put it mildly...
Anyway point of this interjection is that using Bodhi Linux to get in seems like a good plan as they have a good UEFI way in it seems and then to fit in the Desktop E of your choice mine LXDE as seen below in snaps  ....    would still like my slackware added too or replacing Bodhi but hey ;    will have to learn much more :]

[[IMG]https://s8.postimg.cc/5cdb5b34h/IMG_4607.jpg[/IMG]]("https://postimg.cc/image/5cdb5b34h/")[[IMG]https://s8.postimg.cc/qysbmdjpd/IMG_4605.jpg[/IMG]]("https://postimg.cc/image/qysbmdjpd/")[[IMG]https://s8.postimg.cc/9y9fdor8h/IMG_4606.jpg[/IMG]]("https://postimg.cc/image/9y9fdor8h/")

---

### Post by lotte67890 on 2018-01-29
Thanks a lot, your thread is very helpful! but I´m struggling with

Sorry, but we are booted via UEFI and can not load this OS.
Please try booting SG2D via BIOS Compatibility Mode.
Press escape....

And I have no clue how you bypass this. I´m using a MacBook 2,1 (looking similar to yours on the images)
I suggest I need a grub.cfg file but I´ve even no idea how to put this on the USB STick since I can not mount...

Thanks a lot!

L

---

### Post by shantiq on 2018-01-29
Hi Lotte just checking you have rEFInd installed on the macbook and you have supergrub2 going ?
If you do try the process a few times ; sometimes it clicks in other times not so well ....    sorry if it seems simplistic but this is what i experienced doing this ...   try again a few times would be my advice ...    make sure all the steps were taken
shan

---


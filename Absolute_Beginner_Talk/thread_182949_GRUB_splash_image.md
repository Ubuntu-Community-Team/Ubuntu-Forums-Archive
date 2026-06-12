---
title: "GRUB splash image"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-05-27
I want a splash image for GRUB , the ubuntu guide sais:
> 1.Read General Notes 
2.e.g. Assumed that hd0,1 is the location of Ubuntu boot partition
3.wget -c [http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz](http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz)
chmod 644 ubuntu.xpm.gz
sudo mkdir /boot/grub/images
sudo cp ubuntu.xpm.gz /boot/grub/images/
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
4.Find this section 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
...
I am not sure where my boot partition is this is my fdisk:
>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2501    20089251    7  HPFS/NTFS
/dev/hda2            2502        5051    20482875    f  W95 Ext'd (LBA)
/dev/hda3            5052        9306    34178287+  83  Linux
/dev/hda4            9307        9610     2441880   82  Linux swap / Solaris
/dev/hda5            2502        5051    20482843+   b  W95 FAT32
 i'm dual booting with Win2003 and I dont understand what "Assumed that hd0,1 is the location of Ubuntu boot partition" means here and how it should effect my what I need to do...

---

### Post by Herman on 2006-05-27
> i'm dual booting with Win2003 and I dont understand what "Assumed that hd0,1 is the location of Ubuntu boot partition" means here and how it should effect my what I need to do...  All due respect to the person who wrote the instructions, it is tricky to write instructions that will be good for everyone. Some have different setups and others are beginners. If you give instructions that will suit every set-up it's confusing for beginners. If you make simple instructions for beginners, they might not work for every set-up.
Those instructions seem to be anticipating that the user may have a seperate boot partition, most of us don't. We just have a /boot directory in our operating system partition. You can probably skip some of those steps. I just put my grubsplash images in my /boot directory and they work fine there. I think you can get away with deviating from the instructions quite a lot if you want. I have never needed to chmod any of my grubsplashes. It's not really that complictated for most people. After you download (or make your own) grub splashimage, just try these instead:
```
sudo cp ubuntu.xpm.gz /boot
``` That should be all you need to do, then 
>  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst I just make a space between the lines '#hiddenmenu and #prettycolors and type in a line similar to:
>     #hiddenmenu
    
   splashimage=(hd0,1)/boot/ubuntus.xpm.gz
   
   #Pretty colours
   #color cyan/blue white/blueThat's what works for me. I hope that makes it easier for you, and I think it's great to have nice grubsplash images in Ubuntu. Good on you!  Regards, Herman

---

### Post by seshomaru samma on 2006-05-27
thanks.
must it be a xpm.gz file?
all the splashscreen that i downloaded are png.

---

### Post by Herman on 2006-05-27
>  must it be a xpm.gz file?
all the splashscreen that i downloaded are png. 
[http://ruslug.rutgers.edu/%7Emcgrof/grub-images/#0]("http://ruslug.rutgers.edu/%7Emcgrof/grub-images/#0")

The Splashimage HowTo I followed is linked above. According to the information I can find there it does not have to be a .gz (compressed) image, but the author says Grub can load compressed files quicker than if they weren't compressed, so it is probably be a small advantage to do so. Instructions for doing that are in the above link.

I have not tried using images in grub that are not .xpm, but I know that LiLo, the other Linux bootloader, has ordinary bitmap splashimages.
I think the best way to find out for sure is to experiment.
The best way to change your images from .png if you need to is to use GIMP image editor in Ubuntu. You only have to open the image with GIMP and click 'File' 'Save Image As', and type in the file extension you want (.xpm) in the box after the name for your image.

The author of the website linked above says the splashimage must be made with only 14 colors, and I have found out that that seems to be true for my computers. I do not know for sure  but I think it is possible that some very new BIOSs might support more colors than that.  

  I have not experimented to find out for sure if the images can contian more pixels than 640 x 480, but LiLo splashimages are also 640 x 480 pixels, so I presume that might be a BIOS limitation also. Some BIOSs may be able to do more if people try, but 640 x 480 is probably a safe image size that will work for almost everyone.

Regards Herman.

---

### Post by seshomaru samma on 2006-05-27
i made an .xpm file but the splash screen didn't come out as expected - it was just a bunch of colored pixels. maybe it wasn't in 14 colors . can you tell me how to make it into 14 colors?
also how do i gzip a file?

---

### Post by catlett on 2006-05-27
This is from Herman's link. It appears to cover everything.
> 1.3.1 Only 14 colors... How do I do that?

To get GIMP to use only a 14 color palette, right click on your file and press ALT+I and put 14 where it says "Generate Optimal Palette:" on the top of the menu. If ALT+I doesn't get you there then right click on the image and go to:

Image-->Mode-->Indexed

Specify you want 14 colors and then if you want (*recommended*) select NO DITHERING. This will tell the gimp not to try to guess colors in between areas. It is also possible that you tell them gimp what colors you want in your 14-color pallete, I actually had to do this for one of my images and I replaced a dark color for a light one. :) The GIMP ROCKS! 

---

### Post by Herman on 2006-05-28
Yes, Catlet is correct, and also, to answer your other question,> also how do i gzip a file?You can use a command similar to the one shown below:    ```
~$ gzip Ubuntusplash.xpm
``` That should gzip any file providing it is located in your /home/username directory (not inside another folder), and of course, you need to replace the name of the file 'Ubuntusplash' with whatever name you gave your own image file.
You should be able to make your own splashimages that way from a photograph or an image file downloaded from the internet, a screencap, or one you make yourself with GIMP. It's well worth doing so in my opinion. 
You can have a number of grubsplashes in your /boot directory too, and just 'comment out' all but one in your menu.lst

---

### Post by seshomaru samma on 2006-05-28
I managed to get it to work for an image I created myself but not for a grub splash screen I downloaded from the Gnome website.
(btw this :
```
wget -c http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz
```
got me a 404 error)
Thank you for your help

---

### Post by catlett on 2006-05-28
error 404 means the website server was not found. Check to make sure the url is right and if it is then wait and try again it may be down or busy

---


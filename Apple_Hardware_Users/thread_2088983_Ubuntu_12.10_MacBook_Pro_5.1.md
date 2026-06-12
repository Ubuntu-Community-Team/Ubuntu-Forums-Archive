---
title: "Ubuntu 12.10 MacBook Pro 5.1"
date: 2012-11-27
forum: Apple Hardware Users
---

### Post by Andrewiski on 2012-11-27
First off I am a new to Ubuntu with limited Linux experince but am a master in windows and I am a software engineer by trade. I want to learn Ubuntu like I know windows so decided to install it for an Embedded project I am working on.
 
I am triple booting Mac OSX, Windows 7 and Ubuntu 12.10. I Installed refid before ubuntu (OS X and Windows 7 were already installed). I had to use the nomodeset F6 option from the Mac Version of the x64 Ubuntu 12.10 to avoid the black screen but was able to install Ubuntu. Now when I choose Linux in refid the grub menu comes up, but I have to add nomodeset to not get the black screen again. Looking at System, Software Sorces, Additional Drivers I am using the 9600GTM card which acts as small room heater, so would like to use the 9400. (Have the same issue in Windows 7 but thats another story)
 
How do I make Ubuntu use the 9400 video card and disable the 9600 video card?
 
What video driver should I be using for the 9400? How do I download and install it.
 
I was going to try this ([https://help.ubuntu.com/community/MacBookPro5-3/Precise#Video_.26_Effects_.28Compiz.29](https://help.ubuntu.com/community/MacBookPro5-3/Precise#Video_.26_Effects_.28Compiz.29)) but I don't have an etc/X11/xorg.conf file to edit so I assume I am running a diferent video card driver or somthing.
 
I found this page as well but it is for Ubuntu 11 so not sure how much of it applies.
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty)
 
I had to use the wired network connection to connect to the internet but I think I have found enough post online to fix the wireless driver.
 
Any help you can give would be appriciated.
 
Thanks
 
Andy

---

### Post by Andrewiski on 2012-12-01
I still haven't made any progress on booting with only the 9400M on my Macbok Pro 5.1. No mater what I seem to do "lspci | grep VGA" always shows only the 9600M GT.
 
I am running Ubuntu 12.10 x64 was instaled using the Mac Specific alternitive CD.
 
I have read so many posts and tried so many things but still no luck.
 
In refit terminal if I do a pci -b I see two vga devices listed although they don't specficaly say they are nvidia.  I have tried booting "Engery Saving Mode" and with out and then warm booting into ubuntu but still only 9600M GT is listed. 
 
When I use gpupwr the 9600M GT seems to power down but becasue the 9400M was never powered up I get a blank screen.  I have tried placing the outb  commands in grub/custom.cfg which basicaly does the same thing as gpupwr and the same result of a black screen result a lot sooner .  I can boot with or without nomodeset.  I have tried both the lastest open source and propritary drivers from nvidia-current, installed using additional drivers but when I run "sudo nvidia-settings" i get a "You do not appear to be running hte NVIDIA X Driver"  but I am not sure why that is. Shouldn't the Add Addtional Drivers make the driver load after the next reboot. 
 
Any experts out there that can point me in the right direction? Any one with a MacBook Pro 5.1 have ubuntu running with out cooking the desk? (ie running 9400M video card only)

---

### Post by 2F4U on 2012-12-02
I don't know if this works in 12.10, but here is a post about 11.10 and 12.04:

[http://askubuntu.com/questions/73332/how-to-deactivate-nvidia-9600m-gt-on-a-macbookpro-5-1-5-2-5-3](http://askubuntu.com/questions/73332/how-to-deactivate-nvidia-9600m-gt-on-a-macbookpro-5-1-5-2-5-3)

---

### Post by alexmurray on 2012-12-02
@Andrewiski - you need to boot in EFI mode, at the moment you are booting in BIOS mode where the 9400M is automatically shutdown by the Apple BIOS. The following should give some more info:

[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Andrewiski on 2012-12-02
> **alexmurray said:**
> @Andrewiski - you need to boot in EFI mode, at the moment you are booting in BIOS mode where the 9400M is automatically shutdown by the Apple BIOS. The following should give some more info:

[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You are absolutly correct. I ran
```
 [ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"
```

and got "Legacy Mode" I thought installing refit before doing the Ubuntu install would casue the cd to EFI boot and Ubuntu to get installed in UEFI mode. I also thought that the lack of the keyboard and circle logo during boot after install and the fact that refit is showing the Penguin Icon ment I was in EFI mode. 

Where did I go wrong during the install from the Ubuntu Live DVD? 

Well here is where I went wrong for those that follow in my path. 

I booted using the Ubuntu 12.10 Alternitive Mac x64 CD which doesn't have EFI boot support. How can you tell you ask? Boot Macbok pro by holding alt (option) key and you will get the boot menu (EFI Boot & Windows with Hard Drive Logos in mycase as I have OS X and Windows 7 with refit EFI Manger install) . Insert Alternative CD and all you will see added to boot menu is Windows with CDROM logo. Eject Alternative CD and insert Ubuntu 12.10 x64 desktop cd and you will get new CDrom Icons labeled Windows and a EFI boot. This is where the catch 22 comes into play. If I boot from the non Mac alternitive cd Ubuntu crashes with 
```
b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
```
but I can press e during grub boot and add ```
outb 0x0750 0
``` 
and have the 9600M GT power down and not get the black screen as the cd boots while until the Brodcom driver crashes. So with the help above we now have both video cards avalible to grub which is what I have been after all along. No just have to figure out how to install ubuntu in UEFI or to convert existing bios install to EUFI install

So the question is how do I boot in UEFI mode using the alternitive Mac cd so I don't crash on the broadcom driverload. 

For those of you booting from the alternative cd in bios mode and getting a black screen you have to press a key when you see the keyboard and circle icon then press F6 select "nomodeset" press enter, press esc, press enter to boot.

So I installed in Bios mode now so lets try to convert grub to UEFI mode.

I followed instructions here. [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
but now when I boot Linux I boot in to grub rescue with error **/boot/grub/i386-pc/normal.mod **looking at the filesystem I see now it should be **/boot/grub/x86_64-efi/normol.mod **just have to figure out how to make that change.

Still no love for the Macbook Pro 5,1 but still a couple more hours before bed time so maybe I will figure it out yet. :(

---

### Post by alexmurray on 2012-12-02
Make sure you're **not** using the +mac iso - as you said this doesn't have the EFI stuff on it - instead you want something like this - [http://mirror.internode.on.net/pub/ubuntu/releases/12.10/ubuntu-12.10-desktop-amd64.iso](http://mirror.internode.on.net/pub/ubuntu/releases/12.10/ubuntu-12.10-desktop-amd64.iso)

Also (when I ran Ubuntu) I [always had to boot]("https://bugs.freedesktop.org/show_bug.cgi?id=27501") using nouveau.noaccel=1 - so perhaps try that - but once you get the nvidia binary driver installed it was fine.

Also you'll probably need the bcm-wl driver over the b43 and you may be able to blacklist this on boot to make sure it doesn't cause a crash - although the missing firmware shouldn't cause it to crash so I suggest using noaccel should avoid this - or you may need a full nomodeset instead.

---

### Post by Andrewiski on 2012-12-03
Seems silly that Uduntu Mac ALternitive CD doesn't offer the EFI boot. Why would they exclude it from that CD?

---

### Post by alexmurray on 2012-12-03
See [this bug report]("https://bugs.launchpad.net/efibootmgr/+bug/774089"), in particular [comment 125]("https://bugs.launchpad.net/efibootmgr/+bug/774089/comments/125") where Colin Watson discusses explicitly disabling EFI for Intel Macs by default. Basically *some* models have errors when doing this, so it was disabled for all.

---

### Post by Andrewiski on 2012-12-03
Frustrating!  I can't boot using standard Ubuntu 12.10 cd in efi mode. If I use ```
nouveau.noaccel=1 b43.blacklist=yes
``` as grub boot I hang at ```
Magic Number: 8:204:495
``` but no b43 error and no black screen.
 
I assume the reason my boot repair didn't work is becasue I booted from cd in Bios mode and even though I told it to do the Seperate EFI option but it only half did it.
 
Also I followed instruction on [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
 
and at grub rescue prompt I typed 
```
insmod (hd0,1)/usr/lib/grub/x86_64-efi/normal.mod 
```
 
but I got ```
 invalid arch independent elf magic
```.
 
I am in a loop and can't seem to get out of it every effort to fix one issue casues to more.  
 
Is there a way to USB boot in UEFI mode after patching the usb stick with b43 drivers and nvidia drivers? Hopefully the process isn't a 3 day event.
 
Thanks for the replies.

---

### Post by alexmurray on 2012-12-04
Sorry @Andrewski I'm all out of ideas - I run Fedora now and the last version of Ubuntu I had on my MBP5,1 was 12.04 - perhaps try that instead using the non -mac iso and it should work with nouveau.noaccel=1 - I never had any trouble with b43 and instead just used to use the bcmwl driver.

---

### Post by Andrewiski on 2012-12-04
Thanks for the reply. Were you running the x64 or 32 bit version of ubuntu.

---

### Post by Andrewiski on 2012-12-04
Tried Ubuntu 12.04 x64 ended up at the same b43 firmware missing panic as with 12.10.
 
So lame.. Why make an installer panic if it can't load the network drivers, just continue to boot and allow the user to fix it later.  Heck even Microsoft installers at least installs the OS and lists unknown devices.
 
Tried b43.blacklist=yes but then I get a panic with yes invalid for b43.blacklist error.
 
So how hard was it to install Fedora on your Mac Book Pro 5,1?
 
Andy

---

### Post by peezee13 on 2012-12-05
Had the same problem when trying to install Live Ubuntu (can't remember which version, 12.10 I think) on my Powerbook G4, had to switch to a different version in the end. Ridiculous.

The fact that it stops installing (or worse yet, hangs/freezes) for not finding a specific driver for a piece of hardware which is not critical to the normal basic functioning of Linux, is indeed wrong.

The fact that each version of Ubuntu have their own specific behaviour wrt to installation is even more troublesome I think (but being a Linux noob, what do I know ? ^^).

Having said that, when you consider the enormous amount of effort the Linux developers community have consented over the years to offer an OS for free - even incomplete and with its own flaws (but which OS doesn't have any ?), that continues to support even old hardware and obsoleted processors...

---

### Post by trogdor1138 on 2012-12-05
> **Andrewiski said:**
> Is there a way to USB boot in UEFI mode after patching the usb stick with b43 drivers and nvidia drivers? Hopefully the process isn't a 3 day event.
 
Thanks for the replies.

Surprised no one else has mentioned this, but I would recommend checking out Rod Smith's site: [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

He's the one who forked rEFIt to create rEFInd. The above link details his process in installing Ubuntu in BIOS emulation and then switching to EFI mode. Basically, you end up installing Ubuntu in the BIOS mode, set up all of your drivers and hardware, then switch. I've found that most information around somehow bases off of his site.

I just completed an install of 12.10 on a MBP 8,2, and it was quite a process. However, I am able to boot the installer directly in EFI mode, which it sounds like yours is refusing to do. I know it's frustrating, but I think it's worth it to stick with it for the experience benefit alone.

---

### Post by Andrewiski on 2012-12-09
Thanks for the link to [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html) I had tried using refitnd but hadn't studied hsi page in depth.  
 
I kept trying differnt refitnd.conf setting in my Mac partition EFI directory but couldn't get it to work. Out of desperation I mounted the EFI partition and copied the ubuntu directory to the Mac Partition EFI folder same spot as refited folder.  Wouldn't you know no more Grub rescue errors it just booted.
 
I have tried so many things at this point I am not 100% sure if that was all it was or a combination of changes that made it work.   
 
I have another hard drive here that I will reload Mac OS X on then install ubuntu to walk through the steps to get it back up and running.
 
I belive the ubuntu folder on the EFI partition was created using boot rescue but I do not know that for sure. I also had a grub partiiton with an grub.efi in it as well but that may have come from my attemps to manual build grub. Not sure which put what where.
 
If I get a few minutes I will try to reinstall from scratch so those who follow in my foot steps will have a guide.

---

### Post by Andrewiski on 2012-12-16
[COLOR=black][FONT=Tahoma]Here is my How to Install Ubuntu 12.10 x64 on a Mac Book Pro 5,1 (5.1) then fix it so it boots in EFI mode so the 9600M GT video card can be powered down and  the 9400M video card used instead.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]I got most of my information from this website ([[COLOR=#0000ff]http://www.rodsbooks.com/ubuntu-efi/index.html[/COLOR]]("http://www.rodsbooks.com/ubuntu-efi/index.html")) but had to make some minor changes to get it to work. I suspect it was because the author had a slightly newer MacBook Pro that had true EFI 2.0 boot where as my Mac Book 5,1 does not.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Step 1. Boot Mac OSX and install eEFInd ([[COLOR=#0000ff]http://www.rodsbooks.com/ubuntu-efi/index.html[/COLOR]]("http://www.rodsbooks.com/ubuntu-efi/index.html"))[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]This is done by running the install script “./install”  .  This copies the files to the mac partitions/EFI directory.  Note this is **not** the EFI Partition /EFI directory but **is** the Mac OS X partition /EFI directory. On my Mac 5.1 the firmware will only boot EFI files from the MAC Partition EFI folder, I believe this is different on new Mac’s that support true EFI 2.0 booting where the 5.1 does not as it’s a EFI 1.1 boot. Anyways its important to install rEFInd using “./install.sh” and not “./install.sh esp” as that will use the EFI partition and rEFInd will not be loaded on the MacBook 5,1 because its not a true EFI 2.0 boot[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Reboot computer twice if you don’t get the rEFInd boot prompt, not sure why but multiple people stated that you have to boot twice to get it come up after its install, I never experienced this but thought I should pass along the info.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Step 2.  You need to make room on your hard drive for ubuntu. I already had Windows 7 installed so I shrunk the Windows 7 Bootcamp partition to make room. If you don’t have windows 7 installed you can use the OS X Disk Utility to resize your mac or bootcamp partition to make room. [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Step 3. Download the Ubuntu 12.10 x64 Mac Specific Alternative ISO and burn the image to a DVD, be sure to burn the image to the DVD not just the single file else it won't be bootable.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Reboot MacBook and hold option (ALT) key, you should get a “EFI Boot” Icon and then after a couple seconds you will get the “Windows” with a CDROM icon displayed to allow the boot of the Ubuntu 12.10 install CD.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]You will need a wired connection later to fix the video and wireless drivers so now is a good time to plug in the Ethernet card.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Click Windows with CDROM icon and wait for little white circle with Keyboard to appear at the bottom of the screen and press a key to allow changing the boot options.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Choose your Language, then click F6, using the down arrow select "nomodeset" press enter so the x appears, press the “ESC” key to close this menu being sue that the x is still selected on “nomodeset”, [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Press Enter to boot "try Ubuntu without Installing" with the “nomodeset” options selected. The Macbook 5,1 should boot into Ubuntu 12.10 Live CD. If not try a clean reboot meaning power off then power on so we know the 9600GT is the active card. If you boot without "nomodeset" you will get a blank screen as the default video drivers crashes with the 9600G MT. Note that during the live CD boot you will get a black screen for up to a minute before Ubuntu loads the desktop.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Now that the Ubuntu Live DVD has booted you can double click the “Install Ubuntu 12.10” Icon from the Desktop.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]I choose to Download Updates and Install Third Party Software but you will need a wired connection before these options will be available as the wireless card drivers won’t be enabled yet. [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]When Prompted for "Installation Type" pick "something else". [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]This will open a tool that shows the partitions.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]On my Partitcular setup I have a EFI, HFS+ OS X , NTFS BootCamp ntfs, And then 75 GB of free space that I freed up by shrinking my Windows 7 Partition. There are multiple tools out there for resizing including Disk Utility built into OS X. Be sure to back up your data first in case something goes wrong.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Select the FreeSpace and click the + icon to create a new partition from the list, select Logical for the Type and use as “ext4” and mount point is set to “/”, I made this one 40GB in my case. [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]The new partition should be added to the list and the freespace will have shrunk in size.  **Write Down the Partition Device for your “/” partition we will need it later when we create or EFI bootloader. Ie “/dev/sda4”**[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Select FreeSpace again and click the + icon to create another new partition from the list and make sure its type is ext4 and mount point is set to /home, I made this one 20GB in my case. [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]The new partition should be added to the list and the freespace will have shrunk in size.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Select FreeSpace again and click the + icon to create another new partition from the list and make sure its type is swap, I made this one 15GB in my case, but should be at least 2 times the amount of ram your mac has.  Click Install, if you don’t already have a Bios boot partition, I didn’t, you will get an error saying that you need a separate Reserved for Bios Boot Partition, We are using refind as our bootloader and its already installed on our OSX partition, rEFInd will find the ubuntu boot files and add an icon for us so we don’t need the Bios Boot partition so we can ignore this warning and click continue.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Once the Ubuntu install starts you will need to pick your time zone and pick your keyboard English (US) - English (Macintosh) for me.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Set your computer name, username, and password. Be sure to remember your username and password in case you have to boot into single mode later.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Now you have to wait for the install to finish.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Once you have rebooted you should see the rEFInd boot prompt and have a new Penguin Icon that can be used to boot Ubuntu in BIOS. At this point we haven’t fixed our video card issues and we still need to boot with nomodeset options but we set this option differently after we have installed ubuntu.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[SIZE=3][FONT=Calibri]Step 4 Boot Ubuntu in Bios Mode and Make Ubuntu Boot in EFi Mode.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]In rEFInd  you should see a new Linux Penguin icon, You can click this icon to boot Ubuntu but you will need to press e as soon as you get the grub prompt as we don’t have the correct video drivers yet and without adding nomodeset we will get a black or scrambled screen as the default nouveau driver will crash with the 9600M GT.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]So we Click the Penguin and get a text based GNU Grub version 2.00 menu,now we need to press “e” on the keyboard to modify the boot entry and add “nomodeset”.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]After pressing e you will have a screen with a bunch of text. Find the text “quite splash” and add after it “ nomodeset”  then press f10 to boot with this new menu entry.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]At the Desktop press Control + Option + T to open a terminal windows.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Type sudo apt-get purge grub-pc grub-pc-bin[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]You will see an older style GUI screen that asks are you sure you want to remove grub, be sure to select yes.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]In Terminal Type[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]sudo mkdir /boot/efi[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]sudo apt-get install grub-efi-amd64[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck **/dev/sda4   (Note this is the ubuntu “/” partition Device Name we wrote down up above).**[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]--This may give some errors about missing variable just ignore its because we are Bios booted and installing EFI grub but what this will do is create a EFI boot file for gub in our /boot/efi/EFI/ubuntu folder that we can then copy to the OS X /EFI folder to allow us to EFI boot ubuntu.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]sudo update-grub[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]We have two options at this point we can reboot into mac OSX and install fuse so we can read the ubuntu partitions in OS X and do the copy all in OS X between the partitions or we can copy the folder to a usb memory tick and use that to do the copy in OS X. [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]The USB Option is simpler but if you don’t have a usb stick handy the other option works just as well.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]To use the USB Option [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Open up your home directory and under computer navigate to File System, boot, efi, EFI, right click on the ubuntu folder and select copy[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Open the USB memory Stick and paste this folder to the Memory Stick.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Reboot into Mac OS X, Copy the ubuntu folder from the USB memory strick to your mac hard drives /EFI folder.  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]To use The Fuse in Mac OS X[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Boot into Mac OS X, if you already have installed a version of fuse you should see your unix partitions listed in finder if not you need to install fuse or macfuse to see the Ubuntu Partitions. Which of them you install depends on what version of OS X you are running.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]FUSE ([/SIZE][/FONT][[FONT=Calibri][SIZE=3][COLOR=#0000ff]http://osxfuse.github.com/[/COLOR][/SIZE][/FONT]]("http://osxfuse.github.com/")[FONT=Calibri][SIZE=3]) or for older OS X versions MacFuse ([/SIZE][/FONT][[FONT=Calibri][SIZE=3][COLOR=#0000ff]http://code.google.com/p/macfuse/[/COLOR][/SIZE][/FONT]]("http://code.google.com/p/macfuse/")[SIZE=3][FONT=Calibri] )[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Once you have fuse installed you can open a Terminal windows in OS X and type “diskutil list” to see a list of partitions.  We are looking for our “/” disk partition we created earlier, you should be able to tell by its size. In my case it was listed as disk0s4[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]So to manually mount the partition we need to run these commands in an OS X Terminal[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]sudo mkdir /Volumes/Ubuntu[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]sudo mount –t fuse-ext2 /dev/disk0s4 /Volumes/Ubuntu[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Now in finder you should see your ubuntu partition.  We need to copy /boot/efi/EFI/ubuntu folder to our mac partitions /EFI folder. After were are done our /EFI folder will have a /refind and /ubuntu directory in it and this will add a new ubuntu icon to rEFInd so we can boot ubuntu in efi mode.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Now we can reboot the computer and EFI boot into Ubuntu using the new Orange Circle Ubuntu Icon (not the Penguin), keep in mind we still haven’t fixed our video problem so we are still going to need to press e at the grub menu and add nomodeset  behind “quite splash” and this time we will boot into terminal single mode only because the default nouveau  video card driver will crash when it detects both video adapters.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]To fix the Video card driver issue we need to login using the username and password we created during the install.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Also be sure at this point you still have a pluged in a wired connection because we need to download the latest version of the nvidia drivers from the internet.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]We have to download the linux-source files as there appears to be a bug in nvidia-current-updates where it will install but show the message “module build for currently running kernel skipped because source not found” so the kernel never gets patched and the driver never loads.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]sudo apt-get install linux-source[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]sudo apt-get install linux-headers-generic[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]sudo apt-get install linux-headers-3.5.0-17-generic[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]sudo apt-get install nvidia-current-updates[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]type “sudo reboot”   to restart the computer.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Now when we boot using the rEFInd Ubuntu logo we will see the ubuntu logo and then a quick flash of the nvidia logo.  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]We can make sure we are running the correct driver and both video cards are present by pressing Control + Option + T to launch terminal and typing “nvidia-settings”  we should see both video cards.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]You can power down the 9600M GT using a couple of applications. Google gpupwr to find the source code another MacBook Pro 5,1 user created. You can alos add outb commands to the grub menu to power down the adapter. There is also a project called Bumblebee out there that is geared for newer MacBooks, I was not able to get it to work correctly but I am not sure I installed it with the correct nvidia drivers.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Hope this saved someone all the hours it took me of reinstalling over and over trying to make since of the madness that was the install of Ubuntu 12.10 on a Macbook Pro 5,1 [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Let hope the next version of Ubuntu is a little more along the way of an automated Install on the Mac Books.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Thanks[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Andy[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]

---

### Post by fhjlx on 2013-01-15
@Andrewiski: You are a savior sent from above :popcorn:

I've been trying to install 12.10 on my 5,3 macbook pro which should have identical hardware as yours but a smaller screen. Hopefully your approach will finally produce results.

---

### Post by Andrewiski on 2013-01-16
Hope it works out for you!  You will get a black screen for 15 seconds or so even with the correct nvidia drivers and efi boot so be sure to wait at least that long as I didn't the first time through.
 
Good Luck, Please post your results.
 
Andy

---

### Post by nickthecook on 2013-01-18
I've been trying to do this since I got the MBP 3 or 4 years ago. I have been unsuccessful on every attempt until I found this thread.

I've now got battery life in linux that is comparable to that in OS X.

Thank you.

---

### Post by Andrewiski on 2013-01-18
Glad it worked out for you.
 
If only we could get Windows 7 to EFI boot we would be in business.  I have tried multiple different things but the Windows 7 EFI bootloader always crashes. I was able to get Windows 8 to efi boot on a 10,2 Mac Book pro for a friend. I havn't tried to get Windows 8 to efi boot on my Macbook 5,1 yet, so not sure if it will work or not. Its on my todo list. Just think Windows on your Mac Book Pro that will run on battery longer then 60 minutes and not melt the tray table on the airplane. 
 
Andy

---

### Post by grybba on 2013-01-24
Thank you for a great guide. 

Unfortunately I run into an issue at the very end. I've Macbook Pro 5.1, so I expected it to be smooth sailing. I've got to the very end but I cannot get the X's functional with nvidia drivers. The plymouth is crashing (known bug when using nvidia drivers) and I get text-mode only. I can startx (nvidia log flash), but all I get is a wallpaper with no menu bars. Any ideas?

Thanks

---

### Post by jgnome on 2013-03-02
First of all I want to say thanks for making this guide, as I too have been trying to get my 9400 working on other operating systems since the day I bought this laptop (MBP 5.1) over 4 years ago.

I followed all the steps and I'm having the same problem as grybba.  Ubuntu successfully installed and I can see it in rEFInd.  However, when I try to boot it, it defaults into text-only mode.  Adding nomodeset doesn't help at this point, it still defaults into text-only mode.  And if I try to use the recovery mode and start with failsafe graphics, it doesn't start at all.

After some frustration and re-installing Ubuntu, I tried installing all the nvidia drivers *before* converting Ubuntu to EFI boot.  I updated every package, and activated nvidia-current-updates and the Broadcom wireless driver.  Still got the text-only boot.

When I type "startx" I get the following message:
Fatal server error:
no screens found

Here is the log file from startx:
```

[   137.888] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   137.888] X Protocol Version 11, Revision 0
[   137.888] Build Operating System: Linux 2.6.42-34-generic x86_64 Ubuntu
[   137.888] Current Operating System: Linux vcm-MacBookPro 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64
[   137.888] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-38-generic root=UUID=aa90c13d-2d84-4c56-baeb-484712ecca6f ro quiet splash nomodeset vt.handoff=7
[   137.888] Build Date: 17 January 2013  06:14:10AM
[   137.888] xorg-server 2:1.11.4-0ubuntu10.11 (For technical support please see http://www.ubuntu.com/support) 
[   137.889] Current version of pixman: 0.24.4
[   137.889]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   137.889] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   137.889] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  2 22:48:17 2013
[   137.889] (==) Using config file: "/etc/X11/xorg.conf"
[   137.889] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   137.890] (==) No Layout section.  Using the first Screen section.
[   137.890] (==) No screen section available. Using defaults.
[   137.890] (**) |-->Screen "Default Screen Section" (0)
[   137.890] (**) |   |-->Monitor "<default monitor>"
[   137.890] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   137.890] (**) |   |-->Device "Default Device"
[   137.890] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   137.890] (==) Automatically adding devices
[   137.890] (==) Automatically enabling devices
[   137.890] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   137.890]     Entry deleted from font path.
[   137.890] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   137.890]     Entry deleted from font path.
[   137.890] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   137.890]     Entry deleted from font path.
[   137.890] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   137.890]     Entry deleted from font path.
[   137.890] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   137.890]     Entry deleted from font path.
[   137.890] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   137.890]     Entry deleted from font path.
[   137.890] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   137.890] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   137.890] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   137.890] (II) Loader magic: 0x7fb367abcb00
[   137.890] (II) Module ABI versions:
[   137.890]     X.Org ANSI C Emulation: 0.4
[   137.890]     X.Org Video Driver: 11.0
[   137.890]     X.Org XInput driver : 16.0
[   137.890]     X.Org Server Extension : 6.0
[   137.892] (!!) More than one possible primary device found.  Using first one seen.
[   137.892] (--) PCI:*(0:2:0:0) 10de:0647:106b:00a9 rev 161, Mem @ 0xd4000000/16777216, 0xb0000000/268435456, 0xd2000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[   137.892] (--) PCI: (0:3:0:0) 10de:0863:106b:00ac rev 177, Mem @ 0xd6000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/131072
[   137.892] (II) Open ACPI successful (/var/run/acpid.socket)
[   137.892] (II) LoadModule: "extmod"
[   137.892] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   137.893] (II) Module extmod: vendor="X.Org Foundation"
[   137.893]     compiled for 1.11.3, module version = 1.0.0
[   137.893]     Module class: X.Org Server Extension
[   137.893]     ABI class: X.Org Server Extension, version 6.0
[   137.893] (II) Loading extension MIT-SCREEN-SAVER
[   137.893] (II) Loading extension XFree86-VidModeExtension
[   137.893] (II) Loading extension XFree86-DGA
[   137.893] (II) Loading extension DPMS
[   137.893] (II) Loading extension XVideo
[   137.893] (II) Loading extension XVideo-MotionCompensation
[   137.893] (II) Loading extension X-Resource
[   137.893] (II) LoadModule: "dbe"
[   137.893] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   137.893] (II) Module dbe: vendor="X.Org Foundation"
[   137.893]     compiled for 1.11.3, module version = 1.0.0
[   137.893]     Module class: X.Org Server Extension
[   137.893]     ABI class: X.Org Server Extension, version 6.0
[   137.893] (II) Loading extension DOUBLE-BUFFER
[   137.893] (II) LoadModule: "glx"
[   137.893] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   137.907] (II) Module glx: vendor="NVIDIA Corporation"
[   137.907]     compiled for 4.0.2, module version = 1.0.0
[   137.907]     Module class: X.Org Server Extension
[   137.907] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[   137.907] (II) Loading extension GLX
[   137.907] (II) LoadModule: "record"
[   137.907] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   137.907] (II) Module record: vendor="X.Org Foundation"
[   137.907]     compiled for 1.11.3, module version = 1.13.0
[   137.907]     Module class: X.Org Server Extension
[   137.907]     ABI class: X.Org Server Extension, version 6.0
[   137.907] (II) Loading extension RECORD
[   137.907] (II) LoadModule: "dri"
[   137.908] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   137.908] (II) Module dri: vendor="X.Org Foundation"
[   137.908]     compiled for 1.11.3, module version = 1.0.0
[   137.908]     ABI class: X.Org Server Extension, version 6.0
[   137.908] (II) Loading extension XFree86-DRI
[   137.908] (II) LoadModule: "dri2"
[   137.908] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   137.908] (II) Module dri2: vendor="X.Org Foundation"
[   137.908]     compiled for 1.11.3, module version = 1.2.0
[   137.908]     ABI class: X.Org Server Extension, version 6.0
[   137.908] (II) Loading extension DRI2
[   137.908] (==) Matched nvidia as autoconfigured driver 0
[   137.908] (==) Matched nouveau as autoconfigured driver 1
[   137.908] (==) Matched nv as autoconfigured driver 2
[   137.908] (==) Matched vesa as autoconfigured driver 3
[   137.908] (==) Matched fbdev as autoconfigured driver 4
[   137.908] (==) Assigned the driver to the xf86ConfigLayout
[   137.908] (II) LoadModule: "nvidia"
[   137.908] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   137.908] (II) Module nvidia: vendor="NVIDIA Corporation"
[   137.908]     compiled for 4.0.2, module version = 1.0.0
[   137.908]     Module class: X.Org Video Driver
[   137.909] (II) LoadModule: "nouveau"
[   137.909] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   137.909] (II) Module nouveau: vendor="X.Org Foundation"
[   137.909]     compiled for 1.11.3, module version = 0.0.16
[   137.909]     Module class: X.Org Video Driver
[   137.909]     ABI class: X.Org Video Driver, version 11.0
[   137.909] (II) LoadModule: "nv"
[   137.909] (WW) Warning, couldn't open module nv
[   137.909] (II) UnloadModule: "nv"
[   137.909] (II) Unloading nv
[   137.909] (EE) Failed to load module "nv" (module does not exist, 0)
[   137.909] (II) LoadModule: "vesa"
[   137.910] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   137.910] (II) Module vesa: vendor="X.Org Foundation"
[   137.910]     compiled for 1.11.3, module version = 2.3.0
[   137.910]     Module class: X.Org Video Driver
[   137.910]     ABI class: X.Org Video Driver, version 11.0
[   137.910] (II) LoadModule: "fbdev"
[   137.910] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   137.910] (II) Module fbdev: vendor="X.Org Foundation"
[   137.910]     compiled for 1.11.3, module version = 0.4.2
[   137.910]     ABI class: X.Org Video Driver, version 11.0
[   137.910] (==) Matched nvidia as autoconfigured driver 0
[   137.910] (==) Matched nouveau as autoconfigured driver 1
[   137.910] (==) Matched nv as autoconfigured driver 2
[   137.910] (==) Matched vesa as autoconfigured driver 3
[   137.910] (==) Matched fbdev as autoconfigured driver 4
[   137.910] (==) Assigned the driver to the xf86ConfigLayout
[   137.910] (II) LoadModule: "nvidia"
[   137.910] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   137.910] (II) Module nvidia: vendor="NVIDIA Corporation"
[   137.910]     compiled for 4.0.2, module version = 1.0.0
[   137.910]     Module class: X.Org Video Driver
[   137.910] (II) UnloadModule: "nvidia"
[   137.910] (II) Unloading nvidia
[   137.910] (II) Failed to load module "nvidia" (already loaded, 32691)
[   137.910] (II) LoadModule: "nouveau"
[   137.910] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   137.910] (II) Module nouveau: vendor="X.Org Foundation"
[   137.910]     compiled for 1.11.3, module version = 0.0.16
[   137.910]     Module class: X.Org Video Driver
[   137.910]     ABI class: X.Org Video Driver, version 11.0
[   137.910] (II) UnloadModule: "nouveau"
[   137.910] (II) Unloading nouveau
[   137.910] (II) Failed to load module "nouveau" (already loaded, 32691)
[   137.910] (II) LoadModule: "nv"
[   137.911] (WW) Warning, couldn't open module nv
[   137.911] (II) UnloadModule: "nv"
[   137.911] (II) Unloading nv
[   137.911] (EE) Failed to load module "nv" (module does not exist, 0)
[   137.911] (II) LoadModule: "vesa"
[   137.911] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   137.911] (II) Module vesa: vendor="X.Org Foundation"
[   137.911]     compiled for 1.11.3, module version = 2.3.0
[   137.911]     Module class: X.Org Video Driver
[   137.911]     ABI class: X.Org Video Driver, version 11.0
[   137.911] (II) UnloadModule: "vesa"
[   137.911] (II) Unloading vesa
[   137.911] (II) Failed to load module "vesa" (already loaded, 0)
[   137.911] (II) LoadModule: "fbdev"
[   137.911] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   137.911] (II) Module fbdev: vendor="X.Org Foundation"
[   137.911]     compiled for 1.11.3, module version = 0.4.2
[   137.911]     ABI class: X.Org Video Driver, version 11.0
[   137.911] (II) UnloadModule: "fbdev"
[   137.911] (II) Unloading fbdev
[   137.911] (II) Failed to load module "fbdev" (already loaded, 0)
[   137.911] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 10:59:51 PDT 2012
[   137.911] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   137.911] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   137.911] (II) NOUVEAU driver for NVIDIA chipset families :
[   137.911]     RIVA TNT        (NV04)
[   137.911]     RIVA TNT2       (NV05)
[   137.911]     GeForce 256     (NV10)
[   137.911]     GeForce 2       (NV11, NV15)
[   137.911]     GeForce 4MX     (NV17, NV18)
[   137.911]     GeForce 3       (NV20)
[   137.911]     GeForce 4Ti     (NV25, NV28)
[   137.911]     GeForce FX      (NV3x)
[   137.911]     GeForce 6       (NV4x)
[   137.911]     GeForce 7       (G7x)
[   137.911]     GeForce 8       (G8x)
[   137.911]     GeForce GTX 200 (NVA0)
[   137.911]     GeForce GTX 400 (NVC0)
[   137.911] (II) VESA: driver for VESA chipsets: vesa
[   137.911] (II) FBDEV: driver for framebuffer: fbdev
[   137.912] (--) using VT number 7

[   137.914] (II) Loading sub module "fb"
[   137.914] (II) LoadModule: "fb"
[   137.914] (II) Loading /usr/lib/xorg/modules/libfb.so
[   137.915] (II) Module fb: vendor="X.Org Foundation"
[   137.915]     compiled for 1.11.3, module version = 1.0.0
[   137.915]     ABI class: X.Org ANSI C Emulation, version 0.4
[   137.915] (II) Loading sub module "wfb"
[   137.915] (II) LoadModule: "wfb"
[   137.915] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   137.915] (II) Module wfb: vendor="X.Org Foundation"
[   137.915]     compiled for 1.11.3, module version = 1.0.0
[   137.915]     ABI class: X.Org ANSI C Emulation, version 0.4
[   137.915] (II) Loading sub module "ramdac"
[   137.915] (II) LoadModule: "ramdac"
[   137.915] (II) Module "ramdac" already built-in
[   137.915] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   137.915] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   137.915] (II) Loading /usr/lib/xorg/modules/libfb.so
[   137.915] (WW) Falling back to old probe method for vesa
[   137.915] (WW) Falling back to old probe method for fbdev
[   137.915] (II) Loading sub module "fbdevhw"
[   137.915] (II) LoadModule: "fbdevhw"
[   137.915] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   137.915] (II) Module fbdevhw: vendor="X.Org Foundation"
[   137.915]     compiled for 1.11.3, module version = 0.0.2
[   137.915]     ABI class: X.Org Video Driver, version 11.0
[   137.915] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   137.915] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   137.915] (==) NVIDIA(0): RGB weight 888
[   137.915] (==) NVIDIA(0): Default visual is TrueColor
[   137.915] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   137.915] (**) NVIDIA(0): Option "NoLogo" "True"
[   137.915] (**) NVIDIA(0): Enabling 2D acceleration
[   138.374] (II) NVIDIA(0): NVIDIA GPU GeForce 9600M GT (G96) at PCI:2:0:0 (GPU-0)
[   138.374] (--) NVIDIA(0): Memory: 524288 kBytes
[   138.374] (--) NVIDIA(0): VideoBIOS: 62.94.58.00.18
[   138.374] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   138.374] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   138.377] (--) NVIDIA(0): Valid display device(s) on GeForce 9600M GT at PCI:2:0:0
[   138.377] (--) NVIDIA(0):     DFP-0
[   138.377] (--) NVIDIA(0):     DFP-1
[   138.377] (--) NVIDIA(0):     DFP-2
[   138.377] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[   138.377] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[   138.377] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[   138.377] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[   138.377] (--) NVIDIA(0): DFP-2: 480.0 MHz maximum pixel clock
[   138.377] (--) NVIDIA(0): DFP-2: Internal DisplayPort
[   138.377] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[   138.380] (EE) NVIDIA(0): Failing initialization of X screen 0
[   138.396] (II) UnloadModule: "nvidia"
[   138.396] (II) Unloading nvidia
[   138.397] (II) UnloadModule: "wfb"
[   138.397] (II) Unloading wfb
[   138.397] (II) UnloadModule: "fb"
[   138.397] (II) Unloading fb
[   138.397] (EE) Screen(s) found, but none have a usable configuration.
[   138.397] 
Fatal server error:
[   138.397] no screens found
[   138.397] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   138.397] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   138.397] 
[   138.402]  ddxSigGiveUp: Closing log
[   138.402] Server terminated with error (1). Closing log file.
 

```

---

### Post by jgnome on 2013-03-03
Okay, after more tinkering, I finally got Ubuntu 12.04 booted in EFI mode. Here are the steps I did:


- when you get to the grub menu, hit "e" over regular 12.04 boot
- add "outb 0x750 0" to the second line.  your menu entry should look like this:
```

menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux     --class gnu --class os {
    outb 0x750 0
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt5)'
    search --no-floppy --fs-uuid --set=root bc495raf-515r-4r2b-b3de-0ec679a7303a
    linux   /boot/vmlinuz-3.0.0-12-generic root=UUID=bc495raf-515r-4r2b-    b3de-0ec679a7303a ro hpet=force
    initrd  /boot/initrd.img-3.0.0-12-generic
}

```

That let me boot into Ubuntu.  The 9600 is disabled and the 9400 is the only GPU activated.

I don't really know how to make this change permanent though.

The link I got the answer from is here:
[http://askubuntu.com/questions/73332/how-to-deactivate-nvidia-9600m-gt-on-a-macbookpro-5-1-5-2-5-3](http://askubuntu.com/questions/73332/how-to-deactivate-nvidia-9600m-gt-on-a-macbookpro-5-1-5-2-5-3)

---

### Post by Gilgalidd on 2013-04-09
Hi, I'm new with ubuntu on a MacBookPro(5.1) and I would like know if is it possible to replace my osX hard drive by a newer for an install of Ubuntu 12.10 or 13.04 and switch the hard drive if i would like re-use osX.

Is it possible to install ubuntu without any damage to my mac (BIOS or anything) if I follow these instructions : [http://ubuntuforums.org/showthread.php?t=2088983&p=12407951#post12407951](http://ubuntuforums.org/showthread.php?t=2088983&p=12407951#post12407951)

Thanks,


Edit : 
Finally, I've instal ubuntu in dualboot and it work great with your help.  Thanks a lot

---


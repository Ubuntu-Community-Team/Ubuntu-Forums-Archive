---
title: "Re: Error: you need to load kernel first"
date: 2015-07-24
forum: Apple Hardware Users
---

### Post by aksel2 on 2015-07-24
It is Official :mad::redface::mrgreen: I Am goin :arrow: ](*,)BANANAZZ!!!
"God protect us all" like bob marley sang in his song...
I have been trying to Install UBUNTU MBP on a 13" MacbookPro 2012 with Yosemite and a Windows 7 bootcamp dual boot for the last three days, with this ..... error
Cannot load Kernel!!!!!! 
imma .... stay calm and try to solve the problem
Okay! 

So here is the case guyz:

MBP 2012
OSX Yosemite
Bootcamped with Windows7 - 64bit

Ubuntu LiveCD 14.04.02 LTS - 64bit
Ubuntu LiveUSB 14.04.02 LTS - 64nbit (same as LiveCD)

USB drive with three partitions:::
1/       /dev/sdc1 EfiBootLoad
2/      /dev/sdc2  Ubuntu
3/     /dev/sdc3  swap "thing"

Booting in Ubuntu in TRY mode from LiveCD
Connecting USB:
Ubuntu sees Ubuntu Partition

not EfiBootLoad partition

so

Openning Terminal::
```
sudo mkdir /media/mountefi
sudo mount -o loop /dev/sdc1 /media/mountefi
```

This lets me mount my efibootload partition and open efi folder inside.
This partition only has an efi folder in it, which contains a boot folder and a ubuntu folder.
the boot folder contains GRUB.CFG

I open the GRUB.CFG file in teminal using:::
```
sudo nano '..........gru.cfg'

I read

[COLOR=#000000][FONT=verdana]# grub.cfg for MBP USB Install Ubuntu[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]# Timeout for menu[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]timeout=20[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]default=0[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]menuentry "UBUNTU MBP" {[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]fakebios[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]root=hd0,2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]linux /vmlinuz root=/dev/sdb2 video=efifb agp=off   [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]initrd /initrd.img[/FONT][/COLOR]
```

From this point::
I Loaded from Efi Boot (usb)
Menuentry: I see Ubuntu MBP
"ENTER"
I get this
Rom is present
Error: you need to load Kernel First
so I comeback
Press C
Enter command line
Type in
reader.rescue
Exit
AND FROM THERE
I boot into Ubuntu efibootload

So "Success!!" I say \\:D/

As always, I got happy toooo sooon..

Reboot,
and there I was again with the same error but this time,
exit
booted in windows7

So I came back to the GRUB.CFG file and changet the linux root value
```

:::


[COLOR=#000000][FONT=verdana]# grub.cfg for MBP USB Install Ubuntu[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]# Timeout for menu[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]timeout=20[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]default=0[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]menuentry "UBUNTU MBP" {[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]fakebios[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]root=hd0,2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]linux /vmlinuz root=/dev/sdc2 video=efifb agp=off   [/FONT][/COLOR][COLOR=#000000][FONT=verdana]#sdc2 because Ubuntu is there[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]initrd /initrd.img

[/FONT][/COLOR]USB is SDC  64GB  (as confirmed in gparted)
```

This didnt work neither

So i changed the grub.cfg again
```

::

[COLOR=#000000][FONT=verdana]# grub.cfg for MBP USB Install Ubuntu[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]# Timeout for menu[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]timeout=20[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]default=0[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]menuentry "UBUNTU MBP" {[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]fakebios[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]root=hd0,2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]linux /boot/vmlinuz-3.16.04-generic-....      root=/dev/sdc2 video=e$fifb agp=off   [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]initrd /boot/initrd.img-3.16.04-generic...  
```

[/FONT][/COLOR]This still does not.... work

So ichanged the

root=hd0,2   

into

root=hd2

this got me with the USB drive as SDB! so i changed it back to hd0,2 and come back to SDC

I added [ ] in between, tried ( ), didnt work...

I installed ubuntu's boot folders in Ubuntu sdc2 too. 

didnt work

Is anyone familiar with this error? Can someone help me out here please! I beg of you.... ):P IDEBEGYOUNA!!

Thanks in advance guys and girls,

Im really going full moon headed... LiveUSB takes forever to load, thus changing my grub.cfg file takes forever for only one line... They say patience is the key... to what door for moonness sake!

[-o

---

### Post by night_sky2 on 2015-07-24
You should request help in the support section of the forum. 

*Ubuntu, Linux and OS Chat*
 is for casual discussions between users.

---

### Post by aksel2 on 2015-07-24
will do thanks

It is Official :mad::redface::mrgreen: I Am goin :arrow:](*,)BANANAZZ!!!
"God protect us all" like bob marley sang in his song...
I have been trying to Install UBUNTU MBP on a 13" MacbookPro 2012 with Yosemite and a Windows 7 bootcamp dual boot for the last three days, with this ..... error
Cannot load Kernel!!!!!! 
imma .... stay calm and try to solve the problem
Okay! 

So here is the case guyz:

MBP 2012
OSX Yosemite
Bootcamped with Windows7 - 64bit

Ubuntu LiveCD 14.04.02 LTS - 64bit
Ubuntu LiveUSB 14.04.02 LTS - 64bit (same as LiveCD)

I did not use rEFIt nor rEFInd.

USB drive with three partitions:::
1/ /dev/sdc1 EfiBootLoad
2/ /dev/sdc2 Ubuntu
3/ /dev/sdc3 swap partition

Booting in Ubuntu in TRY mode from LiveCD
Connecting USB:
Ubuntu sees Ubuntu Partition

not EfiBootLoad partition

so

Openning Terminal::
sudo mkdir /media/mountefi
sudo mount -o loop /dev/sdc1 /media/mountefi

This lets me mount my efibootload partition and open efi folder inside.
This partition only has an efi folder in it, which contains a boot folder and a ubuntu folder.
the boot folder contains GRUB.CFG

I open the GRUB.CFG file in teminal using:::
sudo nano '..........gru.cfg'

I read

# grub.cfg for MBP USB Install Ubuntu

# Timeout for menu
timeout=20
default=0

menuentry "UBUNTU MBP" {
fakebios
root=hd0,2
linux /vmlinuz root=/dev/sdb2 video=efifb agp=off 
initrd /initrd.img

From this point::
I Loaded from Efi Boot (usb)
Menuentry: I see Ubuntu MBP
"ENTER"
I get this
Rom is present
Error: you need to load Kernel First
so I comeback
Press C
Enter command line
Type in
reader.rescue
Exit
AND FROM THERE
I boot into Ubuntu efibootload

So "Success!!" I say \\:D/

As always, I got happy toooo sooon..

Reboot,
and there I was again with the same error but this time,
exit
booted in windows7

So I came back to the GRUB.CFG file and changet the linux root value

:::


# grub.cfg for MBP USB Install Ubuntu

# Timeout for menu
timeout=20
default=0

menuentry "UBUNTU MBP" {
fakebios
root=hd0,2
linux /vmlinuz root=/dev/sdc2 video=efifb agp=off #sdc2 because Ubuntu is there
initrd /initrd.img

USB is SDC 64GB (as confirmed in gparted)

This didnt work neither

So i changed the grub.cfg again

::

# grub.cfg for MBP USB Install Ubuntu

# Timeout for menu
timeout=20
default=0

menuentry "UBUNTU MBP" {
fakebios
root=hd0,2
linux /boot/vmlinuz-3.19.0-15-generic.efi.signed root=/dev/sdc2 video=e$fifb agp=off 
initrd /boot/initrd.img-3.19.0-15-generic

This ... still does not work

So i changed the

root=hd0,2 

into

root=hd2

this got me with the USB drive as SDB! so i changed it back to hd0,2 and come back to SDC

tried root=hd0,3
I added [ ] in between, tried ( ), didnt work...

I installed ubuntu's boot folders in Ubuntu sdc2 too. 

didnt work

Is anyone familiar with this error? Can someone help me out here please! I beg of you.... ):P

Thanks in advance guys and girls,

Im really going full moon headed... LiveUSB takes forever to load, thus changing my grub.cfg file takes forever for only one line... They say patience is the key... to what door for moonness sake!




EDIT:::
I will try this new edit and will let you know
""
I…once I select Ubuntu and click enter is says something about it needs to load the operating system first.

Actually, it wants to load the kernel. For some reason, your link to initrd is problematic. What you can do is modify the menuentry in the grub.cfg to point directly to the needed files rather than the links in the root directory. For instance what may currently read as:

menuentry "Ubuntu, Linux" {
search    --set /vmlinuz
insmod    ext2
linux    /vmlinuz root=/dev/sdc2 video=efifb
initrd    /initrd.img
}

Try adding a copy of the above, but change it as such:

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
search    --set /vmlinuz
insmod    ext2
linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc2 video=efifb
initrd    /boot/initrd.img-2.6.31-14-generic
}

This way it loads the kernel directly. Once booted, go to your /boot folder and note the most recent version of vmlinuz and initrd and add them as yet another menuentry into your grub.cfg file until you find the one that works best.

Note: I prefer to replace the search line to address the drive directly. Changing, in my case:

search    --set /vmlinuz

to

set root=(hd1,2)

I also removed the 'video=efifb" since my iMac's nVidia card is supported.

LasVegas ""

---

### Post by sandyd on 2015-07-24
Moved to *New to Ubuntu*

---

### Post by aksel2 on 2015-07-24
Alright! Good news:

I Changed 

# grub.cfg for MBP USB Install Ubuntu

# Timeout for menu
timeout=20
default=0

menuentry "UBUNTU MBP" {
fakebios
root=hd0,2
linux /boot/vmlinuz-3.19.0-15-generic.efi.signed root=/dev/sdc2 video=e$fifb agp=off 
initrd /boot/initrd.img-3.19.0-15-generic

to

# grub.cfg for MBP USB Install Ubuntu

# Timeout for menu
timeout=20
default=0

menuentry "UBUNTU MBP" {
fakebios
root=(hd1,2)
linux /boot/vmlinuz-3.19.0-15-generic root=/dev/sdc2 video=e$fifb agp=off 
initrd /boot/initrd.img-3.19.0-15-generic

I now can boot Ubuntu MBP

problem is, i now gey stuck to this line:

1.831012  --- end trace 9aaf81e7a74f81ee

any thoughts?

I rebooted the mac, went back to the terminal

I changed root=[1,2]

rebooted:: and it didnt work : brought to me to the same error, "you need to load the kernel first"

So i put back the same as I did before
 
Rebooted again to see the other lines::::

guess what:
Yes

The same error! 

I have no clue what is happenning

I really wanted to solve this, but visibly there is something wrong which I cannot correct. I will install it through Disk Utility and make a new partition on my hdd to put it on there. I would really want to know if anyone solved this or knows anything about it.
:-({|=

---

### Post by coffeecat on 2015-07-25
Two threads merged, and a few serial posts merged.

@aksel2, your posts (at least until I edited a couple) contain a mass of unnecessary color and fonts tags. You don't need to specify black for text since posted text defaults to black anyway, and it defaults to an elegant sans serif font as well. Please only use the formatting controls in the editor toolbar when you need to highlight small portions of text.

---

### Post by aksel2 on 2015-07-25
I copy/pasted some elements, I think this is why because I absolutely didn't use any text formatting tools at all. I apologize about that and thank you for your concern.

BTW, I like your picture!

I now have decided to use disk utility.
I already have OSX Yosemite
and Bootcamped W7
in dual boot.
I added a partition to the OSX existing so I could install Ubuntu on it.
I then rebooted the mbp on the LiveCD I did and selected Install Ubuntu.

Then I chose the partition I had created to install Ubuntu as Ext4 with " / " as root.
Ubuntu seemed to have installed correcty with its updates but when I reboot the mac pressing alt to chose my booting partition, no ubuntu partitions visible.
So I boot in OSX, go to my DiskUtil to see that my drive is called by a strange disk0s4 name and it is not black, the partition is present but its name faded. Somehow Ubuntu is not recognized on my mac...

What is there to do? I don't want to wait with the liveCD all the time in Try mode. This is not an option.


Can somebody help me please

edit:

Diskutil list in terminal gives me
0       Guid partition scheme 250.1GB disk0
1       EFI EFI 209.7 MB disk0s1
2      Apple HFS OSX 52.6GB disk0s2    #visible during boot selection
3      Apple_Boot Recovery HD 650.0 MB disk0s3     #visible during boot selection
4      Microsoft Basic Data 52.6 GB disk0s4               #This is where it's strange to have 'Microsoft basic data' as the name for disk0s4
5      Microsoft Basic Data BOOTCAMP 144.0 GB disk0s5     #visible during boot selection

What I am about to write is difficult... I installed rEFInd, and finally I could see my Ubuntu partition. I now have my three partitions, and they all work together. I'm a happy guy right now.

Still, I would have loved to know why I had the Kernel Error with my LiveUSB and how to fix it...

---

### Post by howefield on 2015-07-25
Thread moved to the "*Apple Hardware Users*" forum.

---


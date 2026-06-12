---
title: "Cannot boot"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Bikespot on 2008-02-01
I just installed Ubuntu Server 7.10 On my external harddrive. Connected through USB.

It only has Ubuntu on it , no windows.

I went through partitioned it , and installed  DNS Server and Ubuntu Desktop. Then i went back and installed the two boot things that where listed. 

I restarted trying to boot ubuntu but nothing happened. 

I went into BIOS and changed Boot Device i tired all the USB boots

Usb Fdd
Usb CdRom
Usb Zip/Mo
Usb LS120
Usb HDD

I tired them all but nothing happened. 

How do i boot up ubuntu?

---

### Post by (((X))) on 2008-02-02
> **Bikespot said:**
> 
I went through partitioned it , and installed  DNS Server and Ubuntu Desktop.
How do i boot up ubuntu?

If you are not able to boot Ubuntu try to edit partitons in grub menu, on grubmenu press e or so to edit partition parameters. You can also edit /boot/grub/menu.lst to always boot the way you want.

change

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=4a4c7b6a-3cc5-441a-875e-f99bcfd3b48e ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic

to

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda?yourpartition ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic

creating new partitions may change UUID number.

---

### Post by Bikespot on 2008-02-02
> **(((X))) said:**
> If you are not able to boot Ubuntu try to edit partitons in grub menu, on grubmenu press e or so to edit partition parameters. You can also edit /boot/grub/menu.lst to always boot the way you want.

change

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=4a4c7b6a-3cc5-441a-875e-f99bcfd3b48e ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic

to

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda?yourpartition ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic

creating new partitions may change UUID number.

How do i get to the grub menu when i start the computer up?

---

### Post by azimuth on 2008-02-02
You do not have grub set to the right partition. To change it:

boot live cd

open terminal
in the terminal type:
sudo grub
find /boot/grub/stage 1 ( you will get a reply of something like (hd0,2) )
root (hd0,2)  or the location from the find command
setup (sd0)  or whatever your usb drive is identified as
quit
exit

Now reboot with your usb drive set as first in the boot order in the bios

I just reread your original post. You may not have a LiveCD with the Server install. If that is the case, then your best bet is to download a Grub LiveCd to do the repairs.

---

### Post by Bikespot on 2008-02-02
> **azimuth said:**
> You do not have grub set to the right partition. To change it:

boot live cd

open terminal
in the terminal type:
sudo grub
find /boot/grub/stage 1 ( you will get a reply of something like (hd0,2) )
root (hd0,2)  or the location from the find command
setup (sd0)  or whatever your usb drive is identified as
quit
exit

Now reboot with your usb drive set as first in the boot order in the bios

I just reread your original post. You may not have a LiveCD with the Server install. If that is the case, then your best bet is to download a Grub LiveCd to do the repairs.

Im really new to this. 

I dont know how to get to the Terminal.
 
I'm at the Screen when you put the cd in that says  Install .... check cd ....

---

### Post by azimuth on 2008-02-02
Are you using a live cd or the alternate install cd?

---

### Post by Bikespot on 2008-02-02
> **azimuth said:**
> Are you using a live cd or the alternate install cd?

I'm using the Cd that i burned Ubuntu Server 7.10 on to. 


I just tried out Ubuntu Desktop and wow , its so much easier to install. Ok back to installing Server version. I want to try and boot from my external usb drive that i installed Ubuntu server onto. 

I have no idea how , i tried going into Bio and changing boot device but still nothing. I dont know how to get to the Terminal thing.

---

### Post by azimuth on 2008-02-03
You are going to need the Ubuntu LiveCD. With it you can run Ubuntu from just the cd. This will allow you to do repairs on your "installed" system.  A terminal is nothing more that a command line interface.

---

### Post by Bikespot on 2008-02-03
What is the liveCd?  Is that the desktop one?

---

### Post by azimuth on 2008-02-03
Yes that is it. The LiveCD will boot and run Ubuntu from just the cd without using the hard drive. This allows partitioning and other functions that can't be accomplished when running on a drive that needs repair. Here is a link [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) that explains the proceedure better than I did in the earlier post. Do take note here that the LiveCD does require 256Mb of ram because the OS is loaded into and is run from ram.

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> Yes that is it. The LiveCD will boot and run Ubuntu from just the cd without using the hard drive. This allows partitioning and other functions that can't be accomplished when running on a drive that needs repair. Here is a link [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) that explains the proceedure better than I did in the earlier post. Do take note here that the LiveCD does require 256Mb of ram because the OS is loaded into and is run from ram.


Im starting to figure out this.

I installed the server version. 

Then i went into the liveCd , i'm in it right now. I opened a terminal and did that thing in the thread above ^^^ . Now i'm going to restart and see if this works. :)

---

### Post by azimuth on 2008-02-03
I am interested in how it works for you, let us know.

---

### Post by Bikespot on 2008-02-03
It says

(hd0,0)

I restarted , nothing happened.

Changed BIOS and tried all the usb devices.

Still nothing.  Went back into Linux ubuntu livecd , checked the files. I found boot/grub/menu.1st

I found the title thing it says.

Title           Ubuntu 7.10 Kernel 2.6.22-14 Server
Root         (hd0,0)
Kernal       /boot/vmlinuz-2.6.22-14-server  root=UUID=c2adaaa2-e12b-46b9-83f8-fdeb76e99425  ro queit splash

initrd      /boot/initrd.img-2.6.22-14-Server


What should i change? 

Also what else can i try to boot from my external USB?

---

### Post by azimuth on 2008-02-03
That shows that your Ubuntu's root folder is on your primary partition of your internal hard drive or atleast that is where grub is looking to find it. What drives do you have and what is installed on them? 

Also: You mentioned installing two boot thingies (not as technical as it might be). If you installed both grub and lilo, that could be your problem. Those are either or options and do not play nice together.

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> That shows that your Ubuntu's root folder is on your primary partition of your internal hard drive or atleast that is where grub is looking to find it. What drives do you have and what is installed on them? 

Also: You mentioned installing two boot thingies (not as technical as it might be). If you installed both grub and lilo, that could be your problem. Those are either or options and do not play nice together.


I only have my External drive connected throguh usb. I made it partition the whole drive when installing Ubuntu Server.

Then i have my C drive with windows , but i disconnect that.

I dont have the two boot thingies anymore, because i reinstalled the server again. This time it automatically installed Grub? loader during the finishing steps. I think thats the name of it.

---

### Post by azimuth on 2008-02-03
If you have reinstalled with only the usb drive available and you have your bios set to boot first from usb hhd then it should be working.

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> If you have reinstalled with only the usb drive available and you have your bios set to boot first from usb hhd then it should be working.

I will try 

1st  USb hhd


and i will disable other devices.

---

### Post by Bikespot on 2008-02-03
You mean hdd? I think thats what was listed.

Anyways i set that to first device , i had C drive connected and that started up.

So i removed C drive and tried again. Nothing , didn't work. 

Not sure whats wrong. :(

---

### Post by Bikespot on 2008-02-03
[http://ubuntuforums.org/attachment.php?attachmentid=58569&stc=1&d=1202074820](http://ubuntuforums.org/attachment.php?attachmentid=58569&stc=1&d=1202074820)

Im going to try the grub terminal thing again , i took an image of it.

When finished and restart do i put the cd back in? Or not , if so which cd.

This is what i get when i put in "quit"

[http://ubuntuforums.org/attachment.php?attachmentid=58570&stc=1&d=1202075021](http://ubuntuforums.org/attachment.php?attachmentid=58570&stc=1&d=1202075021)

---

### Post by azimuth on 2008-02-03
You must have had the c drive connected when you reinstalled the server and grub installed to the MBR of the c drive. If that is not the case, then your bios is not properly following the boot order. Sorry I have to ask, you are saving the bios configuration and not just exiting out of the bios setup?

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> You must have had the c drive connected when you reinstalled the server and grub installed to the MBR of the c drive. If that is not the case, then your bios is not properly following the boot order. Sorry I have to ask, you are saving the bios configuration and not just exiting out of the bios setup?


I didn't have the C drive plugged in when i installed the server or when i installed grub. 

When i go into Bios i do save by pressing f8 , the settings are there when i go back so it must be saving. Is there something else i can do to like search for the exact drive and try to boot from there?

What is MBR?

---

### Post by azimuth on 2008-02-03
MBR is the master boot record. This is where the bios looks to start loading the operating system. From your screen shots, it appears that your linux system is on your internal hard drive (hd0) . Normaly a usb drive is seen as a serial drive (sd0). I am stumped, we need somebody with some new ideas here.

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> MBR is the master boot record. This is where the bios looks to start loading the operating system. From your screen shots, it appears that your linux system is on your internal hard drive (hd0) . Normaly a usb drive is seen as a serial drive (sd0). I am stumped, we need somebody with some new ideas here.

I reinstalled the Server again , tried it and same thing.

I got an idea i'm going to install the Ubuntu Desktop on the external drive. If it boots from that then we know the external drive is bootable or if the BIOS is working right. 


Also about (sd0)  , it came up as (hd0,0) so i dont know why it would come up as that, but thats where it found it.

---

### Post by Bikespot on 2008-02-03
I dont know if this is useful or not but this is what the name of the external drive.

---

### Post by Bikespot on 2008-02-03
I installed Ubuntu Desktop on the external drive. 

Restarted , changed BIOS settings,  Won't boot.

Something is wrong. :(

---

### Post by azimuth on 2008-02-03
Did you have the internal drive plugged it when you installed?

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> Did you have the internal drive plugged it when you installed?


No its not plugged in.

Why should i have it in?

---

### Post by azimuth on 2008-02-03
That was just for clarification. Do you still have a bootable windows partition? If so, you may want to just use it for now and take a breather. Sometimes it helps to leave a problem for a few days and come back to it fresh. Maybe by then someone will come along to this thread with the answers.

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> That was just for clarification. Do you still have a bootable windows partition? If so, you may want to just use it for now and take a breather. Sometimes it helps to leave a problem for a few days and come back to it fresh. Maybe by then someone will come along to this thread with the answers.

Yea i do.


Hopefully someone will know something about this.

Also i found somethings while searching
[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253)

Do you know if i can see a list of MBR  or even edit it or something to try get it to boot.

---

### Post by azimuth on 2008-02-03
I had an epifany. I think your outboard drive is suffering from a similar problem with older bios's. Older bios could not read boot information beyound cylinder 1024. The only way to boot and run Linux on drives larger than 2Gb was to make sure the boot partition was completely within the first 1024 cylinders. The partitioning scheme was to make a small boot partition at the very begining of the drive. All of the boot information can fit within 50Mb. Your usb drive is way big enough to leave 180Mb for the boot without suffering realestate cramping in the rest of the drive. So what I propose is atleast three partitions. They would look something like this:

/boot 150Mb ext3 or ext2
/   (root)  bulk of drive   ext3
/swap  1 Gb ( or about twice your ram size)

Just be sure that the /boot is moved to the very front of the drive.

If you are willing to try another install, I am confident this will do it.

---

### Post by Bikespot on 2008-02-03
> **azimuth said:**
> I had an epifany. I think your outboard drive is suffering from a similar problem with older bios's. Older bios could not read boot information beyound cylinder 1024. The only way to boot and run Linux on drives larger than 2Gb was to make sure the boot partition was completely within the first 1024 cylinders. The partitioning scheme was to make a small boot partition at the very begining of the drive. All of the boot information can fit within 50Mb. Your usb drive is way big enough to leave 180Mb for the boot without suffering realestate cramping in the rest of the drive. So what I propose is atleast three partitions. They would look something like this:

/boot 150Mb ext3 or ext2
/   (root)  bulk of drive   ext3
/swap  1 Gb ( or about twice your ram size)

Just be sure that the /boot is moved to the very front of the drive.

If you are willing to try another install, I am confident this will do it.



You might be right , because my computer is 5 years old.

About the partitions , i dont know how to set it up like that.  :(

Can you give me details on how to set it up like that? I'm guessing in the server install i need to go into the partitions part and click manual instead of full disk or resize.

---

### Post by azimuth on 2008-02-03
> **Bikespot said:**
> You might be right , because my computer is 5 years old.

About the partitions , i dont know how to set it up like that.  :(

Can you give me details on how to set it up like that? I'm guessing in the server install i need to go into the partitions part and click manual instead of full disk or resize.

Yes, manual is what you would use. When it first shows you the partitions, delete all of them and start from scratch. In the space made available start with /boot and limit the size to something under 200Mb. I think my boot partition has 17Mb used in it. You will get an option to make that partition at the start or end of the avilable space. You want it at the beginning. Next make your /swap partition. It can be at the end or beginning of the remaining space. Size it to twice your ram. You can make the rest of the space /root. You may later want to break this up into extra partitions like /home and /var , For right now, that would just complicate it. 
If this works, it is because the controler in your outboard drive is not reading far enough into your 360Gb drive to find the /boot information. Good luck!

---

### Post by Bikespot on 2008-02-03
Will do

Im going to try in desktop first.


Question 

In create new partition is says

Use as:


ext3
ext2
reiserfs
jkf
xfs
fat16
fat32 
swap
efi
dont_use


I dont see root or boot there.

Edit:

Never mind i figured i out.

/boot 150Mb ext3 or ext2
/ (root) bulk of drive ext3
/swap 1 Gb ( or about twice your ram size)

What should /swap be called?

---

### Post by azimuth on 2008-02-03
The /boot /root are mount points, you can manualy put them in or wait and edit the partitions later. Just be sure to have them set before you leave the partitioner.

---

### Post by azimuth on 2008-02-04
When you get to the swap just chose swap in the file format and it will set itself.

---

### Post by Bikespot on 2008-02-04
How does this look?

---

### Post by azimuth on 2008-02-04
It looks right. You may as well add a /home in the remaining free space.....lol

---

### Post by Bikespot on 2008-02-04
Hit forward and it says

No root file system is defined.

Something is wrong wiht /root file.

Does it matter if /root file is  Beginning or End , also what about the Primary or logical?

---

### Post by azimuth on 2008-02-04
oh...root is just "/ "   not "/root"  just edit that partition.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> oh...root is just "/ "   not "/root"  just edit that partition.

Oh thats why , works now. I will continue setup.

---

### Post by azimuth on 2008-02-04
Good luck with the install. I'll check up on you tommorow to see how it turned out.

---

### Post by Bikespot on 2008-02-04
I think i made a mistake somewhere. Not sure , but im going to try that again.

Once finish installing , i should go into bios and change it to  Usb Hhd

Right?

I just added Screenshot of the partitions i just made.

---

### Post by azimuth on 2008-02-04
That looks correct and it should work. If you set your boot order to:
cd
usb hdd

then you won't need to keep changing it while you are working on this thing. Just pull the LiveCD out of the drive when you reboot.

---

### Post by Bikespot on 2008-02-04
Alright i installed it again.

When it finished installing it say 

Continue  using livecd    or Restart

So i clicked restart and it had black screen with some text saying checking boot or something like that. I waited for 2 minutes nothing happened. So i restarted computer , took cd out.

Nothing.....  :(

I dont understand why its not working.

---

### Post by azimuth on 2008-02-04
What is "nothing"? Do you get any error message or just a blank screen? Was the /boot partiton set as a primary or logical?

---

### Post by Bikespot on 2008-02-04
Everything was set to primary.

When i mean nothing , it says cannot find boot or what ever.

---

### Post by azimuth on 2008-02-04
What I am thinking now is either the /boot partition is not being flagged as bootable or your external drive is not capable of booting. That leaves us with 2 choices. 
1. download and run Gparted LiveCD  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) to check and set the boot flag.
2.hook up your internal drive and put GRUB on it's boot partition and make a standard dual boot system out of things. (this is probably a non reversable option)

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> What I am thinking now is either the /boot partition is not being flagged as bootable or your external drive is not capable of booting. That leaves us with 2 choices. 
1. download and run Gparted LiveCD  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) to check and set the boot flag.
2.hook up your internal drive and put GRUB on it's boot partition and make a standard dual boot system out of things. (this is probably a non reversable option)


Can i have some more information.

1.  [http://download.tuxfamily.org/gpartedlive/](http://download.tuxfamily.org/gpartedlive/)  Which one do i download? When finished downloading put it on a Cd and boot from it right?


2. How do i put GRUB on the boot partition? Also is this going to affect the windows thats already on the c drive. I dont want to loose those files.

---

### Post by azimuth on 2008-02-04
> **Bikespot said:**
> Can i have some more information.

1.  [http://download.tuxfamily.org/gpartedlive/](http://download.tuxfamily.org/gpartedlive/)  Which one do i download? When finished downloading put it on a Cd and boot from it right?


2. How do i put GRUB on the boot partition? Also is this going to affect the windows thats already on the c drive. I dont want to loose those files.

Depends on which method you want to use to download. HTTP or FTP . that is an iso file just like the Ubuntu LiveCD.

Putting grub on your windows boot partition is just back to what we were doing to make sure that grub was setup on your external drive. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> Depends on which method you want to use to download. HTTP or FTP . that is an iso file just like the Ubuntu LiveCD.

Putting grub on your windows boot partition is just back to what we were doing to make sure that grub was setup on your external drive. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


Ok i'm downloading the livecd right now.

I will try that first , not sure what i am looking for.


Then i will put grub on the internal drive.

---

### Post by azimuth on 2008-02-04
Don't go too fast here. You need to understand that most tools on Linux are very powerful and you can trash your system if they are not applied properly. The Gparted is just too look at your partitions at first and only if the boot flag is not set on the /boot partition do you want to do anything. After it opens up just check the column marked flags and see if it has boot set on the primary partition of your external drive. If that flag is already set then just close the program and exit the GUI with the big red button in the top left corner. If the flag isn't set then you will have to set it.

---

### Post by Bikespot on 2008-02-04
I ran that program

Came up at Gnome Partition Editor.

Clicked on G parted-LiveCd  (boot off external-usb-cd:dev/sro)

It did a bunch of commands , entered language and keymap. 

Got into the system. It opened a window. I found the External Drive , here is what was listed for it.

/dev/sda1   ext3  boot
/dev/sda2   linux  swap
/dev/sda3  ext3
/dev/sfa4   ext2

I also saw the internal drive , it had boot on it also.

I will wait to see what you say before i continue.

---

### Post by azimuth on 2008-02-04
send me a screen shot of that window. You may have to move the window to see the screen shot button.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> send me a screen shot of that window. You may have to move the window to see the screen shot button.

I'm in windows now , i did see the screenshot button.

but how do i send that to you , i didn't see any browsers in that program.

---

### Post by azimuth on 2008-02-04
I guess you can't then. If the boot flag is in the first drive then it should have booted. All that leaves is the hardware will not boot. I suspect it is the controller in the outboard drive rather than the computer's bios that is at fault. 
 Now the question is where or not to risk your Win partition to set grub on the internal drive. If you deside to continue, first backup all of your personal files and docs before you do anything else.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> I guess you can't then. If the boot flag is in the first drive then it should have booted. All that leaves is the hardware will not boot. I suspect it is the controller in the outboard drive rather than the computer's bios that is at fault. 
 Now the question is where or not to risk your Win partition to set grub on the internal drive. If you deside to continue, first backup all of your personal files and docs before you do anything else.

Well there was two sections ,

There was the internal drive part. Which i think only showed one file , and it had boot on it.

Then there was the external drive part. It had four parts listed. The first one on that list had boot on it.

Is there a program out there i can make a complete backup of everything on my internal drive and put it on my external drive.

If so what if i just add ubuntu onto the internal drive, i will do the manual part so it doesn't delete windows files. . Then try and boot from there.

---

### Post by azimuth on 2008-02-04
Was your internal drive plugged in when you ran Gparted?

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> Was your internal drive plugged in when you ran Gparted?


Yes

---

### Post by azimuth on 2008-02-04
We need to slow down here. We are working at the very raged edge of my knowledge and I don't want to help you lose your wanted docs and files.
There are programs like Norton Ghost as well as utilities from Western digital and Maxtor to clone drives.
What brand of hard drives do you have?

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> We need to slow down here. We are working at the very raged edge of my knowledge and I don't want to help you lose your wanted docs and files.
There are programs like Norton Ghost as well as utilities from Western digital and Maxtor to clone drives.
What brand of hard drives do you have?

The external drive is Seagate.  Internal is WDC , thats what it says on Device manager.

If i was able to clone i could try to boot from that.

---

### Post by azimuth on 2008-02-04
If you wish, you can even clone your XP Drive with the Ubuntu LiveCD . Instructions are here [http://www.justlinux.com/forum/showthread.php?threadid=134457](http://www.justlinux.com/forum/showthread.php?threadid=134457)

---

### Post by azimuth on 2008-02-04
Since one of your drives is a WD, you can use Data Guard from WD web site.
[http://support.wdc.com/download/index.asp](http://support.wdc.com/download/index.asp) This is the only one I have hands-on knowledge. My Windows drive is a clone made with Data Guard.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> Since one of your drives is a WD, you can use Data Guard from WD web site.
[http://support.wdc.com/download/index.asp](http://support.wdc.com/download/index.asp) This is the only one I have hands-on knowledge. My Windows drive is a clone made with Data Guard.

I will try with the Data Lifeguard program first.

---

### Post by azimuth on 2008-02-04
Now that you have gone to all this work, I think I found the fix. The embarassing part is I was involved in the fix and had completely forgotten it. It was the very first post I ever made on the forums. [http://ubuntuforums.org/showthread.php?p=1507827#post1507827](http://ubuntuforums.org/showthread.php?p=1507827#post1507827) If you would like to throw a few bricks at me, I would completely understand.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> Now that you have gone to all this work, I think I found the fix. The embarassing part is I was involved in the fix and had completely forgotten it. It was the very first post I ever made on the forums. [http://ubuntuforums.org/showthread.php?p=1507827#post1507827](http://ubuntuforums.org/showthread.php?p=1507827#post1507827) If you would like to throw a few bricks at me, I would completely understand.

So in other words we wasted all that time? :)

Not really , but anyways

> Dennis, I am running Ubuntu on a USB drive. I preformated two partitions on the drive for use with XP (data only) and left 32GB unformated. The Live CD found my unformated section and installed without a hitch. I know it can work, you may have to tickle some things on your setup. This was my first Linux install of any kind and I went with the outboard drive because I didn't know what I was getting into  

Isn't that like the same thing we were doing?

I don't understand the fix.

---

### Post by azimuth on 2008-02-04
The bootable partition was a windows partition, the original poster tried the same and the usb would then boot. Mine worked purely by accident, but duplicating my setup seemed to work for others. The amount of handson knowledge you gain working through these little problems is how you learn Linux.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> The bootable partition was a windows partition, the original poster tried the same and the usb would then boot. Mine worked purely by accident, but duplicating my setup seemed to work for others. The amount of handson knowledge you gain working through these little problems is how you learn Linux.


OK , but i still dont understand what i need to do. 

I'm currently still moving files to my external drive , its taking sometime.

---

### Post by azimuth on 2008-02-04
It takes a while with large drives, usb is not the fastest way to go. When you have the drive cloned, then you can go ahead with a dual boot install without worries and even be able to duplicate your main drive even if things were to go terribly wrong. Which they shouldn't but it doesn't hurt to have insurance.

---

### Post by azimuth on 2008-02-04
How much free space do you have on your main drive?

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> It takes a while with large drives, usb is not the fastest way to go. When you have the drive cloned, then you can go ahead with a dual boot install without worries and even be able to duplicate your main drive even if things were to go terribly wrong. Which they shouldn't but it doesn't hurt to have insurance.

Ok , once i get this finished cloning.  What are my steps. 

I want to install the server version this time. What should i be putting in for the partitions?

---

### Post by azimuth on 2008-02-04
First step is do a windows cleanup. Then you need to defragment the drive. After that you will be able to start partitioning and the install.

---

### Post by Bikespot on 2008-02-04
> **azimuth said:**
> How much free space do you have on your main drive?


30 GB

Can i do this on my external drive?

---

### Post by azimuth on 2008-02-04
Is that 30Gb of unformated free space or is that just unused space inside your win partition? How much free space is left on your usb drive?

When you get it all booted up, this may be of use to you [http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/](http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/)

---

### Post by Bikespot on 2008-02-05
> **azimuth said:**
> Is that 30Gb of unformated free space or is that just unused space inside your win partition? How much free space is left on your usb drive?

When you get it all booted up, this may be of use to you [http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/](http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/)

I just got home , anyways it did finish cloning the C: drive. 


30 Gb of free space. Its already formated.

The External holds 320 Gb and i only have about 130 GB of windows files. 

I tried booting from external but it didn't work, not sure what i did wrong. I will check the folder and see.

Edit: I checked the clone drive (external) everything seems to be copied, is there some reason why it won't boot?

I dont know if this is useful or not , but i took a screenshot of msconfig  boot tab.

---

### Post by azimuth on 2008-02-05
> **Bikespot said:**
> I just got home , anyways it did finish cloning the C: drive. 


30 Gb of free space. Its already formated.

The External holds 320 Gb and i only have about 130 GB of windows files. 

I tried booting from external but it didn't work, not sure what i did wrong. I will check the folder and see.

Edit: I checked the clone drive (external) everything seems to be copied, is there some reason why it won't boot?

I dont know if this is useful or not , but i took a screenshot of msconfig  boot tab.

It appears more and more like your outboard drive is incapable of booting. I won't tell you what to do, but rather tell you what I would do. I'd get rid of all the multimedia files from the internal drive (they are already backedup and available on the usb drive). Clean house, get the windows partiton on the internal down to 60Gb used. Defragment that drive. Use Gparted LiveCD to shrink the Win partition to 100Gb. Then, I would install the Ubuntu Server in the unsued space above 100Gb. When Grub is installed, it will pickup the 2 windows installs (both internal and USB drive as well as the server. If asked where to boot from use {hd0) the internal drive, (the external drive won't boot anyway) 

that is what I would do, but the choice is yours.

---

### Post by Bikespot on 2008-02-05
> **azimuth said:**
> It appears more and more like your outboard drive is incapable of booting. I won't tell you what to do, but rather tell you what I would do. I'd get rid of all the multimedia files from the internal drive (they are already backedup and available on the usb drive). Clean house, get the windows partiton on the internal down to 60Gb used. Defragment that drive. Use Gparted LiveCD to shrink the Win partition to 100Gb. Then, I would install the Ubuntu Server in the unsued space above 100Gb. When Grub is installed, it will pickup the 2 windows installs (both internal and USB drive as well as the server. If asked where to boot from use {hd0) the internal drive, (the external drive won't boot anyway) 

that is what I would do, but the choice is yours.


I dont understand why my external drive is incapable of booting. 

Before i try that i'm going to see if i can get some help on this other forum and look at Seagate's site about trying to boot windows on the external drive. 

If its not the external drive problem i think its the BIOS problem .

---

### Post by azimuth on 2008-02-05
> **Bikespot said:**
> I dont understand why my external drive is incapable of booting. 

Before i try that i'm going to see if i can get some help on this other forum and look at Seagate's site about trying to boot windows on the external drive. 

If its not the external drive problem i think its the BIOS problem .

I don't understand it either. It would be nice to get your hands on another usb drive to elimate either the drive or the bios. Good Luck and hope you find the help you need.

---

### Post by Bikespot on 2008-02-05
> **azimuth said:**
> I don't understand it either. It would be nice to get your hands on another usb drive to elimate either the drive or the bios. Good Luck and hope you find the help you need.

I havn't heard anything yet. I sitll need to look on the site.

You know how in windows when you boot up sometimes you see this screen that says 

Boot Windows in Safe Mode
Boot Windows Normally

How do i get to that window? Do you think something would be in there? 

I dont think the MD5 is reading the USB to find the boot file.

---

### Post by azimuth on 2008-02-05
> **Bikespot said:**
> I havn't heard anything yet. I sitll need to look on the site.

You know how in windows when you boot up sometimes you see this screen that says 

Boot Windows in Safe Mode
Boot Windows Normally

How do i get to that window? Do you think something would be in there? 

I dont think the MD5 is reading the USB to find the boot file.

That is usually just hitting F8 while it is booting. I don't think you will find anything there, that Safe Mode just prevents drivers from loading so you get Windows started when it is broken.

MD5? You must mean BIOs. As far as I know, MD5 is just the checksum for ISO files.

---


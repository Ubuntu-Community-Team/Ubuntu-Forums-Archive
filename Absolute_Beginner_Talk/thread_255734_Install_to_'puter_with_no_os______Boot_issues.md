---
title: "Install to 'puter with no os  __  Boot issues"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by maitre2pitza on 2006-09-11
I have a new computer purchased with no OS  (Dell Optiplex from Dell Auction).  I have downloaded the program and burned it to a CD.  How do I make it bootable to start the install?

---

### Post by ewl1217 on 2006-09-11
Could you explain the problems you're having? We can't do much to help you if we don't know what's wrong.

---

### Post by blakesmith on 2006-09-11
You need to go into your bios; hit delete or all of the F1 F2 etc. and set your CD rom as the first boot device.

---

### Post by maitre2pitza on 2006-09-11
With the downloaded disk in the CD drive,  and the setup revised to boot only from the cd I get the message press F1 to try to re-boot or press F2 to re-enter setup (bios setup)  Is the disk supposed to boot or should I install windows and put this over windows?  I would like to have one machine free of the influences of the evil empire.

---

### Post by confused57 on 2006-09-11
Here's an excellent guide to burning an iso:

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

You need to burn the iso "as an image", not as a data or bootable cd...and burn it at a low speed(8x or less).

You'll need to set your computer to boot to the cd drive before the hard drive...you do this by entering bios at bootup by pressing F2, del, etc, there should be a menu of what to press at bootup.
   With it being a Dell, you may need to press "F12" or "F8" at bootup, which gives you an option of booting the cd drive 1st without having to enter bios setup.

You can install Ubuntu on the entire hard drive, you don't need to install Windows...unless you want to dualboot.

---

### Post by blakesmith on 2006-09-11
The disc is supposed to boot, you do not install Ubuntu in windows.  Are you sure you wrote a bootable CD or just a data CD?

---

### Post by bodhi.zazen on 2006-09-11
> **maitre2pitza said:**
> I have a new computer purchased with no OS  (Dell Optiplex from Dell Auction).  I have downloaded the program and burned it to a CD.  How do I make it bootable to start the install?

Put the CD in the drive and boot.

If it does not boot to CD, re-boot and set BIOS to boot to the CD. As you computer boots hit ? Esc, F2, F8 (different on each box it seems).

This will enter bios. Look for a boot section. Change boot order to:
[list=number][*]CO-ROM drive
[*]Floppy
[*]Hard drive[/list]
Save and exit bios, reboot.

---

### Post by catlett on 2006-09-11
> **maitre2pitza said:**
> With the downloaded disk in the CD drive,  and the setup revised to boot only from the cd I get the message press F1 to try to re-boot or press F2 to re-enter setup (bios setup)  Is the disk supposed to boot or should I install windows and put this over windows?  I would like to have one machine free of the influences of the evil empire.

When you get to this part press F2, That will take you into your bios or a menu. I have 2 computers and they are both different.
On one of them when I get to this part, I have a menu with 4 options. floppy, cd rom, hard drive, removable media. I use the arrow key to move to cd rom and then I press enter. This makes the copmputer boot to the cd drive.
On my other computer, this takes me to the bios. It is another menu but bigger. You use the arrow keys to navigate and enter if you want to enter into a sub menu, You want to find the section about booting. When you ghetg there it will give you a choice of boot order. i.e. floppy, cd , hard drive etc Just make sure the cd drive is before the hard drive. Usually you press F10 to save and exit but check to see which key you hit to save changes and exit. It will then boot the cd drive when starting.
Once you get the cd booting just follow the menu. You will have it easy, just select "erase the entire disk and install ubuntu" The installer will tsake care of the rest.

---

### Post by YeahBuntu on 2006-09-12
When you burned the ISO to disc did you simply copy the files over making a data cd or did you:

In your burning program:  COPY CD IMAGE or SAVED IMAGE ?

As long as your bios is set to boot from the CDROM; the Ubuntu Dapper is already setup to be ' bootable ' 

So if your failing somewhere in this process can you elaborate?

It could be that the CDROM on your computer is not working properly.. do you have another operating system cd to test if your CD Drive is working correctly?

---

### Post by maitre2pitza on 2006-09-12
thanks for all the help.  I had the bios thing.  It was the way my son burned the cd.  I'm burning a new one here at the office so I'll try again tonight:D

---

### Post by pesach on 2006-09-12
I've had the same problem, and I followed the instructions.  But when Ubuntu was installed I was not able to boot from the hard drive.  The BIOS setting were set to harddrive boot.

---

### Post by pesach on 2006-09-12
Is there anyone out there who can help me?

---

### Post by bodhi.zazen on 2006-09-12
I will try. You question makes no sense though.

What does it mean to > But when Ubuntu was installed I was not able to boot from the hard drive.

but then you say> The BIOS setting were set to harddrive boot.

Is it that your system does not boot to HD despite changing BIOS? Or is it booting to CD? Or is it booting to Windows?

Details please.

---

### Post by pesach on 2006-09-13
This is a new computer that i built myself.
After installing Ubuntu, it prompted me to remove the cd and restart.  I removed the cd, and turned off the computer.  I turned it back on and changed the BIOS settings to 1.Hard drive 2.CD 3.empty(no third option(I have no floppy drive))When I tried to boot up however, It tried to boot from hard drive, failed, and prompted my to put the system cd in.  what do i do know?

---

### Post by bodhi.zazen on 2006-09-13
Boot the ubuntu CD and lets look at your system. Could be you need to install Grub.

---

### Post by pesach on 2006-09-13
The ubuntu cd is booted.  I am curently on the computer using the live cd boot.  tell me waht you what to know about the system.  The computer works great,but I cant take the cd out.

---

### Post by pesach on 2006-09-13
and I think grub is already installed, but im not sure. how do i find out?

---

### Post by catlett on 2006-09-13
Grub will be in your boot folder. Go to the top of your screen and enter into Places<Computer<Filesystem then open the boot folder. You will then see the grub folder. If it isn't there, it definately isn't installed. If it is, you want to look at the menu.lst and the device.map. All you want to check in the map is that all you hard drives are listed. The menu.lst is a bit more complicated but you want to make sure it has listings for booting Ubuntu. 
You can open the files with these commands and then post the contents if you aren't sure.
```
sudo gedit /boot/grub/menu.lst
```
```
sudo gedit /boot/grub/device.map
```Just be cautious, when you open them with that command you can erase the contents or overwrite the file etc. I just wanted to give them to you in case you have to edit the files later, you will know how to open them up for editing.

---

### Post by bodhi.zazen on 2006-09-13
> **pesach said:**
> and I think grub is already installed, but im not sure. how do i find out?

catlett's post is very good. The only thing is, if it is not already mounted, you need to mount your ubuntu partition.

Then look for a grub directory in /path_to/ubuntu/boot/grub. for example, if Ubuntu in on dev/hda1 mounted at /media/hda1 look for:

/media/hda1/boot/grub

To see your mounted partitions:
```
df -h
``` 

If grub is not installed post and we can help install it.

If it is let's try to install grub to the mbr and re-boot.

---

### Post by pesach on 2006-09-13
i checked and there is no grub installed, so what should i do to install it?

---

### Post by pesach on 2006-09-13
this is what i got when I put in "df -h"

Filesystem            Size  Used Avail Use% Mounted on
unionfs               844M  692M  153M  82% /
varrun                219M   80K  219M   1% /var/run
varlock               219M  4.0K  219M   1% /var/lock
udev                  219M  104K  219M   1% /dev
devshm                219M     0  219M   0% /dev/shm
lrm                   219M  7.4M  212M   4% /lib/modules/2.6.15-26-amd64-generic/volatile
tmpfs                 219M   16K  219M   1% /tmp

---

### Post by bodhi.zazen on 2006-09-13
Step 1. Your Ubuntu partition is not mounted. We need to mount it.

We need to mount it, do you know what partition you installed to? If not, use GParted to look at you partitions.

Then:```
sudo mkdir /mnt/ubuntu
sudo mount /dev/hdax /mnt/ubuntu
```

Where hdax is your Ubuntu partition (? hda1)

Now look to see if you have a grub directory in /mnt/ubuntu/boot
(ie /mnt/ubuntu/boot/grub).

Advise...

---

### Post by pesach on 2006-09-13
mayb if i don understand wat u just said i shouldnt be trying linux,  but I did not understand at all what I am supposed to do.

---

### Post by bodhi.zazen on 2006-09-13
Sorry. :redface:

Open a terminal and enter the commands I gave you in mu last post (in the box).

sudo will ask for a password. Use our login password. You will NOT see text on the screen as you type.

---

### Post by pesach on 2006-09-14
from the first line of code I get
mkdir: cannot create directory `/mnt/ubuntu': File exists
from the second line I get
mount: special device /dev/hdax does not exist
so that means what?

---

### Post by Timothy Butwinick on 2006-09-14
The "hdax" part is supposed to be changed to the name of your system partition on your hard drive:

Write the following in a terminal window:
```
sudo gparted
```

You will see a new window with a list of the partitions:

```
Partition            Filesystem
/dev/hda1            ext3
/dev/hda2            ext2
/dev/hda3            swap
...
free space

```

The name of your partition should be next to the entry with the filesystem "etx3" or "ext2". *Presumably* it is "hda1", but it could also be "hda2".

Then you write (in terminal):

```
sudo mkdir /mnt/ubuntu2
sudo mount /dev/YOUR_PARTITION_HERE /mnt/ubuntu2
```

Replace "YOUR_PARTITION_HERE" with the name.

---

### Post by bodhi.zazen on 2006-09-14
Nice post.

You can get the same info from the CLI:

```
fdisk -l
```
(That is a small "L" not the number 1.)

---

### Post by pesach on 2006-09-14
i tried both of your suggestions.  With Timothy, the partition window came up, but when I put the second part of code in nothing happened.\
With Bodhi, when I put that code in nothing happened either.  And what does this have to do with installing grub?
Currently, I can not use my computer without the cd in the drive and this is getting really annoying.  If grub can fix it, Im all for it.  So since I think we established that I dont have grub installed (I think) then what should I do so it should be installed?
by the way, thanks for all the time and effort that you are putting in to help me. I appreciate it.

---

### Post by pesach on 2006-09-14
oh, and I got this when I put in the command "sudo gparted"
dumpe2fs 1.38 (30-Jun-2005)
Warning: Unable to open /dev/hdd read-write (Read-only file system).  /dev/hdd has been opened read-only.
Error: Unable to open /dev/hdd - unrecognised disk label.
And  the Ubuntu partition is in dev/hdc1 and filesystem ext3

---

### Post by bodhi.zazen on 2006-09-15
We are trying to identify you Ubuntu root partition.

Assuming it is ded/hdc1:

Open a terminal.

Type:```
sudo mount /dev/hdc1 /mnt/ubuntu
sudo grub
```

In the terminal you will now get a grub prompt:
grub>

At the grub prompt type:```
root (hd2,0)
setup (hd2)
quit
```

You will exit grub.

In the terminal type```
cat /mnt/ubuntu/boot/grub/menu.lst
```You should see text output to the screen. If you get an error message ("No such file or directory") STOP and re-post.

Otherwise re-boot....

---

### Post by Lakefall on 2006-09-15
> **pesach said:**
> oh, and I got this when I put in the command "sudo gparted"
dumpe2fs 1.38 (30-Jun-2005)
Warning: Unable to open /dev/hdd read-write (Read-only file system).  /dev/hdd has been opened read-only.
Error: Unable to open /dev/hdd - unrecognised disk label.
And  the Ubuntu partition is in dev/hdc1 and filesystem ext3
You said you built the system yourself. Have you done that before and to which sockets did you attach your hard drive and CD/DVD drive?

I too built a system some time ago and due to physical reasons caused by the location I chose for the hard drive and laziness I ended up connecting my DVD drive as a master to the first [PATA](http://en.wikipedia.org/wiki/AT_Attachment) socket (hda) and the hard drive as a master to the second PATA socket (hdc). Then I went on to install Ubuntu 5.10 on the system. I had rather serious issues, because the installer wanted to write portions of GRUB into my DVD drive, which obviously didn't work. Trying to use LILO instead didn't help. In the end I managed to work around the situation (without doing anything to the cables) and didn't file any bug reports, which I probably should have done. I have no idea if the installer of Ubuntu 6.06 is any better.. or worse. (GRUB is able to handle the situation when configured correctly, but the default installer wasn't able to configure it that way.)

It sounds like you have your hard drive as a master in the second PATA socket (hdc) and something else as a slave in the same socket (hdd), but possibly nothing in the first PATA socket. If you want things to "just work", I would advice you to put a normal hard drive to the first PATA socket as a master (hda). In your case the simplest solution may be to move the end of the cable on the motherboard from the second socket to the first and to install Ubuntu again.

---

### Post by pesach on 2006-09-15
here is what I got when I put in those commands ( the enire cod eis listed here)
```
buntu@ubuntu:~$ sudo mount /dev/hdc1 /mnt/ubuntu
mount: mount point /mnt/ubuntu does not exist
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd2,0)
root (hd2,0)

Error 21: Selected disk does not exist
grub> setup (hd2)
setup (hd2)

Error 12: Invalid device requested
grub> quit
quit
ubuntu@ubuntu:~$ cat /mnt/ubuntu/boot/grub/menu.1st
cat: /mnt/ubuntu/boot/grub/menu.1st: No such file or directory

```

---

### Post by pesach on 2006-09-15
> **Lakefall said:**
> You said you built the system yourself. Have you done that before and to which sockets did you attach your hard drive and CD/DVD drive?

This is the first computer I built and I put it in socket "1" (there is a socket "0")
I tried putting it in socket "0" and reinstalling, but this did not work.

---

### Post by bodhi.zazen on 2006-09-15
We need to install grub.

Run this:
[code]sudo mkdir /mnt/ubuntu
sudo mount /dev/hdc1 /mnt/ubuntu
sudo grub
grub> setup (hd2)[code]

Post /mnt/ubuntu/boot/grub/menu.lst

FYI: It may be easier to re-install Ubuntu. When you get to the part re install grub, install both to the MBR and root partition (use the back arrow keys after installing GRUB to hte MBR and re-install in root partition).

As has been pointed out, you should switch the phycisal connection of your HD and CDROM so your HD is recogniced as /dev/hda rather then /dev/hdc.

---

### Post by Lakefall on 2006-09-16
> **pesach said:**
> This is the first computer I built and I put it in socket "1" (there is a socket "0")
I tried putting it in socket "0" and reinstalling, but this did not work.
Make sure your hard drive shows up as hda now. Maybe it's something else, though. Do you get any errors or warnings during the install when it's installing GRUB?

(I haven't used any of the Ubuntu 6.06 installers, so I'm not the best person to tell anyone how they work. I'm not a GRUB expert either.)

---

### Post by pesach on 2006-09-16
Im currently reinstalling and nothing asks me about grub at all...
I also thought that grub is only for people that have also have windows on their hd

---

### Post by pesach on 2006-09-16
After reinstalling, I restarted and tried to reboot.  I had to boot from cd, but when I got to the opening page (where it says "start or install ubuntu", start ubuntu in safe grafics mode".....) I clicked on "boot from first  hard drive" after about 30 seconds I got this error message:
isolinux: disk error OS, AX=0000, drive 80
Is that progress? I mean, it is actually recognising there is linux on the drive...

---

### Post by Jukey on 2006-09-16
> **pesach said:**
> here is what I got when I put in those commands ( the enire cod eis listed here)
```
buntu@ubuntu:~$ sudo mount /dev/hdc1 /mnt/ubuntu
mount: mount point /mnt/ubuntu does not exist
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd2,0)
root (hd2,0)

Error 21: Selected disk does not exist
grub> setup (hd2)
setup (hd2)

Error 12: Invalid device requested
grub> quit
quit
ubuntu@ubuntu:~$ cat /mnt/ubuntu/boot/grub/menu.1st
cat: /mnt/ubuntu/boot/grub/menu.1st: No such file or directory

```



one problem might be that it says menu.1st instead of menu.lst

---

### Post by catlett on 2006-09-16
What is happening when you reboot after the install WITHOUT the cd in? If the installer worked correctly your computer should start booting. You will see a splash page of your computer maker, this is where you have the chance to enter the bios menu- usually. Then it will sau grub loading stage1.5...and finally the grub menu will appear with 3 selections. An ubuntu with a kernel number after it, an ubuntu with recovery mode and a 'memtest' selctionb for testing ram.
Does any of that happen when you boot without the cd. If not, what does happen?
Did you double click the installer icon on the desktop when you booted into the live cd? Did it ask you about partitioning your hard drive?
Something has gone wrong but it is hard to tell what you have or have not done and at what point the errors are coming up.
I guess start by describing what happens when you start your computer without the cd.

---

### Post by pesach on 2006-09-16
Jukey, I tried without the space and with an "l", but didnt help, same answer

---

### Post by pesach on 2006-09-16
ok. It did ask about partitioning the hard drive, and I hit "erase entire hard drive", and then next, and it showed me the list of settings I set it to ( language, time zone, keyboard, erase all hard drive) and i hit install. I was watching it, and during the entire installation procces nothing about grub came up.  After it was done, I hit restart.  Ubuntu closed down, and the only thing that came up as failed was RAID. ( this is kind of suprising because I dont think my mainboard  supports RAID, and if it does, I am definetly not using it.)  when the computer came back on the screen describing the mainboard came up(MSI V class k8mm-v) it said hit "tab" for post or "del" for boot settings.  I hit "del" so I could change it to boot from hard drive.  nothing about grub ever came up (this machine never had any other operating system on it) I changed it to boot from hard drive and started it up again.  It came back to the mainboard screen, and this time I hit "tab"( I know from experiance that even if I dont hit tab the same thing happens).  It went to the screen where it was detecting the IDE drives.  It had 
IDE 0 Master Hard drive
IDE 0 Slave  CD drive
IDE 1 Master empty
IDE 1 slave  empty
After is was done, it prompted me ti hit f1 to continue and and f11 for boot settings.  I had already configured the boot settings so I hit f1 It said something about BMI configuration (or something like that)  then said
"system boot failure insert system disk and press enter"
Having nothing to insert, I just pressed enter, and after 30 seconds, the same thing happened.  I restarted the computer, this time changing boot setting to include cd boot.  The BMI configuration thing came up again and after a while, it said boot from cd.( the cd was not in the drive) it told me to put the cd in the drive and press enter.  I did so, and the ubuntu screen came up (start or install ubuntu, startubuntu in safe graphics mod....) I hti boot from first hard disk ans this came up:
isolinux: disk error OS, AX=0000, drive 80
press any key to retry. I pressed a key, and the mainboard screen came up, the whole IDE checking thing came up again, and when the ubuntu screen came up, I just hit "start or install ubuntu"  ubuntu started up, with every thing starting OK, and it is currently working from the live cd.
The entire time nothing about grub came up

---

### Post by catlett on 2006-09-17
It appears the installation isn't happening. You can mount your drive and check it from the live cd but I would suggest another route.
I do not like the live cd. I prefer the Alternate Install cd. It is the old installer. It is texted based (you do not boot into a live session). It has a more in depth configuring of your system. You will not miss the installation of grub.
If you still have the desire to install ubuntu, try the alternate install cd. I wouldn't waste any more time with the live cd.
Download it here, [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/) scroll down past server install to alternate.

---

### Post by pesach on 2006-09-17
I made the alternate cd, put it in, same problem.  Nothing changed.  The thing is, I do not want to buy windows or try a diffrent os because how do I know it will work? Might just be a wiring problem.   sigh...

---

### Post by catlett on 2006-09-17
If you have a friend to help, that is great. In the meantime, you might want to try a different distro. DreamLinux is an easy install and is even faster because it runs xfce [http://www.dreamlinux.com.br/english/download.html](http://www.dreamlinux.com.br/english/download.html)
Or you might want to try Mandriva, it was the 'friendly' distro before Ubuntu came along. [http://www.mandriva.com/download](http://www.mandriva.com/download)

---

### Post by pesach on 2007-01-23
and after a long time of not using ubuntu I am happy to say that after replacing the mobo (another long story) ubuntu works PERFECTO!! thankx evey1 for ttryign to help:guitar:

---


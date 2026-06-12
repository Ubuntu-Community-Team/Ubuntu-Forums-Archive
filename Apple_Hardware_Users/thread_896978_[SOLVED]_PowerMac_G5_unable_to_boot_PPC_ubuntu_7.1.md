---
title: "[SOLVED] PowerMac G5 unable to boot PPC ubuntu 7.10"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by Chucklz15 on 2008-08-21
Hi all, I'm a bit new to the forums nad have a problem. I have a 2003 PowerMac G5 1.8 Dual Processor and was trying to install Ubuntu on it. When I put in the cd and hold the 'c' key it doesn't boot. So I go into the open-firmware and try the linux boot (boot cd:,\install\yaboot), sadly it doesn't work. I then try just the normal boot (boot cd) and it says LOAD-SIZE too small.

---

### Post by mrsteveman1 on 2008-08-21
Is this a shipit CD or one you burned?

---

### Post by Chucklz15 on 2008-08-21
It's one I burned, but when it varified it said it was successful.

---

### Post by tiresia on 2008-08-21
Why do you want to install Ubuntu 7.10?
I installed Hardy on my g5 and it works very well.
You can download it here:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
You can choose the LiveCD or the alternate installer, both should work.
Burn it with the Apple Disk Utility (if you have Mac OS X) at low speed.
At the first prompt hit TAB and choose the option nosplash-powerpc64

---

### Post by Chucklz15 on 2008-08-21
Thanks I'll try that tomarrow.

Chucklz

---

### Post by Chucklz15 on 2008-08-22
OK I've downloaded it and tried to load it and it still says that the load-size is too small. (in open-firmware)

---

### Post by Chucklz15 on 2008-08-22
OK, nevermind. I forgot to boot and hold the 'c' key :) Thanks everyone for your help.

---

### Post by Chucklz15 on 2008-08-22
OK now i need help. I was able to successfully install ubuntu 8.0 on my mac but when I try to boot, it has this dos like console that says "press 'l' to boot linux or press 'c' to boot cd". When I press 'l' it goes to the second bootstrap and then the question mark with the mac icon appears again. Sorry to be a bother again. :)

Chucklz

---

### Post by tiresia on 2008-08-22
Most probably is the configuration of yaboot not ok.
Start with your Installer-CD (if you used the alternate-CD choose at the first prompt the option rescue-powerpc64, if you used the Live-CD mount the HD where you installed Ubuntu just by choosing it in Places).
When you get a shell, or when you open a terminal, type in:```
cat /etc/yaboot.conf
```
You can post the result here.
Please tell us if you have on your g5 just Ubuntu, and where you installed it (/dev/sda3 maybe?)

---

### Post by LBC_Nut on 2008-08-22
I don't mean to hijack this thread but I'm having an identical problem on a PowerMac G4 (single 450 MHz CPU, dual 17.2 GB hard drives, and a stock ATI Rage128 video card) using ubuntu 7.04.  Everything about this machine is original from the factory with the obvious exception of the OS.  I expect the date of manufacture is ~2000, but can't say for sure.  As soon as the download completes, I will reinstall with 8.04 and provide the results of the above command.

While trying to solve this problem, Google searching led me to
[http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)

Which led me to [http://ubuntuforums.org/showthread.php?t=758301](http://ubuntuforums.org/showthread.php?t=758301)

I am afraid that I don't any prior experience with Linux or Unix and am not sure how to implement the patch recommended in post #8 if this is indeed the source of my pain.

---

### Post by maxi780 on 2008-08-22
Iam burned the cd but it's show the message "burnig are are not successful".please give me any information to correct the problem.
===================================================================
maxi

[Illinois Drug Addiction]("http://www.drugaddiction.net/illinois")

---

### Post by tiresia on 2008-08-23
[QUOTE=maxi780;5645856]Iam burned the cd but it's show the message "burnig are are not successful".please give me any information to correct the problem.
===================================================================
maxi

<Snip>Thread&#8230;:)
Wich software have you used to copy the CD-image?
Try at low speed!

---

### Post by Chucklz15 on 2008-08-23
> **tiresia said:**
> Most probably is the configuration of yaboot not ok.
Start with your Installer-CD (if you used the alternate-CD choose at the first prompt the option rescue-powerpc64, if you used the Live-CD mount the HD where you installed Ubuntu just by choosing it in Places).
When you get a shell, or when you open a terminal, type in:```
cat /etc/yaboot.conf
```
You can post the result here.
Please tell us if you have on your g5 just Ubuntu, and where you installed it (/dev/sda3 maybe?)

OK I have done that in the console after I have mounted the HD but it says that the directory cannot be found. Maybe I also need to specify a drive in the command.

---

### Post by Chucklz15 on 2008-08-23
OK I did some digging thinking that I can just navigate to the folder and I was right. Here is what was inside:```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/disk@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

---

### Post by tiresia on 2008-08-23
Ok, you may want to check the open firmware path of the boot-device
First of all back up your yaboot.conf
```
cp /etc/yaboot.conf /etc/yaboot.conf-backup
```
To determine the open firmware path of the boot-device
```
ofpath /dev/sda2
```
You should get something like:
/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:2 (it is just an example!!!)
Edit your yaboot.conf
```
sudo nano /etc/yaboot.conf
```
Insert the ofpath after "device". It should look something like this
(again, it is just an example!!!)
boot=/dev/sda2
**device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:2**
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

Save the changes (ctrl+X), say yes.

Run ```
sudo ybin -v 
```

Restart your computer

---

### Post by Chucklz15 on 2008-08-23
OK the info on the device was correct, but when I do the last command I get this:
```
ubuntu@ubuntu:~$ ybin -v
ybin: Warning: no /etc/yaboot.conf, running yabootconfig to make one
yabootconfig: You are not root, go away
ybin: yabootconfig failed, please supply a valid /etc/yaboot.conf
ybin: You may also use ybin's --boot, --image, --partition, and --device switches
ybin: These switches will cause ybin to generate a basic yaboot.conf on the fly
ubuntu@ubuntu:~$ 

```

When I do the "ofpath /dev/sda2" command It just shows /disk@0:2.

---

### Post by tiresia on 2008-08-23
Sorry, I have forgotten to tell you to run ybin with sudo.
After you changed and saved yaboot.conf, run```
sudo ybin -v
```

---

### Post by Chucklz15 on 2008-08-23
OK now I get this:
```
ubuntu@ubuntu:~$ sudo ybin -v
ybin: Warning: no /etc/yaboot.conf, running yabootconfig to make one
yabootconfig: unionfs: No such file or directory
ybin: yabootconfig failed, please supply a valid /etc/yaboot.conf
ybin: You may also use ybin's --boot, --image, --partition, and --device switches
ybin: These switches will cause ybin to generate a basic yaboot.conf on the fly
ubuntu@ubuntu:~$ 

```

It's almost like it cannot find the yaboot.conf or something.

---

### Post by tiresia on 2008-08-23
You must mount the device (as you have done before, when you used cat /etc/yaboot)!

---

### Post by Chucklz15 on 2008-08-23
How? In the console? I already mounted it (by clicking on it in places).

---

### Post by tiresia on 2008-08-23
Can you please just run```
ls /etc
``` and tell us if you find your yaboot.conf

---

### Post by Chucklz15 on 2008-08-23
It's not there, it might be looking in only the CD-ROM (called "File System") not the actual hard disk.

---

### Post by tiresia on 2008-08-23
I'm sorry, another mistake! Yes, of course, your HD is on /media.
Therefore, the file you must edit is also in /media/yourHD/etc/yaboot.conf

---

### Post by Chucklz15 on 2008-08-23
I did and did the ybin thing again and it says this:
```
ubuntu@ubuntu:~$ sudo ybin
ybin: Warning: no /etc/yaboot.conf, running yabootconfig to make one
yabootconfig: unionfs: No such file or directory
ybin: yabootconfig failed, please supply a valid /etc/yaboot.conf
ybin: You may also use ybin's --boot, --image, --partition, and --device switches
ybin: These switches will cause ybin to generate a basic yaboot.conf on the fly
ubuntu@ubuntu:~$ 

```

---

### Post by Chucklz15 on 2008-08-23
Maybe I need to tell it to look for the yaboot.conf in my drive rather than the one in the directory that they are trying to look for. The thing is I don't know how to do that.

---

### Post by tiresia on 2008-08-24
Let's recapitulate what you have done.
I assume that your Bootstrap Partition (where Yaboot is) is on /dev/sda2, and Ubuntu is on /dev/sda3, whose name is 'disk'

1. Start from the LiveCD

2. Mount the Ubuntu Partition ('disk') on /media (just by selecting it in the Menu Places)

3. Find the OpenFirmware Path of your Boostrap Partition (/dev/sda2) with```
ofpath /dev/sda2
```

4. Edit the yaboot.conf of the Ubuntu partition, in order to add the OpenFirmware Path (device=)
```
sudo nano /media/disk/etc/yaboot.conf
```
Save the file

5. Now you must run ybin
```
sudo ybin -v -b /dev/sda2 -C /media/disk/etc/yaboot.conf
```


P.S. Do not mount /dev/sda2, otherwise ybin will not run
Do you want to install also MacOSX on your G5?

---

### Post by Chucklz15 on 2008-08-24
Thats what I've been trying to do (but just install Mac OS X, not both). But the disk my friend gave me was no good (it was a backup or something) do you know where I can get a free copy or at leat a cheap one?

P.S. I don't know what you mean by the /dev/sda2, and /dev/sda3...I think that /dev/sda2 is my HD, I don't know. I just use the /media/disk but maybe I should try the /dev/sda3.

---

### Post by Chucklz15 on 2008-08-24
OK I did the last code you posted with the ybin (I was trying to figure out how to tell it to look there) and here is what it said:
```
ubuntu@ubuntu:~$ sudo ybin -v -b /dev/sda2 -C /media/disk/etc/yaboot.conf
ybin: Finding OpenFirmware device path to `/dev/sda2'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda2...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda2...
ybin: Installing /media/disk/etc/yaboot.conf onto /dev/sda2...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda2 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
ubuntu@ubuntu:~$ 

```

---

### Post by sayad on 2008-08-24
load size small is teeh meesseege given when the ram is not able to completely take up the data , that is is the laod size requirees more than 128 mb per second , when your 128 ram cannot take in 128 mb per sond , then the messege appears ' load size small "
I have learned that bit of information cause i never faced this problem , but i had problem that my screen suddenly went blue with some error scripts , thats when my vendor said thir is problem with mmy ram.

---

### Post by tiresia on 2008-08-24
> **Chucklz15 said:**
> 
I don't know what you mean by the /dev/sda2, and /dev/sda3...I think that /dev/sda2 is my HD, I don't know. I just use the /media/disk but maybe I should try the /dev/sda3.

You have one hard disk. For Linux, it is a device (therefore /dev), its name is sda (if you had two hard disks the second hd would be sdb), and you have several partitions on it (sda1, sda2, sda3, and so on&#8230;)

When you install a Linux distro on a PowerPc Mac, usually you have at least four partitions on a hd:

1. /dev/sda1 Apple_partition_map
2. /dev/sda2 Apple Bootstrap (where yaboot, the bootloader is)
3. /dev/sda3 Linux (here Ubuntu)
4. /dev/sda4 Swap Partition

If you run fdisk -l /dev/sda, you should see a similar situation.

In order to access these partitions, you must mount the file system on it.
When you start your computer from a Ubuntu-LiveCD, Ubuntu mount a FileSystem on /media (with the name disk, disk1, disk2, and so on).

Please try to do just what I wrote in the post before. At least you can access your ubuntu system. 

If you want to install MacOSX, you should do it *before* installing Linux. But we can try to find a solution for it, when you are done with the Ubuntu installation. 
Have you already tried to boot the MacOs Installer-DVD, that you have (pressing C at boot)? When you are done, we can check this DVD, and maybe try to make it bootable if it is not.

---

### Post by tiresia on 2008-08-24
> **Chucklz15 said:**
> OK I did the last code you posted with the ybin (I was trying to figure out how to tell it to look there) and here is what it said:
```
ubuntu@ubuntu:~$ sudo ybin -v -b /dev/sda2 -C /media/disk/etc/yaboot.conf
ybin: Finding OpenFirmware device path to `/dev/sda2'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda2...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda2...
ybin: Installing /media/disk/etc/yaboot.conf onto /dev/sda2...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda2 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...
ubuntu@ubuntu:~$ 

```
Well, you are done, try to restart your computer

---

### Post by Chucklz15 on 2008-08-24
OK, I restarted and still no dice. It still starts the first stage bootstrap, I press 'l' and then it starts second stage bootstrap, then it has the mac symbol and question mark thing appear, I think we just reset the first stage bootstrap, not the second one (which we need to somehow fix).

---

### Post by tiresia on 2008-08-24
Can you please check all the steps I listed in the post #25?
Please check again the ofpath and be sure that you edit the file adding the correct ofpath. Can you please post the result of
```
cat /media/disk/etc/yaboot.conf
```

---

### Post by Chucklz15 on 2008-08-24
Here (I even added the ofpath command to see if I put it in right):
```
ubuntu@ubuntu:~$ ofpath /dev/sda2
/disk@0:2
ubuntu@ubuntu:~$ cat /media/disk/etc/yaboot.conf
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/disk@0:2
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
ubuntu@ubuntu:~$ 
```

---

### Post by tiresia on 2008-08-24
Ok, the OpenFirmware Path you found with ofpath is not correct, because this command has a bug!!! Here is a link, where you can find more:
[http://ubuntuforums.org/showthread.php?t=758301](http://ubuntuforums.org/showthread.php?t=758301)

Well, it is not so 'canonical', but you can try with this path (maybe we are lucky... add it to your yaboot.conf)
```
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0
```

After that, run again ybin as you did before

```
sudo ybin -v -b /dev/sda2 -C /media/disk/etc/yaboot.conf
```

Restart your computer after that.

---

### Post by Chucklz15 on 2008-08-24
So do you want me to replace the other ofpath or run this one somehow or what (how do you run it in the console without it being in the etc folder?)

P.S. I just tried your "device= %whatever%" and when I tried to boot (by pressing 'l') it did the little question mark and mac os symbol then it started to boot from cd-drive. I also read the post you lead me to, and I don't get it (I know that there is a bug and that there is a new version out). But I don't know what to do with it. I can't replace the old one because I don't have the permission (unless I do it with the console which I don't know how to do) nad I cant run it just on the desktop with root permissions.

---

### Post by tiresia on 2008-08-24
I was suggesting to try adding that openfirmware path to the your yaboot.conf.
But, since it is not so 'canonical' as I sad before, let's try another safer way(you must be a little patient...):popcorn:

Start your computer again and press immediately this four keys cmd+opt+O+F in order to access Open Firmware.
At the prompt run```
devalias
```
You will see a list of all your devices and their open firmware path.
You must look for 'hd' (it is the alias for your hard disk) and its path.
It should be something like:
'device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0'
Note it (please pay attention to each details), 
and run ```
boot
``` to start again the computer. 
Press C to start from your ubuntu LiveCD and post the OpenFirmware Path  to us.

---

### Post by Chucklz15 on 2008-08-24
OH, now it makes sense, one second...

UPDATE: OK its:

/ht/pci@7/k2-sata-root/k2-sata@0/disk@0

---

### Post by tiresia on 2008-08-24
1. Mount your Ubuntu-HD (just choose your HD in Places)
2. Edit the yaboot.conf 

```
sudo nano /media/disk/etc/yaboot.conf
```

After device add the open firmware path. it should look like this
```
boot=/dev/sda2
**device=/ht/pci@7/k2-sata-root/k2-sata@0/disk@0**
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
```

Exit and save the file

Run again ybin as before

```
sudo ybin -v -b /dev/sda2 -C /media/disk/etc/yaboot.conf
```

Restart the computer

---

### Post by Chucklz15 on 2008-08-24
Still doesn't work, even after doing to the OpenFirmware to get the hard disk's thing.

---

### Post by tiresia on 2008-08-24
Are you sure that you copied the OF Path correctly?

Try to add to /media/disk/etc/yaboot.conf these two solutions, repeating the same process as before (run always ybin!)

First solution:
device=/ht/pci@7/k2-sata-root/k2-sata@0/disk@0:
(run ybin as shown above and restart your computer)


Second solution:
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
(run ybin as shown above and restart your computer)

---

### Post by Chucklz15 on 2008-08-24
None of them work.

---

### Post by tiresia on 2008-08-24
It sounds frustrating... I'm afraid that because of the mentioned bug we can't install a working yaboot. You may want trying the alternate install CD.
Here is the link:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
Check it after downloading and burn at low speed.
Let me know, if it works!

---

### Post by Chucklz15 on 2008-08-24
OK, I will try what you just suggested, but I think I have solved the problem. I know that there is a bug in the ofpath command and that there is a patch for it. But I cannot use the patch because of permission problems. I was hoping that you could supply a command that lets me replace the current ofpath from my drive with the one that I downloaded form this thread: [http://ubuntuforums.org/showthread.php?t=758301]("http://ubuntuforums.org/showthread.php?t=758301") (page 1 from user "pxwpxw", link at end of his reply "ofpath.gz") Thanks for your help.

---

### Post by tiresia on 2008-08-24
I wanted to suggest you to do what you are right now trying to do, but I was afraid it is a bit annoying. Can you tell me, how are you triying to apply the patch?

---

### Post by Chucklz15 on 2008-08-24
First off, nobody that I talk to for help has ever been annoying and why should you be if your helping me with my most hardest problem. Secondly I'm trying to replace the other ofpath with the patch one by just rewriting it. But I always get the "you do not have the correct permissions" pop-up. I was trying to do a copy command in the terminal but I don't know how (I'm only Windows savy).

Thanks

---

### Post by tiresia on 2008-08-24
Every command that changes your System must be run as 'super user'
Therefore you must use 'sudo cp'

If downloaded the ofpath.gz on your Desktop run
```
zcat Desktop/ofpath.gz > Desktop/ofpath
```
To copy that command
```
 sudo cp Desktop/ofpath /media/disk/usr/sbin/ofpath
```

Then you can try to use it, in order to get the right Open Firmware Path
```
/media/disk/usr/sbin/ofpath /dev/sda2
```

Anyway, at this point you must really use the alternate install CD and at the prompt select the 'rescue option' (you do not need to install everything again!)
Then, when you are in your Ubuntu installed System, edit the /etc/yaboot.conf with the (correct) Open Firmware Path you got.
Run ybin.

---

### Post by Chucklz15 on 2008-08-24
OK, I've copied the patched ofpath the the dir of my old one and still doesn't work. Now I'm trying the alternate disc.

---

### Post by tiresia on 2008-08-24
I added some informations in the post #46.

---

### Post by Chucklz15 on 2008-08-24
OK, so I've replaced the ofpath with the instructions and the other patch that you gave me and when I ran the command it said the drive's full name (/ht/pci...disk@0). I put it into the yaboot.conf file and ran ybin. I restarted and it still doesn't work. Although now the ofpath is fixed so that's soething positive. But it's still not booting right. I think you said something about a bootstrap update (from 1.13.13 to 1.13.14 or something like that). Maybe that is what we need to do.

Thanks

---

### Post by tiresia on 2008-08-25
The problem is that when you run ybin from the Live-CD, ybin runs again the 'ofpath'  command that it finds on the Live-CD (and that is buggy).
Therefore you got now a working ofpath, but you need to start it from inside the installed Ubuntu System. It means, that you need to change your Root Directory. 
The easiest way  is to download the Alternate install CD.
Here is the link (burn it at low speed!)
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

When you start (pressing C) your computer, at the prompt hit TAB
You will see several options. Choose:
'rescue-powerpc64'
After that you need to give some informations (it's extremely easy and faster then the Live-CD).

When you get to the question 'which device you want to use as root file system', choose /dev/sda3 (is where your Ubuntu System is).
 
You will get another question with several options, among them if you want:
1. to execute a shell in /dev/sda3
2. (ignore this one)
3. to install yaboot

Try first the third solution. If you are lucky, is  the ofpath of the alternate install CD not so buggy as that one of the Live-CD and you will get a working Yaboot install on /dev/sda2.
Restart the computer and wait for yaboot.

If it doesn't work, get again to the same point like before, and choose the option:
execute a shell in /dev/sda3
At the prompt 
check again that your /etc/yaboot.conf is OK. Run again:
```
ofpath /dev/sda2
```
```
cat /etc/yaboot.conf
```
and
```
ybin -v -b /dev/sdb2 -C /etc/yaboot.conf
``` 
(probably you do not need to specify these options, but let's be sure…)
Now you can start again your computer.
--
Can you please tell me if the open firmware path you get with the patched 'ofpath' is  the same you got when you started with the Open Firmware.
Let me know how it works, so we can try to solve the problem with OSX

---

### Post by pxwpxw on 2008-08-25
The easiest way is to use your
option 1. to execute a shell in /dev/sda3 the installed ubuntu.
Then, if you have the good /usr/sbin/ofpath still intact in sda3
and you NewWorld bootstrap partition still exists, just run
```

 yabootconfig --debug

``` 
from /dev/sda3,
that will rewrite yaboot.conf and the boot files all in one go,
and it should restart correctly.

If you take option 3, it will re-install the yaboot package and overwrite ofpath, and you are back to the start of the problem.

The other way was to put ofpath (pxw) on a usb stick and do the fixup in the initial install after the first part of the yaboot install, before ofpath is used by the installer, but that can be tricky.

---

### Post by tiresia on 2008-08-25
> **pxwpxw said:**
> If you take option 3, it will re-install the yaboot package and overwrite ofpath, and you are back to the start of the problem.

Thanks pxwpxw, yes, you are right. I have read your useful post as well 
[http://ubuntuforums.org/showthread.php?t=896978&page=4](http://ubuntuforums.org/showthread.php?t=896978&page=4)
I tought that the alternate install cd could manage to find the right open firmware path.
(I know it not logic… But on the other hand is it logic that ofpath works well in several situations (for me it is ok) and it fails in other similar ones? :confused: )

---

### Post by pxwpxw on 2008-08-25
It depends on the apple model and the drive type, works fine for internal ide drive on ibook g4, not so for external or sata on some g5. All the ubuntu distros use the same version ofpath (buggy). The whole problem can be fixed by the revision when included in the yaboot package. Support the bug report if you agree.
[https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607)

---

### Post by Chucklz15 on 2008-08-25
OK so I did the 1st option and did the yabootconfig --debug and now restarting (I did notice the last line after I ran the yabootconfig, I said "unable to determine OpenFirmware device name to /dev/disk/by-uuid/cbf, aborting..."). I don't know what this means but I will still try.

UPDATE: I finished restarting and still didn't work, when I exited the rescue disk there was a message box and it stated that the kernal in device /dev/sda3 loaded but had errors running, I will try again to see it it can fix itself.

UPDATE_2: I retried the rescue disk but the same thing happened, now what? 

Thanks

---

### Post by tiresia on 2008-08-25
Can you please start again from your live-CD and do following:
```
sudo mount /dev/sda2 /mnt
```
Please, post me what you get from
```
cat /mnt/yaboot.conf
```

---

### Post by Chucklz15 on 2008-08-25
OK here:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ cat /mnt/yaboot.conf
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0:2
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
ubuntu@ubuntu:~$ 

```

---

### Post by tiresia on 2008-08-25
Ok, I think it is missed up. 
Anyway I would like to try following.
Restart your computer and stop it at the Open Firmware (cmd+alt+o+f)
The alias for your HD (coorisponding to '/ht/pci@7/k2-sata-root/k2-sata@0/disk@0') is 'hd', right?
 
If so, try first just
```
boot hd:,\\:tbxi
```

If it does not work, try:
```
boot hd/disk@0:2,\\:tbxi
```

Tell ma, please, what happens in both situations

---

### Post by Chucklz15 on 2008-08-25
Situation 1: can't OPEN hd:,\\tbxi
Situation 2: can't OPEN hd/disk@0:2,\\:tbxi

---

### Post by tiresia on 2008-08-25
Just a question, before telling you my next proposal.
How many Hard Disks do you have?
Mac OS X is not yet installed, right?

---

### Post by Chucklz15 on 2008-08-25
I only have one 320GB SATA disk installed on my computer and I would like to have Mac OS X on my computer, but I do not.

---

### Post by tiresia on 2008-08-25
Boot from your LiveCD (again...)
Mount your Ubuntu partition selecting it in 'Places'

Mount the proc, sys and dev file systems inside your Ubuntu install
```
sudo mount -t proc none /mnt/media/disk/proc
sudo mount -o bind /dev /mnt/media/disk/dev
sudo mount -o bind /sys /mnt/media/disk/sys
```

Chroot into your Ubuntu system:
```
sudo chroot /media/disk /bin/bash
```

Tell me what you get from
```
ls -l
cat /etc/yaboot.conf
ofpath /dev/sda2
```

---

### Post by Chucklz15 on 2008-08-25
First three:
```
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/media/disk/proc
mount: mount point /mnt/media/disk/proc does not exist
ubuntu@ubuntu:~$ sudo mount -o blind /dev /mnt/media/disk/dev
mount: mount point /mnt/media/disk/dev does not exist
ubuntu@ubuntu:~$ sudo mount -o blind /dev /mnt/media/disk/sys
mount: mount point /mnt/media/disk/sys does not exist
ubuntu@ubuntu:~$ 

```

Third set (1 of 3):
```
ubuntu@ubuntu:~$ sudo chroot /media/disk /bin/bash
root@ubuntu:/# ls -l
total 96
drwxr-xr-x   2 root root  4096 2008-08-24 19:08 bin
drwxr-xr-x   2 root root  4096 2008-08-24 19:30 boot
lrwxrwxrwx   1 root root    11 2008-08-24 18:54 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-08-24 19:33 dev
drwxr-xr-x 117 root root 12288 2008-08-25 08:27 etc
drwxr-xr-x   3 root root  4096 2008-08-24 19:30 home
drwxr-xr-x   2 root root  4096 2008-08-24 18:56 initrd
drwxr-xr-x  14 root root  4096 2008-08-24 19:12 lib
drwx------   2 root root 16384 2008-08-24 18:54 lost+found
drwxr-xr-x   3 root root  4096 2008-08-24 18:54 media
drwxr-xr-x   2 root root  4096 2008-06-13 12:07 mnt
drwxr-xr-x   2 root root  4096 2008-08-24 18:56 opt
drwxr-xr-x   2 root root  4096 2008-06-13 12:07 proc
drwxr-xr-x   3 root root  4096 2008-08-24 19:17 root
drwxr-xr-x   2 root root  4096 2008-08-24 19:30 sbin
drwxr-xr-x   2 root root  4096 2008-08-24 18:56 srv
drwxr-xr-x   2 root root  4096 2008-04-18 12:02 sys
drwxrwxrwt   2 root root  4096 2008-08-24 19:30 tmp
drwxr-xr-x  11 root root  4096 2008-08-24 20:50 usr
drwxr-xr-x  15 root root  4096 2008-08-24 19:21 var
root@ubuntu:/# 

```

2 of 3:
```
root@ubuntu:/# cat /etc/yaboot.conf
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0:2
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
root@ubuntu:/# 

```

3 of 3:
```
root@ubuntu:/# ofpath /dev/sda2
/usr/sbin/ofpath: 160: cannot create /dev/null: Permission denied
ofpath: /dev/sda2: No such file or directory
root@ubuntu:/# 

```

UPDATE!!! (well not really): I was wondering I you could take control of my computer or something to help me do what needs to be done, or at least watch it and then tell me (guiding).

---

### Post by tiresia on 2008-08-25
Sorry, I made a mistake (I'm not used to mount a disk on /media).
Please, run 
```
exit
```
and do again

Mount the proc, sys and dev file systems inside your Ubuntu install
```
sudo mount -t proc none /media/disk/proc
sudo mount -o bind /dev /media/disk/dev
sudo mount -o bind /sys /media/disk/sys
```

Chroot into your Ubuntu system:
```
sudo chroot /media/disk /bin/bash
```

Tell me what you get from
```
ofpath /dev/sda2
```

---

### Post by cyberdork33 on 2008-08-25
> **Chucklz15 said:**
> First three:
```
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/media/disk/proc
mount: mount point /mnt/media/disk/proc does not exist
ubuntu@ubuntu:~$ sudo mount -o blind /dev /mnt/media/disk/dev
mount: mount point /mnt/media/disk/dev does not exist
ubuntu@ubuntu:~$ sudo mount -o blind /dev /mnt/media/disk/sys
mount: mount point /mnt/media/disk/sys does not exist
ubuntu@ubuntu:~$ 

```
there was a typo. you should be mounting to /media/disk/whatever instead of /mnt/media/disk/whatever

EDIT. Beat me to it.

---

### Post by Chucklz15 on 2008-08-25
Pre-note, UPDATE in my last post.

Ok now here:
```
ubuntu@ubuntu:~$ sudo mount -t proc none /media/disk/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /media/disk/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev /media/disk/sys
ubuntu@ubuntu:~$ sudo chroot /media/disk /bin/bash
root@ubuntu:/# ofpath /dev/sda2
/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0:2
root@ubuntu:/# 

```

---

### Post by tiresia on 2008-08-25
> **Chucklz15 said:**
> 
UPDATE!!! (well not really): I was wondering I you could take control of my computer or something to help me do what needs to be done, or at least watch it and then tell me (guiding).

No, I can't (and it would not be safe for you...)
Anyway, I hope we get soon a good answer from it

---

### Post by tiresia on 2008-08-25
Ok, run now```
yabootconfig --debug
``` and tell me what you get

---

### Post by Chucklz15 on 2008-08-25
LOL!!!!, I love linux (top line):
```

ubuntu@ubuntu:~$ yabootconfig --debug
yabootconfig: You are not root, go away
ubuntu@ubuntu:~$ sudo yabootconfig --debug
yabootconfig: DEBUG: ROOT=unionfs
yabootconfig: unionfs: No such file or directory
ubuntu@ubuntu:~$ sudo chroot /media/disk /bin/bash
root@ubuntu:/# yabootconfig --debug
yabootconfig: DEBUG: ROOT=UUID=cbf5c1ce-4fd7-4862-b096-2efd33909a00
yabootconfig: DEBUG: mac-fdisk is: mac-fdisk
yabootconfig: DEBUG: BOOT=/dev/sda2
yaboot is the Linux Loader for PowerPC.  yabootconfig sets up your system to boot directly
from your hard disk, without the need for a boot CD, floppy or a network boot.
Install yaboot bootstrap on /dev/sda2 to boot Linux from /dev/sda3? [Yes] 
Creating a simple /etc/yaboot.conf...
yabootconfig: DEBUG: KERNEL=/boot/vmlinux
yabootconfig: DEBUG: INITRD=/boot/initrd.img
yabootconfig: DEBUG: KERNEL=/boot/vmlinux
KERNDEV=/dev/disk/by-uuid/cbf5c1ce-4fd7-4862-b096-2efd33909a00
KERNDIR=/dev/disk/by-uuid/cbf5c1ce-4fd7-4862-b096-2efd33909a00
LINKDEV=/dev/disk/by-uuid/cbf5c1ce-4fd7-4862-b096-2efd33909a00
PARTITION=00
KERNELDISK=/dev/disk/by-uuid/cbf
yabootconfig: DEBUG: INITRD=/boot/initrd.img
IRDDEV=/dev/disk/by-uuid/cbf5c1ce-4fd7-4862-b096-2efd33909a00
IRDDIR=/dev/disk/by-uuid/cbf5c1ce-4fd7-4862-b096-2efd33909a00
IRDLINKDEV=/dev/disk/by-uuid/cbf5c1ce-4fd7-4862-b096-2efd33909a00
IRDPARTITION=00
INITRDDISK=/dev/disk/by-uuid/cbf
ofpath: /dev/disk/by-uuid/cbf: No such file or directory
yabootconfig: Unable to determine OpenFirmware device name to /dev/disk/by-uuid/cbf, aborting...
root@ubuntu:/# 

```

---

### Post by tiresia on 2008-08-25
Well, I'm not sure, if it works. Anyway, run 
```
exit
umount /media/disk/proc
umount /media/disk/sys
umount /media/disk/dev
umount /media/disk/

```

Restart and try...

---

### Post by Chucklz15 on 2008-08-25
Well all of them were not found anyway, and I think that matters.

---

### Post by tiresia on 2008-08-25
If you didn't restart, can you please tell me, what you see in :
```
ls /dev/disk
```

---

### Post by Chucklz15 on 2008-08-25
```

root@ubuntu:/# ls /dev/disk
by-id  by-label  by-path  by-uuid
root@ubuntu:/#

```

I'm going to have to finish this (I hope), a bit later. Going somewhere and will be back in about 4 hours.

---

### Post by tiresia on 2008-08-25
Ok, I go soon to sleep (I live in Berlin...)
My two last suggestions (for today): run, from the chrooted Ubuntu 
```
mkofboot -v
```
and post it here.
If it should work umount everything, as explained before, and restart.


Second option:
If you can't yet boot, try again from Open Firmware (comd+opt+o+f) with following (please, note the difference 0 and 1) :

```
boot /ht/pci@7/k2-sata-root/**k2-sata@0**/disk@0:2,\yaboot
```
or
```
boot /ht/pci@7/k2-sata-root/**k2-sata@1**/disk@0:2,\yaboot
```
or
```
/ht@0,f2000000/pci@7/**k2-sata-root@c**/**k2-sata@0**/disk@0:2,\yaboot
```
or
```
/ht@0,f2000000/pci@7/**k2-sata-root@c**/**k2-sata@1**/disk@0:2,\yaboot
```

---

### Post by pxwpxw on 2008-08-26
If you want to pursue the yabootconfig way:

/dev/disk/by-uuid numbers should point to device names like this (for this box)
```

admax@g4:~/forum$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-08-26 12:51 700bb606-55d1-4229-b211-556bd53b7079 -> ../../hda4
lrwxrwxrwx 1 root root 10 2008-08-26 12:51 938093c7-954e-4d28-bf0d-f6d0b88133d0 -> ../../hda6
lrwxrwxrwx 1 root root 10 2008-08-26 12:51 96826303-77b7-48b6-b5cd-bb97015e4fa7 -> ../../hda9
lrwxrwxrwx 1 root root 10 2008-08-26 12:51 a4e24732-e321-491f-897c-6c687441d856 -> ../../hda8
lrwxrwxrwx 1 root root 10 2008-08-26 12:51 c7d01fd4-6dc7-4ade-ad2f-b866d13d3cf2 -> ../../hda7
lrwxrwxrwx 1 root root 10 2008-08-26 12:51 CF127CED1089211F -> ../../hda3

```

The by-uuid names should be links pointing to the sda partitions, but yabootconfig and ofpath are trying to interpret the uuid name (got from fstab) as device names which they need.

If there is some problem there, then an option is to give yabooconfig the bootstrap and root device name. 

For example, (In your case -b /dev/sda2 -r /dev/sda3 I think)
I ran this as --noinstall for a test.

This would be done finally from the  <chroot>/ with /proc /sys and /dev mounted as you have done.

```
 
admax@g4:~$ sudo yabootconfig -b /dev/hda2 -r /dev/hda6 --noinstall --debug
yaboot is the Linux Loader for PowerPC.  yabootconfig sets up your system to boot directly
from your hard disk, without the need for a boot CD, floppy or a network boot.
Create simple /etc/yaboot.conf to boot Linux from /dev/hda6? [Yes] y
Creating a simple /etc/yaboot.conf...
yabootconfig: DEBUG: KERNEL=/boot/vmlinux
yabootconfig: DEBUG: INITRD=/boot/initrd.img
yabootconfig: DEBUG: KERNEL=/boot/vmlinux
KERNDEV=/dev/hda6
KERNDIR=/
LINKDEV=/dev/hda6
PARTITION=6
KERNELDISK=/dev/hda
yabootconfig: DEBUG: INITRD=/boot/initrd.img
IRDDEV=/dev/hda6
IRDDIR=/
IRDLINKDEV=/dev/hda6
IRDPARTITION=6
INITRDDISK=/dev/hda
admax@g4:~$ 

```

---

### Post by Chucklz15 on 2008-08-26
And thats it, just run that command with the --noinstall? Or should I try tiresia's 4 solutions first?

UPDATE - IMPORTANT!!!: I did the ls -l /dev/disk/by-uuid command and this is what I got (I noticed that it didn't do sda2!!!!):

```

ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-08-26 10:33 1895efdd-f1bb-4be9-9073-d78878492ae6 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-08-26 10:33 cbf5c1ce-4fd7-4862-b096-2efd33909a00 -> ../../sda3
ubuntu@ubuntu:~$ 

```

---

### Post by tiresia on 2008-08-26
Hi Chucklz,

please, before trying my suggestiongs, try what pxwpxw suggests (me too i think is right)
You must be in the chrooted ubuntu (with /dev, /proc and /sys mounted)

```
sudo yabootconfig -v -b /dev/sda2 -r /dev/sda3
```

Please, tell me what you get.
If it doesn't work try my other solutions

---

### Post by Chucklz15 on 2008-08-26
BINGO, YES!!! Your second solution seemed to have worked and I think I know why. I was looking around inside my computer and I noticed where my hard disk was located. It was in slot B, meaning slave, so in your second solution when you said "...sata@1..." it meant slave. Thanks everyone for your help.

---

### Post by tiresia on 2008-08-26
Right, I tought yesterday the same (because the patched ofpath gave a different path than that one you found days ago in the OpenFirmware - you have in fact seen the HD in slot A).
Now, from inside your new Ubuntu, you should anyway run (just to check that the command gives the same path that you used to boot)
```
 ofpath /dev/sda2
```

and install a correct Yaboot

```
sudo yabootconfig -b /dev/sda2 -r /dev/sda3 --debug
```

Please, if your g5 is now ok, mark the thread as solved
:)

---

### Post by Chucklz15 on 2008-08-26
How do I do that exactly?

UPDATE: Everything matchs what I booted with and the yabootconfig is working.

---

### Post by cyberdork33 on 2008-08-26
> **Chucklz15 said:**
> How do I do that exactly?
See the "thread tools" menu at the top.

---


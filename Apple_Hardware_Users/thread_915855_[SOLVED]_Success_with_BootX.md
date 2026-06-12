---
title: "[SOLVED] Success with BootX?"
date: 2008-09-10
forum: Apple Hardware Users
---

### Post by Bikerbob on 2008-09-10
I would like to get Xubuntu installed on a 9600 with G3.

If I use the kernel and image from 7.04 alternate cd I get most of the way through the boot with the bootX app, but it crashes. If I go to linux durring full boot, the extention .. I get into the install program, but.. it will not detect my scsi cdrom drive. Now is this something that the 7.04 maybe has done away with? so maybe I need to go back further?

James

>  Re: Installing Xubuntu on a OLD World Mac
I had the same problem trying to install 8.04 Beta and the 7.10 would ended up going to the "busy box". I reinstalled Feisty 7.04 with the alternate CD installer and it worked fine. Stick with a 7.04 alternate CD for PPC. Burn the ISO to the slowest setting you can.

[http://cdimage.ubuntu.com/ports/rele...te-powerpc.iso](http://cdimage.ubuntu.com/ports/rele...te-powerpc.iso)


or


[http://cdimage.ubuntu.com/xubuntu/po...te-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/po...te-powerpc.iso)
__________________
Your TV might soon be obsolete...find out at [https://www.dtv2009.gov/](https://www.dtv2009.gov/)
Close the Windows and "open" the "source" . 2008 is the year for Linux
Last edited by Midwest-Linux; April 14th, 2008 at 07:56 AM. 

---

### Post by pxwpxw on 2008-09-10
there was a scsi bug that failed to detect some scsi drives in feisty 704 (affected my ppc Old World with twin scsi). That particular bug was cleared in hardy 804, intrepid 810 and I think in gutsy710. I have 810 (server) installed on an Oldworld pre g3 ppc. Not sure if its yr issue, but sounds like it. Try 804, dont go back.

---

### Post by Bikerbob on 2008-09-10
Wow 804 on an oldworld?? thats great. I was under the impression that would not fly. 

This is Ubuntu right? Xubuntu or even looking forward to Fluxbuntu as these seem lighter and might run better on an older machine.

OK.. I will try 804 as well.. CDs are cheap.

James

---

### Post by tiresia on 2008-09-10
I installed Ubuntu Hardy on a PowerMac 8500 (with a Sonnet Prozessor Upgrade g3 500 
mhz) via BoootX. It runs perfectly. 
Do not forget to run the G3 Cache Enabler (and to choose this option in the preferences)
How much RAM do you have?

---

### Post by snowpine on 2008-09-10
> **Bikerbob said:**
> 
This is Ubuntu right? Xubuntu or even looking forward to Fluxbuntu as these seem lighter and might run better on an older machine.


As far as I know, the PowerPC version of Fluxbuntu never materialized...

---

### Post by Bikerbob on 2008-09-10
No not yet.. but I have been told the project is not dead.

OK.. so I cannot get the .app to get anywhere.. I assume it will work better when I am trying to run an installed system.

BUT 8.041 did boot and run the installer fine from a cold boot. WOO HOO!


I will report when I have an installed system.

James

---

### Post by Bikerbob on 2008-09-11
OK, so I get the system installed.

But I am having some issues.


Running BootX with the kernel and the ramdisk worked.. but trying to use the kernel and a root=/dev/sdb11  does not..

From what I can see in the dmesg.. the linux boot has not even setup the scsi drives yet.. therefore it cant find the root.

How do I get around this?

Found this thread [http://ubuntuforums.org/showthread.php?t=13344](http://ubuntuforums.org/showthread.php?t=13344)

I tried this, it does accept the the options, and it does start a boot, but I just end up back at the language install prompt.

But I could see that with the ramdisk loaded that either gave it time, or the ramdisk itself gave the commands for starting up the scsi drives.

I have 8.04 installed.. I just cant get to it now. Any ideas?

James

---

### Post by tiresia on 2008-09-11
The problem is that in the OldWorld Powerpc the installer does not install a bootloader. 
You will always need BootX to start Ubuntu.Therefore you need the new kernel and the initrd.img for it, that the Ubuntu installer generated after the Installation in /boot.

In order to get a copy of it, you must start from the Installer CD again (as you did to install Ubuntu) and run a shell. I would do like this:
1. Start from the CD and follow all steps as if you want to install again until the Parted mount all disks for you - note the number of your MacOS9 partition - let's say '/dev/sda3
2. At this point choose the option 'back' to go back to the main menu
3. Choose the option 'execute a shell' (or somenthing similar)
4. You should find all your disks mounted on /target
5. If your MacOS9 Partition is not mounted run

```
mkdir /mnt/MacOS9
mount -t hfsplus /dev/sda3 /mnt/MacOS9
```
If the MacOS9 partition has hfs File System use
```
mount -t hfs /dev/sda3 /mnt/MacOS9
```

6. Now you can copy the installed Kernel and the initrd.img from /target/boot to your macOs9 partition
7. Restart again and choose in BootX the new Kernel and the new initrd.img

P.S. If your System will upgrade the kernel, do not forget to copy it again to MacOS9!

---

### Post by tiresia on 2008-09-11
You may find this link helpful:

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by Bikerbob on 2008-09-11
> **tiresia said:**
> The problem is that in the OldWorld Powerpc the installer does not install a bootloader. 
You will always need BootX to start Ubuntu.Therefore you need the new kernel and the initrd.img for it, that the Ubuntu installer generated after the Installation in /boot.

OK I get this, sort of thought that might be the issue because the ramdisk is the installer.

> In order to get a copy of it, you must start from the Installer CD again (as you did to install Ubuntu) and run a shell. I would do like this:
1. Start from the CD and follow all steps as if you want to install again until the Parted mount all disks for you - note the number of your MacOS9 partition - let's say '/dev/sda3
2. At this point choose the option 'back' to go back to the main menu
3. Choose the option 'execute a shell' (or somenthing similar)
4. You should find all your disks mounted on /target

OK here we have an issue, I can get to the the partioning, it will show me the devices, I can go back and drop to the ash shell, it even says the drives should be in /target but when I get to the command line.. no /target and the ash shell does not hove  mkdir or mount built into it.

Errrr.. what do I do now?

James

---

### Post by tiresia on 2008-09-11
What do you get if you type just 'ls' ?

---

### Post by tiresia on 2008-09-11
> **Bikerbob said:**
> 
OK here we have an issue, I can get to the the partioning, it will show me the devices, I can go back and drop to the ash shell 

You stopped the process 'too early'. Parted has shown you the devices, but they are not yet mounted. Choose to make a manual configuration, and choose the mount point for the device you need.
When you get in the shell, change directory```
cd /target
``` 
Now you should be in your Ubuntu

---

### Post by Bikerbob on 2008-09-11
thanks for helping btw tiresia,

I am trying it now...

So I did what you asked, I see the drives after a manual configuration (which I did do last time) So now I should make like I am going to install the system again? and pick the partitions? so make like I am proceeding to installing the core?

OK, I looked at the oldworld FAQ and I switched to another console, which is what I was doing wrong.. I was using the first console and dropping to a shell, all I had to do was option F2 and then I was there.

Now I was still not at a point where things were mounted.. so I just mounted them all myself.

Then copied vmlinz and the initrd.gz over.

I am watching my Ubuntu boot up now!! :)

:( OH noooo.. somehow I did not install a desktop and X??? I asked it to install the pkgs for a Kubuntu desktop... man.....

I think installing all the items it will take to get Xwindows up and running manually is poop.. I am trying.. so I guess I will re-install.. at least I know how to do it now!!! :)


James

---

### Post by tiresia on 2008-09-11
> **Bikerbob said:**
> 
So I did what you asked, I see the drives after a manual configuration (which I did do last time) So now I should make like I am going to install the system again? and pick the partitions? so make like I am proceeding to installing the core?

Usually, you should copy the kernel and the initrd.img, after the installation, when the Installer ejects the CD. Instead of rebooting, you should then enter a shell.

So, now do, as if you would install the system again. If I remember, it should mount the partitions, and before starting to install the core, will ask you to set the clock. There you can go back and enter the shell.

---

### Post by tiresia on 2008-09-11
> **Bikerbob said:**
> 

:( OH noooo.. somehow I did not install a desktop and X??? I asked it to install the pkgs for a Kubuntu desktop... man.....


Are you sure, that you don't have X? Or do you have a problem with xorg.conf?
If you didn't install X, it is not so bad. Just use aptitude or apt-get and install what you need.

---

### Post by tiresia on 2008-09-11
> **Bikerbob said:**
> 
I think installing all the items it will take to get Xwindows up and running manually is poop.. I am trying.. so I guess I will re-install.. at least I know how to do it now!!! :)


You don't need to install everything again. If you can get to a shell, and if you want KDE  run just

```
sudo apt-get install kubuntu-desktop
```

---

### Post by Bikerbob on 2008-09-11
tiresia

it looks like from aptitude I could just load in the whole desktop pkg again... 

Am I right?


You answered me before I asked.. thanks :)


James

---

### Post by tiresia on 2008-09-12
If there is no problems anymore, please mark this thread as SOLVED

---

### Post by SubGothius on 2009-04-19
FWIW -- perhaps if only for the benefit of anyone else stumbling into this thread -- I fully documented the process of installing Xubuntu on an "oldworld" PowerMac clone here:

[http://ubuntuforums.org/showpost.php?p=2419715&postcount=3](http://ubuntuforums.org/showpost.php?p=2419715&postcount=3)

Same procedure should still work, about the only thing needing an update is the URL of the latest Xubuntu PPC Intrepid ISO here:

[http://cdimage.ubuntu.com/xubuntu/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/intrepid/release/)

...and the Intrepid installer kernel and boot ramdisk image for BootX here:

[http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/](http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/)

I recommend using the /netboot/ installer files instead of burning a CD, if you've got a DHCP'd ethernet connection and a free afternoon to babysit the download-as-needed Alternate installer.

---


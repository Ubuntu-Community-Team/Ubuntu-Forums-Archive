---
title: "dual booting (first time advice)"
date: 2013-01-30
forum: Any Other OS
---

### Post by majorburt on 2013-01-30
i'm about to dual bot my computer with windows 7. i have a couple questions as i have never done this and don't wish to foul it up.

1) will i need any software other than whats on the OS disk to dual boot?

2) will i need to remove my current harddrive (i'm getting another harddrive for 7) to dual boot cleanly to a new harddrive?

3)will windows 7 automatically partition the harddrive as Ubuntu did? 

4) if not than how do i go about partitioning the harddrive?

anything i forgot to ask that you think would help would be highly appreciated 

thank you all in advance for all the help from you guys !

---

### Post by TheFu on 2013-01-30
There are many opinions on your questions.

First, know that dual booting is dangerous.  The setup forces Ubuntu/Linux to work with Microsoft Windows.  Ubuntu tries to play nice, but Microsoft assumes they own the entire HDD and sometimes does not play nice with other, non-MS OSes.  Linux, Canonical and others try really hard to handle these cases. Sometimes we fail. That can leave you with a computer that will not boot.

Installing Windows7 AFTER any Linux is likely to cause issues. Linux will not boot.  Installing Linux AFTER Windows is probably fine, since Linux is used to working behind MS for booting.

Windows does not understand the linux file systems. We only hope that it ignores them. Usually that is the case.

Linux can understand Windows file systems, to a certain extent.  It is not perfect support, but usually good enough to allow access to data on NTFS.  NTFS does not support the same permissions that Linux file systems support AND that Linux requires. File permissions are critical to multi-user operating systems like Linux.

There are many opinions about partitioning HDDs. With the relatively new changes to HDDs and new format requirements to support large HDDs, but Microsoft and Linux tools are not perfect.  The rule of thumb is to use the OS tools for the partition target user (Windows for Windows AND Linux tools for Linux partitions).  The best recommendation that I can make about this is to use either **parted **or** gparted** for partitioning on Linux systems. **Do not use** fdisk sfdisk or cfdisk - they were created for older 512b sector HDDs which are not commonly sold today.  To modify a partition, you cannot be running an OS on that partition, so I use a special gparted ISO that I boot from a USB-Flash drive under Yumi (from the unetbootin guys).

When partitioning for Linux and Windows7, here are a few ideas:
* Use GPT partitioning, not MBR, unless you plan to run older OSes like WinXP.
* Linux can boot from and access either primary or logical partitions.
* With GPT, over 100 primary partitions are allowed.
* With MBR, only 4 primary partitions are allowed.

I think Windows need 2 primary partitions - to support 4k sector HDDs with GPT. Let Windows create those.

For Linux, you want 3 partitions, perhaps 4.
* / - where most of the OS and applications go. 10-20G is fine for this.
* swap - like the Windows swap file, a place to have 1-2G only.
* /home - where your personal settings, documents and programs reside.  If you place large files elsewhere, then 5-15G is plenty ... unless you are a Java programmer. Then you'll need lots more.
* If you want to share data with Linux and Windows, you probably want an NTFS Data partition. This is where all those big files should be placed too - videos, music, etc... Know that file permissions mean next to nothing on NTFS partitions.

This took me awhile to write. Hopefully others have commented too.

---

### Post by oldfred on 2013-01-30
Some good info from TheFu.

I use gpt for my Linux drives, but Windows will only boot from gpt with UEFI, so for Windows you may need MBR(msdos) partitioning.

If you have a full Windows install it will just install to an empty drive. But be sure to set BIOS to boot from that drive before installing or it may put its boot drives on the other drive.

I prefer to keep each system on separate drives. And keep Windows as the first partition(s) on the sda drive. Windows will work with other configurations, but it works better if it still thinks it is the only system.

I recommend the separate shared data NTFS partition for any data you may want in both systems. Set Windows as read-only from Ubuntu.

---

### Post by ozanne on 2013-01-30
I have just recently done exactly what you are going to do - one difference being you probably know a lot more about this than I did (or do!). I can tall you I just jumped in and did the install without any prep on my laptop - everything went fine and I can boot up now on Windows 7 or Ubuntu. Soon afterward I found my Ubuntu space was rapidly becoming too small - so I simply used the partition manager to re-size the partitions that resulted from the default install. If you can, my suggestion is to give Ubuntu 5G headroom. Good luck - I'm using Ubuntu almost exclusively now and probably won't look back!

---

### Post by kevdog on 2013-01-31
A few questions that I have to ask you since I've done dual boots with winxp, vista, and 7.

Are you planning on using 1 or 2 hard-drives?  2 hard drives are the most secure in case something goes wrong, however with laptops this is a no go.

Most tutorials will tell you to install Windows first and Ubuntu last.  However the thing you need to be careful about is overwriting the windows MBR if this is important.  Ubuntu will by default overwrite the MBR (Master Boot Record) which will in turn run grub.  Its possible to do it the other way around (add Linux to Windows boot menu and do it that way).  I've done it both ways, however it just depends on your setup and if their are any hardware constraints that will get in the way.  

Do yourself a favor and readup on this before you do anything -- particularly if everything is going on one hard drive or disc.  It will determine the way you partition.  I usually do a /boot partition, / (root partition or system partition, /home partition and /swp partition however that's just my preference.  Your's might be different.  You are going to have to do some reading.  Within Windows you can shrink your windows partition if needed and then I usually use GParted to add and configure the windows partition.  

Good luck and don't be afraid to ask questions. What you want to do is very easy, however I've found that in the end sometimes I messed things up.  And this usually either deals with overwrite of the MBR, not making the correct partitions, or making the partitions either too big or too small when I run out of disc space months later.

---

### Post by majorburt on 2013-01-31
> **kevdog said:**
> A few questions that I have to ask you since I've done dual boots with winxp, vista, and 7.

Are you planning on using 1 or 2 hard-drives?  2 hard drives are the most secure in case something goes wrong, however with laptops this is a no go.

Most tutorials will tell you to install Windows first and Ubuntu last.  However the thing you need to be careful about is overwriting the windows MBR if this is important.  Ubuntu will by default overwrite the MBR (Master Boot Record) which will in turn run grub.  Its possible to do it the other way around (add Linux to Windows boot menu and do it that way).  I've done it both ways, however it just depends on your setup and if their are any hardware constraints that will get in the way.  

Do yourself a favor and readup on this before you do anything -- particularly if everything is going on one hard drive or disc.  It will determine the way you partition.  I usually do a /boot partition, / (root partition or system partition, /home partition and /swp partition however that's just my preference.  Your's might be different.  You are going to have to do some reading.  Within Windows you can shrink your windows partition if needed and then I usually use GParted to add and configure the windows partition.  

Good luck and don't be afraid to ask questions. What you want to do is very easy, however I've found that in the end sometimes I messed things up.  And this usually either deals with overwrite of the MBR, not making the correct partitions, or making the partitions either too big or too small when I run out of disc space months later.

i'm going to be using a separate, clean harddrive to install windows 7 onto.

will i be needing to make all of the above mentioned partitions when using a separate harddrive?
of not than what partitions should i make on the harddrive?
and lastly, will the partitions need to be made before or after the installation of windows 7?

---

### Post by furything on 2013-01-31
> i'm going to be using a separate, clean harddrive to install windows 7 onto.

will i be needing to make all of the above mentioned partitions when using a separate harddrive?
of not than what partitions should i make on the harddrive?
and lastly, will the partitions need to be made before or after the installation of windows 7?If using a separate hard drive as you have said (and that is how I do it)

unplug unbuntu drive
mount new drive into sata0 so it is sda (if you want to use windows back up it has to be the first drive)
run the windows install (whether you create a single partition for the whole drive or part of the drive a small 100mb partition will be created and labelled as system reserved at the beginning of the drive)

reconnect ubuntu and using BIOS tell it to always boot from ubuntu as primary boot device

When you load ubuntu do the```
grub-mkconfig
``` in the terminal and enjoy.

When wanting to do windows backup from the BIOS select single boot option and select the windows drive to boot.

---

### Post by majorburt on 2013-01-31
> **furything said:**
> If using a separate hard drive as you have said (and that is how I do it)

unplug unbuntu drive
mount new drive into sata0 so it is sda (if you want to use windows back up it has to be the first drive)
run the windows install (whether you create a single partition for the whole drive or part of the drive a small 100mb partition will be created and labelled as system reserved at the beginning of the drive)

reconnect ubuntu and using BIOS tell it to always boot from ubuntu as primary boot device

When you load ubuntu do the```
grub-mkconfig
``` in the terminal and enjoy.

When wanting to do windows backup from the BIOS select single boot option and select the windows drive to boot.

why do i have to do the code/what does it do?

---

### Post by oldfred on 2013-01-31
We normally post this:

sudo update-grub

But all that is, is a link to this which runs the grub-mkconfig:
```
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```

You can see these files in /usr/sbin

And what that does is run the grub scripts to write a new grub.cfg file which is the menu you see when you reboot. It also runs the os-prober which is one of the scripts it runs and that finds other installs on you system.

---

### Post by TheFu on 2013-01-31
> **majorburt said:**
> i'm going to be using a separate, clean harddrive to install windows 7 onto.

will i be needing to make all of the above mentioned partitions when using a separate harddrive?
of not than what partitions should i make on the harddrive?
and lastly, will the partitions need to be made before or after the installation of windows 7?

There is only 1 boot sector for each HDD, but a PC BIOS only boots from 1 drive.  If you plan to have both drives connected at the same time, then you'll need to have both Windows and Linux be able to boot.

Also, MBR is for older hard drives. If you have a newer HDD, then it is likely to be 4K sectors, not 512b sectors.  It is important for performance in both Windows AND Linux that you get the sectors aligned on 4K boundaries.  While you can use MBR for drives smaller than 2TB, that might not be the best answer.  For drives larger than 2TB, you** must use** GPT partitioning.

OTOH, if you will physically disconnect each drive when the other is connected and will be changing the BIOS to point to the boot sector of the HDD between changes, then you can ignore what I've said.

---

### Post by majorburt on 2013-02-03
> **TheFu said:**
> OTOH, if you will physically disconnect each drive when the other is connected and will be changing the BIOS to point to the boot sector of the HDD between changes, then you can ignore what I've said.

that seems like over complicating simple stuff in my opinion.

> **TheFu said:**
> Also, MBR is for older hard drives. If you have a newer HDD, then it is likely to be 4K sectors, not 512b sectors. It is important for performance in both Windows AND Linux that you get the sectors aligned on 4K boundaries. While you can use MBR for drives smaller than 2TB, that might not be the best answer. For drives larger than 2TB, you must use GPT partitioning.

so, this basically says what kind of partitioning i should do for the windows drive?

> **oldfred said:**
> We normally post this:

sudo update-grub

But all that is, is a link to this which runs the grub-mkconfig:
```
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```

You can see these files in /usr/sbin

And what that does is run the grub scripts to write a new grub.cfg file which is the menu you see when you reboot. It also runs the os-prober which is one of the scripts it runs and that finds other installs on you system.

so without doing the above mentioned code in Linux, the default boot-loader will only see Linux as an option to boot from and not windows?

---

### Post by TheFu on 2013-02-03
> **majorburt said:**
> that seems like over complicating simple stuff in my opinion.  I agree, but you didn't say how you planned to use it, so I did not assume anything.

> **majorburt said:**
>   so, this basically says what kind of partitioning i should do for the windows drive?

I provided information without knowing your specific setup. YOU have to choose what makes the most sense for your specific needs OR provide much more detailed information.  There is always a trade-off between complexity and capabilities, right?

> **majorburt said:**
>  so without doing the above mentioned code in Linux, the default boot-loader will only see Linux as an option to boot from and not windows?

I don't know.  Oldfred can answer that, but I suspect if anything bad happens around your dual-booting, it will be easier to run those commands in Linux to see any Windows AND any Linux partitions that could be booted - adding them to the boot record for one of the HDDs installed in your system.  Just remember that BIOS will only look for boot code in a specified order on your system.  Whichever device it discovers a valid boot on based on that order will be booted.  Usually, it is best to have 1 boot menu per computer to prevent confusion later, but that is just an opinion.  If 1 HDD fails, and it is the only one with a boot sector installed, that could be bad too for someone unfamiliar with the grub tools.  It has gotten much easier to recover from failed/corrupt boot loaders thanks to some smart tools that understand where Linux likes to place boot information on partitions.

Personally, I avoid dual booting and use virtual machines instead. They are less risk for my specific requirements and I've learned how to get great performance for pretty much any tasks, except  GPU intensive like high-end gaming.   If your PC has 4G of RAM, is at last a C2D CPU with VT-x capables enabled, then virtual machines are pretty great AND very easy.  Either Windows or Linux can be the hostOS.

---

### Post by oldfred on 2013-02-03
With multiple drives and multiple installs I prefer to keep each boot loader on the same drive as the install, but set BIOS to boot from grub since grub is designed to multiple boot. That way when one drive fails, I should be able to change BIOS and boot other drive.

If you have drives disconnected when you install Ubuntu, grub cannot find other systems. If you have the drives connected you have to use Something Else or manual install to have the option on where to install the grub2 boot loader. But then you also have to manually specify partitions, formats & sizes.

---

### Post by majorburt on 2013-02-16
ok, between you guys and my bro, its installed!!!!

everything's working and as it should be.


thanks to all here, you all rock!!!

---

### Post by ShadowGuardian on 2013-03-03
Its good to hear you got it working.  For anyone else curious about dual booting (on two hdd) here is what i did:   

Hook up first hdd, then install win7,  unplug it.  Then hook up different hdd, install ubuntu.  Plug both in and edit BIOS to boot on the ubuntu hdd first.  At first GRUB didn't show up because it didn't locate Windows 7.  i edited a GRUB file to make it show GRUB, then updated GRUB.  Everything works.

P.S. This worked for me, but i am not responsible if you screw something up.

---


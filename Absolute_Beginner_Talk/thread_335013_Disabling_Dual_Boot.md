---
title: "Disabling Dual Boot"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by g3k0 on 2007-01-09
I want to reset my windows partition to factory settings.  Before I was dual boot I was able to press control -f11 to make it use the restore but now that I dual boot it does not work.  Is there any way to make it boot just to windows and then reenable it to allow me to dual boot again.

Sorry if I didnt explain this well. 
Thanks

---

### Post by Sweet on 2007-01-09
Try this topic, it should help:

[http://ubuntuforums.org/showthread.php?t=43834](http://ubuntuforums.org/showthread.php?t=43834)

---

### Post by g3k0 on 2007-01-09
So my only option is to remove linux?

---

### Post by wireddad on 2007-01-09
Try this too.

[http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr](http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr)

---

### Post by Duck2006 on 2007-01-09
Once your done the fixmbr and windows is working ok have a look at this site,

[http://www.enterprisedt.com/publications/dual_boot.html](http://www.enterprisedt.com/publications/dual_boot.html)

It sould let you keep the mbr intact and let you boot to ubuntu

I thing this is what your looking for.

---

### Post by g3k0 on 2007-01-09
I cant access 
[http://www.users.bigpond.net.au/herm....htm#fdisk_mbr](http://www.users.bigpond.net.au/herm....htm#fdisk_mbr)

I am connecting through a proxy which blocks it =/

---

### Post by wireddad on 2007-01-10
> **g3k0 said:**
> I cant access 
[http://www.users.bigpond.net.au/herm....htm#fdisk_mbr](http://www.users.bigpond.net.au/herm....htm#fdisk_mbr)

I am connecting through a proxy which blocks it =/

I am not sure if this will work but here goes...

            [CENTER]
            [SIZE=+3][B]Un-install Page
        [/B][/SIZE]               [SIZE=+3]**    **[/SIZE] [LEFT] [RIGHT]Edited 22nd September 2006
 
 [/RIGHT]
  Even if you don't use Ubuntu, you should still keep it unless you really need the extra hard disk space. Ubuntu is very secure, and you can use it as a secret partition for storing back-ups and important data on. You can ['hide' the GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst"), so that no-one will see it when the computer is starting up, unless you press the 'Esc' key at the right moment. Some people pay a lot of money for a 'security vault' in their computer, and you have one already for free.
            
            Ubuntu is a good emergency operating system too. When your other operating system lets you down and fails at a critical time, you can just boot into Ubuntu and get your urgent work done until you have time to get the other operating system repaired. At the same time, you'll know if it's a software problem and not a hardware problem if your equipment suddenly works properly under Ubuntu.
            
            Okay, enough talk, for those who really insist on uninstalling, here it is:
            
            [B]Uninstalling Ubuntu is a two step process which most people should be able to do very easily.

[/B]STEP ONE, PREPARE THE MBR..........................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE_PREPARE_THE_MBR")
[B]
[/B]STEP TWO, DELETE THE LINUX PARTITION.....................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_TWO_DELETE_THE_LINUX_PARTITION_")
[B]
            
            STEP ONE, PREPARE THE MBR
            
            [/B]First, let me explain the main thing you'll need to understand. Remember back when you installed Ubuntu? I don't know about you, but I always choose to install the GRUB bootloader to [MBR]("http://users.bigpond.net.au/hermanzone/p6.htm") on my hard disk during the install. The MBR is in the first sector of our hard disks. One sector of  a hard disk is 512 bytes in size. 
 The MBR contains three important parts. One is the hard disk's 64 byte partition table,  and another is the 2 byte 55aa signature to indicate to the BIOS that it is a bootable device. 
 That only leaves 446 bytes of room for the bootloader. No bootloader can actually fit into such a small space. When we say we are installing a bootloader to our Master Boot Record, we don't really mean that exactly. The bootloader only puts a small code there just enough to point the BIOS somewhere else on the disk where there is more room. The part that fits in the MBR is called the 'IPL' or 'stage one' of the bootloader. That's the only thing that gets changed, and it's the only thing that needs to be changed again now.
 
 
 Normally the easiest place for stage two, the larger and most important part of a bootloader to live is in an operating system partition. Your Windows NTLDR lives in your Windows partition and Grub lives in your Ubuntu partition. 
 The main part of the bootloader, be it Grub, Lilo, or NTLDR, is the part that actually does the real work of booting the operating system's kernel. 
 When we are dual or multi-booting,  Stage2 also gives us a menu which allows us to choose which operating system you want during boot-up. When you were using Grub, if you choose Windows, GRUB redirects the BIOS back to Windows bootsector and NTLDR bootloader, to 'chainload' Windows. It works like a relay system. 
     
     Now, while you still have Grub's IPL code in your MBR, when you delete the Ubuntu partition, that second, vital part of Grub will be gone. When you try to boot up, your MBR will be pointing to an empty space, and there will be nothing there to offer you a menu to choose Windows anymore either. 
 You'll get a black monitor background with white text on it: 
'GRUB error 22'
 Meaning, 'No such partition. This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.' 
Grub won't be there anymore and you won't be able to boot Windows or any other operating system you might have installed. You'll just have one of those black screens with the white typing on it and a blinking cursor.
     
 You can avoid that situation by preparing your MBR first. This can be easily done by overwriting the 446 bytes of bootloader code in the MBR with code for another bootloader before you delete the Ubuntu partition. 
Well, don't worry if you have deleted Ubuntu already, you can still overwrite your Master Boot Record's IPL code any time, it doesn't really matter whether you do it first or later.
 
            To replace Grub's MBR code with the equivalent code for NTLDR and make the MBR point directly to Windows like it used to, you just use the same software you used when Windows was installed in the first place. This will overwrite GRUB's version of the 'IPL' in your MBR (or 'boot sector'), and  replace it with the Windows version again.
            The way to do that is very simple, exactly the same way you did it the first time. (Remember?)
           You just re-install Windows....Well, that is one way to do it, but it will take you a while. There are plenty of faster ways...

fixmbr.......................................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#fixmbr")

fdisk /mbr.................................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr")

dd command.............................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#dd_command")

Super Grub Disk ......................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk_")

GAG Boot Manager...................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager")

MbrFix.exe.................................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")


            
            **fixmbr**
            Just put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the fixmbr command.
            
            **fdisk /mbr**
For Windows 98 or Windows XP without an 'install' CD
  You will need a blank, formatted floppy disk.
  I have used this method to restore the bootsector on both my Windows XP Home Edition computer and also my Windows 98SE computer. 
  Your computer may have come with a Windows XP 'Recovery Disk' instead of an 'Install' disk, or maybe you lost your Windows XP CD or have Windows 98 or some other version. 
            You can download a self extracting file to make your own Windows 98 boot floppy disk from [Bootdisk.com]("http://www.bootdisk.com/").  The one I use is called **98SE OEM.**
  To make the boot disk, once the boot98se WinImage Self Extractor file is downloaded, place a formatted floppy in the floppy drive and then just double-click on the file. I it will make a boot floppy automatically. 
            A Windows 98 boot floppy will work just as well as an install CD to restore your 'boot sector'. 
  You must first of course have your computer's BIOS set to boot from the floppy disk drive before the hard disk in the BIOS boot sequence. See this website's [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm").
   Just pop the floppy in the drive and boot your computer. You will soon see a black background in your monitor and will be given three choices. 
  These are,  
                       1. Start computer with CD-ROM support
                       **2. Start computer without CD-ROM support**
                       3. View the Help file.
  
  Choose number **2, 'Start computer without CD-ROM support'. **
  After a few minutes, you will see a prompt that looks like this, 
  **A:\_**
  
   After the     **A:\_**   prompt and type the command **fdisk /mbr** and wait for the command to work. When it is finished, press 'Ctrl'+'Alt'+'Del' to reboot, and remove the floppy disk.
  Your 'boot sector' will be pointing to Windows again.
 
**dd command**
 Or, if you planned ahead enough to have already made a back-up copy of your previous MBR, you can just restore it if you like. 
     **Back up and Restore your MBR**....................................................................................[GO]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")
          
 
 There are several more alternative methods for writing Windows bootloader code to an MBR. You might like to use one of these if neither of the above methods suit you.
 
**  Super Grub Disk **
 Super Grub Disk has a new feature that installs Windows bootloader code to MBR faster and easier than any other way I have tried yet.
 **  Super Grub Disk Page**................................................................[Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
                      
            _****_**GAG Boot Manager**
           Rather than put simply put plain old Windows IPL back in your 'boot sector', another thing you should consider is whether to upgrade and install [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") to your MBR instead. GAG Boot Manager  will boot Windows and do lots more as well. You could easily install GAG to MBR to overwrite GRUB. GAG Boot Manager can boot up to nine operating systems _and_ it installs to the first track of your hard drive and overwrites any viruses that might be lurking there. It's a good idea to have that normally vacant space filled. 
           
     ****[U]
   [/U]**MbrFix.exe**
1) Download a small utility called MbrFix.exe, [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)
   
   2) Paste the file to the root of drive C:
   If you don't know what I mean by 'the root of drive C, just open in 'My Computer, Click on Local Disk (C:), open it, and paste MbrFix.exe.there.
   
    3) Click 'Start'->'Run', type CMD (for a Command Prompt).
   The command prompt will at first be something like,
                     C:\ Documents and Settings \ Herman >_                (Where 'Herman' is my username for Windows, yours will probably be something different).
 
   Change it to just a C: prompt by typing: cd \ , then press 'Enter'.
   After that you should just have a plain C:\>_ prompt. 
                     C:\>_                
   Type this command after the C:\> prompt: MbrFix /drive 0 fixmbr /yes
 for example,
 Code:
                     C:\> MbrFix /drive 0 fixmbr /yes                
   Nothing much will appear to happen, your monitor may blink slightly, that's all. You will see the plain C:\>_ prompt again. Type 'exit'.
 
   4) That's it! Reboot to see if it worked.
 
 
           
            [B]STEP TWO, DELETE THE LINUX PARTITION
            
            [/B]Deletion of the Linux partition is really the easy part. You can use any partitioning software for that.  Just delete the partition.
            You can then do whatever you like with the resulting 'free space'. You might want to use the partitioning software to resize your Windows partition back to the original size, or create a new partition there for data storage. You might want to leave the free space alone and partition it later when you install some new operating system maybe.
            My favorite partitioning software is [GParted LiveCD]("http://gparted.sourceforge.net/"), in case you don't already have something.
            
            
            
            [CENTER][Back to Top]("http://www.users.bigpond.net.au/hermanzone/p18.htm#uninstall_top")[/CENTER]
             
            
            
             
            
            
            
            
            
            
            
            
            
            
                                  [B]
            [/B]
            [/LEFT]
             [/CENTER]

---

### Post by wireddad on 2007-01-10
I hope no one gets mad for pasting the site in the post.

---


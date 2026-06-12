---
title: "how to install mbrfix?"
date: 2012-05-30
forum: Any Other OS
---

### Post by s1wood on 2012-05-30
I've downloaded mbrfix from Softpedia on my Windows XP computer and have extracted the zip files. I have an HTML doc which gives a list of  commands and a file labelled
 "MbrFix [www.sysint.no]("http://www.sysint.no") Systemintegrasion AS"

Opening or running it  it produces a brief flash as if a console screen has opened for an instant but nothing else. 
Using the command prompt 'mbrfix' is not recognised.
I am running it as administrator.
I am presumably missing out a step somewhere - can someone advise please.

Susan
I know this is actually a Windows question but mbrfix gets so strongly recommended on this site that I thought I'd try here first.

---

### Post by kanikilu on 2012-05-30
I've never used it, but if it's giving you a "command not found" (or similar) error, are you sure you are in the same directory that you downloaded/extracted the executable files?

---

### Post by oldfred on 2012-05-30
Moved to other OS.

Several other ways.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Boot Repair for Windows or Grub2 bootloaders:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

From Ubuntu liveCD:
Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by s1wood on 2012-05-30
>are you sure you are in the same directory that you downloaded/extracted the executable files?<
Not quite sure what a directory is on Windows - it's in my downloads folder at the moment.

Susan

---

### Post by kanikilu on 2012-05-30
Ok, so then in the cmd window, do:

```
cd %USERPROFILE%\Downloads\
```

If you extracted the program to a sub-directory (FYI: directory = "folder"), add that on to the end of the path above.

And then try the MbrFix program again. It looks like it's a program that's run on-demand, and not installed. It has a lot of options:

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

Good luck.

---

### Post by chrissywissy on 2012-05-31
I have Easy BCD installed on my dual boot W7 machine. Gives you the options of restoring MBR and/or changing boot order/times within W7. Available at [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/) . Hope this helps.

---

### Post by qyot27 on 2012-05-31
> **kanikilu said:**
> Ok, so then in the cmd window, do:

```
cd %USERPROFILE%\Downloads\
```

If you extracted the program to a sub-directory (FYI: directory = "folder"), add that on to the end of the path above.
This isn't necessary for Vista and Win7 (it is good to know how to do, though).  If you're in Windows Explorer, just hold down Shift and then right-click somewhere in the current folder, and choose 'Open Command Window Here'.  Cuts down on navigation fuzziness or trying to remember the environment variable or absolute path.

(XP users have to install either the MS-hosted XP Powertoy to do this, or a third-party shell extension like ContextConsole; these put it in the normal right-click menu for convenience)

---

### Post by wilee-nilee on 2012-05-31
> **oldfred said:**
> Moved to other OS.

Several other ways.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Boot Repair for Windows or Grub2 bootloaders:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

From Ubuntu liveCD:
Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

+1
These are the standard methods on fixing a boot problem.

---

### Post by ahso4271 on 2012-05-31
you can also boot windows rescue cd and type: "fixmbr" or alike

---

### Post by s1wood on 2012-05-31
Thanks for the advice, I don't have a Windows CD and  I couldn't get the command prompt to recognise the path, so I have downloaded BootRepair and will burn a disk .
I'm not quite sure how to use it though, what I have is a dual-boot with Windows XP and Linux (Gnome Zen-Mini) and. in order to speed up the boot I want to go direct to Windows. I was intending to remove the Linux and wanted to restore the Windows boot first.
Can I run the BootRepair CD under Windows or do I need to have the Linux running?

Susan

---

### Post by wilee-nilee on 2012-05-31
> **s1wood said:**
> Thanks for the advice, I don't have a Windows CD and  I couldn't get the command prompt to recognise the path, so I have downloaded BootRepair and will burn a disk .
I'm not quite sure how to use it though, what I have is a dual-boot with Windows XP and Linux (Gnome Zen-Mini) and. in order to speed up the boot I want to go direct to Windows. I was intending to remove the Linux and wanted to restore the Windows boot first.
Can I run the BootRepair CD under Windows or do I need to have the Linux running?

Susan

You can post the bootinfo summary from the tool, post the http address, so we know what is going on.

Did you try the lilo option?

Courtesy of oldfred. 

You may need to run to confirm the hard drives X, as in sdX might be sda, or sdb, etc
```
sudo fdisk -lu
```> From Ubuntu liveCD:
Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box  against the Universe repo in the Ubuntu Software tab. Close that window  and click on reload before installing lilo with Synaptic or command  line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by s1wood on 2012-05-31
The BootRepair CD opens to reveal folders but doesn't do anything - tried on Ubuntu as well as the ZenMini. Typing boot-repair in the terminal didn't do anything.

Went through the Ubuntu Live CD install lilo process, did the install  but the sudo lilo -M/dev/sda/mbr command gave no such pathway.

Now a bit worried that installing lilo may prevent the computer booting at all - there seemed to be some such warning on the terminal. Is this likely?

Susan

---

### Post by wilee-nilee on 2012-05-31
> **s1wood said:**
> The BootRepair CD opens to reveal folders but doesn't do anything - tried on Ubuntu as well as the ZenMini. Typing boot-repair in the terminal didn't do anything.

Went through the Ubuntu Live CD install lilo process, did the install  but the sudo lilo -M/dev/sda/mbr command gave no such pathway.

Now a bit worried that installing lilo may prevent the computer booting at all - there seemed to be some such warning on the terminal. Is this likely?

Susan

When you boot the cd or open the boot repair in a cd or ubuntu install you should see this screen, hit the bootinfo summary button you see, you will after it scans, if all goes well, see a http address where this script is at post that link.

[ATTACH]219015[/ATTACH]

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-05-31
Lilo is a full boot loader but works like Windows in the MBR. So we put its boot loader in the MBR (only) to boot Windows but do not install the full Lilo boot loader. Ignore error messages as the rest of Lilo is missing.

sudo lilo -M/dev/sda/mbr

Should be:

sudo lilo -M /dev/sda mbr

Or a space between the path and the mbr and a space after the parameter -M.

---

### Post by s1wood on 2012-05-31
OK,I ran that command again correctly and got the result

'Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of /dev/sda has been updated'

Is that what was expected? If so, what do I do next?

Susan

---

### Post by wilee-nilee on 2012-05-31
> **s1wood said:**
> OK,I ran that command again correctly and got the result

'Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of /dev/sda has been updated'

Is that what was expected? If so, what do I do next?

Susan

So, you have only really referenced what your problem or problems are. We or at least myself ask for the bootscript for several reason. First to get a clear picture of your set up, and second to confirm your problems. 

So in not providing a clear description as far as I can tell it is difficult to actually direct you.

We don't know exactly what is installed, where it is at, or what your problems actually are and the final goal here is, does this make sense to you?

Anyway I see oldfred has answered you so carry on.

---

### Post by s1wood on 2012-05-31
Is this what you are after?

The Master Boot Record of  /dev/sda  has been updated.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x587bfbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155    78156224    13478535   83  Linux

Disk /dev/sdb: 1056 MB, 1056702464 bytes
2 heads, 63 sectors/track, 16379 cylinders, total 2063872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x014c6439

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2059263     1029616    6  FAT16
ubuntu@ubuntu:~$ 


This is on the machine in question using Ubuntu 10.10 live CD

Susan

---

### Post by wilee-nilee on 2012-05-31
> **s1wood said:**
> Is this what you are after?

The Master Boot Record of  /dev/sda  has been updated.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x587bfbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sda2        51199155    78156224    13478535   83  Linux

Disk /dev/sdb: 1056 MB, 1056702464 bytes
2 heads, 63 sectors/track, 16379 cylinders, total 2063872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x014c6439

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2059263     1029616    6  FAT16
ubuntu@ubuntu:~$ 


This is on the machine in question using Ubuntu 10.10 live CD

Susan

Thanks that is really helpful. :)

You should have a windows boot now, if the files in windows were correct, and you ran the commands as oldfred posted.

If you still have problems you can run the bootinfo summary from the boot-repair tool. 

Or down load the bootscript directly, exstact it to the 10.10 desktop, and run the command and copy and paste the whole results.txt that is generated by the command.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```The boot-repair tool is using this same basic script, slightly modified, we prefer it if possible, but I wanted to to have access to a direct download as well. :)

---

### Post by s1wood on 2012-05-31
Amazing! It actually worked!

I never did sort out mbrfix but I can boot directly into Windows and will be able to eliminate the linux partition, which was the point of it all.

Thanks, all of you for your patience.

Susan

---


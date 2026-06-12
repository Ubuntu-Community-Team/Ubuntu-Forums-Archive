---
title: "Messed up migration of a dual boot on a SSD: broken Ubuntu boot"
date: 2018-01-25
forum: Apple Hardware Users
---

### Post by singularite on 2018-01-25
Hello,

I need some help to fix my non-booting Ubuntu. I have a Macbook Pro with a dual boot OS X / Ubuntu 16.04.3. I have recently bought a SSD. I have cloned the full HD disk with Clonezilla, changed the partition sizes and upgraded OS X on the new clone (/sdb2). I have also changed the cloned UUID of Ubuntu to try to avoid the confusion between the two Ubuntu clone.

I did a mistake formatting the older Ubuntu partitions too early (on disk /sda), and I am know left with an unbootable Ubuntu partition (/sdb4).

I tried to run Boot-Repair from an Ubuntu liveUSB but the situations is not better. Here is the generated boot-info: [http://paste.ubuntu.com/26459686/](http://paste.ubuntu.com/26459686/)

I can access the newly installed grub and also the rEFInd menu. There is (or at least there was before the Boot-Repair) a Bios-grub partition in /sdb6. Though, I can not find the boot
```
sdb1/EFI/ubuntu/shimx64.efi
```
as advised by the Boot-Repair.

Here are screenshots of GParted (were /sda2 and /sdb2 are OS X partition).
[ATTACH=CONFIG]278319[/ATTACH][ATTACH=CONFIG]278320[/ATTACH]

Do you have any idea what is going wrong here ?

Thank you :-)

---

### Post by oldfred on 2018-01-25
I do not know Mac, but generally you cannot have duplicate UUIDs.

```
 /dev/sda1        [COLOR=#b22222]70D6-1701[/COLOR]                              vfat       EFI 

   /dev/sdb1        [COLOR=#b22222]70D6-1701[/COLOR]                              vfat       EFI 


```

Also UEFI uses the GUID or Part UUID to know which partition to boot from. Yours is also duplicated.

      ```
 /dev/sdb1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" PARTLABEL="EFI System Partition" [COLOR=#ff0000]PARTUUID="89dafd3c-884c-4f97-9b50-194ad32f1583"[/COLOR]
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" PARTLABEL="EFI System Partition" [COLOR=#ff0000]PARTUUID="89dafd3c-884c-4f97-9b50-194ad32f1583" 
[/COLOR]

```    

Did you install Windows in BIOS boot mode which forces a hybrid MBR/gpt which should not now be used. Windows will install in UEFI mode on Mac.
       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html


[/URL]

---

### Post by singularite on 2018-01-26
Thank you for your answer. So I began with a little clean up according to your advice:
- I have made a backup (image) of the partitions sda1 (old EFI) and sdb6 (Bios-grub)
- I have deleted them with GParted

I looked at you documentation about mbr and gpt. From GParted (on a liveUSB), I see that both disks are gpt. By the way, when GParted starts, an error from Libparted appears:
> The primary GPT table is corrupt, but the backup appears OK, so that will be used.

However I don't remember getting this error from the installed Ubuntu.
There is no Windows installed on my computer.

Now, the default boot is grub version 2 on the remaining EFI. But Ubuntu is still not booting. I replace is by rEFInd reinstalling it from Mac OS X. Many ineffective boot options appear for Ubuntu.
Either it goes in grub rescue mode, or it crashes with a black screen.


I wonder if it could be a problem with the Nvidia driver. I remember that I had troubles with the default driver when I installed first Ubuntu, and again after an update. How could I check or fix that without booting ? Thank you

EDIT : I tried to boot with the options modprobe.blacklist=nouveau, as well as acpi=off (using F2 in rEFInd), and for both, the boot goes "farther". The command lines that are usually appearing when starting Ubuntu are there, but it crashes anyway at one point. For the first option, the crash is a black screen, and for the second one, a loop of error lines are appearing very fast. I can decipher "Nvidia" and "initialized", which seems to confirm the origin of the problem.

---

### Post by oldfred on 2018-01-26
Moved to Apple sub-forum where those who know Mac may help.

On a PC, you often need nomodeset to boot into lower graphics. But that depends on how old nVidia card/chip is. My system just boots, but has an older nVidia card so nouveau works.
If you need nomodeset then you should install the proprietary nVidia driver from Ubuntu repository. Do not know if same with Mac or not.

Older Mac with older Windows had to use hybrid MBR/gpt partitioning. Mac boots with UEFI but old Windows booted with BIOS which required MBR(msdos) partitioning. Then you had to keep partitions in MBR and gpt partition tables in sync. You do not want hybrid partitions anymore.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html) 

you should be able to run gdisk to clean up partitions.

 sudo gdisk /dev/sda
Command (? for help):  


 GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 
      
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table) 
    
       More repair info:
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by singularite on 2018-02-02
Hello,

I come back to this problem after giving it a little rest. The MBR is now updated to "protective" with gdisk on both disks.

I have forgotten to mention that I also tried the nomodeset option when booting (which seemed to be the most classical fix to this problem).

I read again about my past Nvidia driver problem, but it seems to be different because Ubuntu was finishing booting (resolution problems or blocked in a loop at a login screen). Now, I can read at one point:
[HTML]Welcome to Ubuntu 16.04.3 LTS![/HTML]

But it crashes after:

[HTML]
[...

...]
Found device Samsung_SSD [...]
Activated swap [...]
Reached target [...]
Started File System Check on /dev/[...]
Mounted /boot/efi.
Started Braille Device Support.
Started Braille Device Support.
[/HTML]

(and then black screen.)

I remember that there were no visible file in /boot/efi when I looked at it from a liveUSB (for Ubuntu installation).

---

### Post by oldfred on 2018-02-02
Your original Summary Report from Boot-Repair showed files in the ESP. 

Are you using nomodeset, until you install the correct version nVidia driver?

---

### Post by singularite on 2018-02-03
[COLOR=#000000][FONT=Arial]I have finally reinstalled Ubuntu 16.04.3 on a new partition. I have imported all the folders from my profile on the old partition, and I might be able to do the same for the system files (although I would not risk it without confirmation).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So now I would rather ask: What is the best strategy to recover my configurations, libraries, applications etc?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Replace some system files of the new Ubuntu with the older ones (which ones?)
- Replace some boot files of the old Ubuntu from the newly installed one?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thank you![/FONT][/COLOR]

---

### Post by oldfred on 2018-02-03
Unless running a server with database or Web, you should not have to import anything from /.
Perhaps some settings from /etc, if you manually changed something. I only edit a couple of files like grub's 40_custom, fstab, my own trim in cron and maybe a couple of others. But I separately save those files in /home so my backup includes them.

You do need to reinstall applications.
I export new list of installed apps with every backup in my rsync script file. Not sure there is an easy way to get that list unless booted in system.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[URL="http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders"]http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders

      [/URL]
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
You may find files listed here.

 Apps that are installed
cd /var/lib/dpkg/info 


 

    [URL="http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders"]
[/URL]

---


---
title: "Change Partition Size and Other Things Involving Windows 7"
date: 2012-07-18
forum: Any Other OS
---

### Post by joga24 on 2012-07-18
I have been using Ubuntu for the past year or so now, and today I realized that I made my Windows 7 partition far too small. Out of ignorance, I deleted the entire Ubuntu partition in Windows, figuring that I could easily annex that space for my C drive. 

Oops, I can't do that. I did not know that I previously removed my computers ability to boot straight to Windows. How foolish of me. I don't understand how these things work. Now I can not boot to anything except for this GNU prompt that useless for a person with my skill set.

Fortunately I still had a USB stick that had the Ubuntu installation  stuff on it, and here I am again, using Linux and booting my PC like a pro. 

Now I will attempt to explain how things currently are with my computer, so hopefully someone with computer knowledge can understand my layman blather. Initially I had a 100 gb Windows and 350 gb Ubuntu partition (with the rest of the space taken up by computer things that I know nothing of). The 350 gb partition was the one I destroyed earlier with a single mouse click. My new installation of Ubuntu is on a 11 gb or 6 gb partition, or something like that. The big 350 gb one is still there, what is going on in there I have no idea.

Does anyone know how to get my Windows partition larger without royally messing everything up? I know I can get a recovery DVD and do things like that, but that involves getting a CD I don't have and probably other annoying things. I think no matter what happens it will be annoying, but I am trying to minimize damage and headache here.

Any help is appreciated!

---

### Post by oldfred on 2012-07-19
Moved to other OS.

You actually have a generous size Windows. I normally suggest about 50GB with a separate shared data NTFS partition for any data you might want to share with Ubuntu. For Ubuntu I normally suggest 10 to 25GB for / (root) depending on drive size and if your data will be in /, a separte /home or the shared data partition.

You can restore the Windows boot loader from your Windows repairCD or from Ubuntu you can restore a Windows work alike.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

From windows:

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If you did not make this do it right away:
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Always use gparted on LInux partitions from your liveCD or USB, and only use Windows to shrink or expand the Windows system partition.

You can also download and install the lilo boot loader which works just like Windows in looking for the boot flag and jumping to that partition to boot:

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader as we are really booting with Windows.

---


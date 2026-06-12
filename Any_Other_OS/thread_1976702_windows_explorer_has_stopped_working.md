---
title: "windows explorer has stopped working"
date: 2012-05-09
forum: Any Other OS
---

### Post by ramakanta on 2012-05-09
I have 
Computer: 
 
Computer Type ACPI x86-based PC 
Operating System Microsoft Windows 7 Ultimate genuine 
OS Service Pack Service Pack 1 
Internet Explorer 8.0.7601.17514 
DirectX DirectX 11.0 
 
Motherboard: 
 
CPU Type DualCore Intel Pentium E2180, 2000 MHz (10 x 200) 
Motherboard Name 
Intel Newberry Lake D945GCNL (2 PCI, 1 PCI-E x1, 1 PCI-E x16, 2 DDR2 DIMM,Audio, Video, Gigabit LAN) 
Motherboard Chipset Intel Lakeport-G i945GC 
System Memory 1013 MB (DDR2-667 DDR2 SDRAM) 
 
DIMM1: 1024636750L 
1 GB DDR2-667 DDR2 SDRAM (5-5-5-15 @ 333 MHz) (4-4-4-12 @ 266 MHz) (3-3-3-9 @ 200 MHz) 
 
Display: 
Video Adapter          Intel(R) 82945G Express Chipset Family (Microsoft Corporation - WDDM 1.0) (256MB) 
3D Accelerator         Intel GMA 950 
Monitor SyncMaster      B1930N 
 
 
 
Audio Adapter 
Realtek ALC888/1200 @ Intel 82801GB ICH7 - High Definition Audio Controller[A-1] 
 
Storage: 
 
Disk Drive SAMSUNG HD161GJ ATA Device (160 GB, 7200 RPM, SATA-II) 
Optical Drive MOSER BAER DH-22AAS ATA Device 
 
Partitions: 
C: (NTFS) 61899 MB 
D: (NTFS) 81999 MB 
E: (NTFS)  8625 MB 
Total Size 140.5 GB

my problem is when i want to open my movie folder  and try to open [COLOR=Sienna]**windows explorer has stopped working**[/COLOR]   message displayed and automatically  restart my computer. please help me  how to solve this problem. 
thank you.

:confused:

---

### Post by andaryfaysal on 2012-05-09
Hi, I had the same problem in the past. It turned out that there was a single video file in the folder that is causing the windows explorer to crash everytime it sees this file.
The solution I did was to create a new temporary folder on another directory and copy my video files (exclude subfolders) one by one to the new directory using the command prompt without having to open the folder with explorer. Every time you copy a file open the new folder then close it. If explorer crashes, then the newest file arriving is the one causing the problem and you can delete it from the original folder using the command prompt "del" command.
That should fix it, and you can remove the temporary directory afterwards. 
Good luck!

---

### Post by ramakanta on 2012-05-09
> **andaryfaysal said:**
> Hi, I had the same problem in the past. It turned out that there was a single video file in the folder that is causing the windows explorer to crash everytime it sees this file.
The solution I did was to create a new temporary folder on another directory and copy my video files (exclude subfolders) one by one to the new directory using the command prompt without having to open the folder with explorer. Every time you copy a file open the new folder then close it. If explorer crashes, then the newest file arriving is the one causing the problem and you can delete it from the original folder using the command prompt "del" command.
That should fix it, and you can remove the temporary directory afterwards. 
Good luck!
please any other solutions.!!

---

### Post by Grenage on 2012-05-09
While I can't help with the issue at hand, I can tell you that all of your posts with screenshots have movie rips on them, which isn't a great idea around here.

---

### Post by jadtech on 2012-05-09
I wouldn't worry to much about  explorer crashing it only has to  work long enough to down load chrome or Firefox  then you can  hide the Icon for it and forget its there .. 

do what  most others here are doing and  forget your windows partition is there

---

### Post by ramakanta on 2012-05-16
> **andaryfaysal said:**
> Hi, I had the same problem in the past. It turned out that there was a single video file in the folder that is causing the windows explorer to crash everytime it sees this file.
The solution I did was to create a new temporary folder on another directory and copy my video files (exclude subfolders) one by one to the new directory using the command prompt without having to open the folder with explorer. Every time you copy a file open the new folder then close it. If explorer crashes, then the newest file arriving is the one causing the problem and you can delete it from the original folder using the command prompt "del" command.
That should fix it, and you can remove the temporary directory afterwards. 
Good luck!
Hi friend my problem is solved when try this thing..
 
--Click Start and click Computer

--Click Organize and select Folder and search options from the dropdown

--On the Folder Options window, click the View tab

--Place a check in the option to Always show Icons, never thumbnail

--Remove the check for the option to Display file icon on thumbnails

--Click OK to close the Folder Options window

you can try these steps , might me solve your problem too.
 
thanks .
 
:) ;) :)

---

### Post by mode7 on 2012-05-17
> **jadtech said:**
> I wouldn't worry to much about  explorer crashing it only has to  work long enough to down load chrome or Firefox  then you can  hide the Icon for it and forget its there .. 

do what  most others here are doing and  forget your windows partition is there

Just so it's made clear, Windows Explorer is the shell for Windows. Internet Explorer is the web browser.

I'm glad your issue is solved, ramakanta, but be careful. The problem-causing file may still be corrupt.. causing issues if you open it directly!

---

### Post by ramakanta on 2012-05-18
> **mode7 said:**
> Just so it's made clear, Windows Explorer is the shell for Windows. Internet Explorer is the web browser.

I'm glad your issue is solved, ramakanta, but be careful. The problem-causing file may still be corrupt.. causing issues if you open it directly!
Thanks for suggesion ... :)

---

### Post by Krishna Murthy on 2012-05-22
Hi Ramakanta

This is because of a corrupt/broken video.

Install Unlocker, run Unlocker, move the video to a different drive and try to open it with windows explorer. Check the processor while doing this. If the processor is running at 100% that definitely means the video is the cause.

Once again run Unlocker and delete the file. Unlocker by default deletes the file to recycle bin. Empty the recycle bin.

Common Sense tells it is not a good idea to crash a system for a video file. Unlocker (1.6 megs) is available at all download centres.

---


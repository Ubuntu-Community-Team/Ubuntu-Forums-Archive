---
title: "problem loading windows after installing ubuntu"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by tashka on 2007-10-01
i've a problem loading windows after installing ubuntu it give me :

Windows could not start because the following file is missing or corrupt:
<windows root >\system 32\hal.dll\.


can anyone help me plz....:confused:

---

### Post by tdrusk on 2007-10-01
> **tashka said:**
> i've a problem loading windows after installing ubuntu it give me :

Windows could not start because the following file is missing or corrupt:
<windows root >\system 32\hal.dll\.


can anyone help me plz....:confused:

You will probably need a windows disk to repair it. Did you defrag about 20 times before installing ubuntu? This is necessary because when a windos filesystem is not defragged files are spread out all across the hard drive. So if you were to use half the drive without defragmenting you can loose important files.

---

### Post by JBAlaska on 2007-10-01
This situation occurs when setting up a dual boot situation with Windows 2000 and Windows XP (it may occur with other setups).  After Windows XP's install routine has finished copying files, and is ready to boot to the GUI portion of SETUP, you may receive the above error.

One possible fix.  So far, this has been traced to an incorrect BOOT.INI file.  To gain access to the Boot.ini:

Go to Start/Run and type in: msconfig.  Then go to the Boot.ini Tab.  Or...Right click the My Computer icon/Properties/
Advanced/Startup and Recovery/Settings/System Startup/Edit.

How to Edit the BOOT.INI File in Windows XP
[http://support.microsoft.com/support/kb/articles/Q289/0/22.asp](http://support.microsoft.com/support/kb/articles/Q289/0/22.asp)

This user had 1 hard drive, partitioned into C and D drives.  His BOOT.INI file looked like this: (the erroneous lines are in "blue")

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

The 3 in the erroneous lines, above, points to the 3rd partition on the first physical hard disk.  Since this user only had 2 partitions, this value was incorrect.  Changing the value to 2, in both lines, allowed the user to complete Windows XP's setup.

The corrected BOOT.INI looked like this:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

HAL - Hardware Abstraction Layer

HAL is Microsoft's abbreviation for the Hardware Abstraction Layer, the technology and drivers that let the Windows NT, 2000, and XP operating systems communicate with your PC's hardware. HAL is one of several features--along with the NT file system (NTFS) that replaced the much less secure MS-DOS--that make NT-based operating systems more secure and reliable than Windows 95, 98, and Me.

HAL prevents applications from directly accessing your PC's system memory, CPU, or hardware devices (such as video and sound cards)--a method that can prevent many device conflicts and crashes. Unfortunately, HAL sometimes also slows or stops DOS games and programs, which need to load their own memory managers or control hardware directly for better performance.

With HAL in the way, developers must rewrite or even abandon their older software in favor of newer, HAL-compatible versions. Microsoft has pressured hardware makers to provide or support technologies such as MMX, DirectX, and 3D graphics language OpenGL, all of which allow fast but indirect access to the advanced high-performance features of video, sound, and CPU hardware. Such access also makes for a better visual experience when using Windows for Web and productivity applications; improved graphics performance is evident all over Windows XP's new user interface.

XP also offers some new compatibility-mode features that let you run programs meant to run under earlier operating systems, but, frankly, most DOS-based and even some Windows-based games simply won't work with the new OS.

     Tip:  To see which HAL is currently installed, open Device Manager, and expand the Computer branch. The entry that
              appears in this branch corresponds to the currently installed HAL.

---

### Post by meborc on 2007-10-01
EDIT: i'm stupid ... :)

---


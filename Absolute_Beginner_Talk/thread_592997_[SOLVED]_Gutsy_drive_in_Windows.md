---
title: "[SOLVED] Gutsy drive in Windows"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by steelklvr on 2007-10-26
Hi,

Since I upgraded to Gutsy, when i boot in windows if i try to access my Ubuntu drive, I get prompted with a message asking me to format the drive.

When I go into properties, it says the HDD has 0 bytes of storage.

I have used a tool to make the drive's ext2 filesystem recognisable in windows and it worked with fiesty.

i can access the windows drive from gutsy but not the other way around. 

Any help would be appreciated.

---

### Post by kelbizzle on 2007-10-26
That was happening to me on my laptop. You can try booting into gutsy and shutting it down properly. Then boot into windows. Then you should be able to access it.

---

### Post by spur on 2007-10-26
Simple it's always been that way. Windows can't read any kind of linux. It will therefore report the drive as empty and as unformatted. Linux can read windows though so will report the true state of windows drives or petitions.

---

### Post by kelbizzle on 2007-10-26
> **spur said:**
> Simple it's always been that way. Windows can't read any kind of linux. It will therefore report the drive as empty and as unformatted. Linux can read windows though so will report the true state of windows drives or petitions.

That's not correct info like steel said He uses [Ext IFS for windows]("http://www.fs-driver.org/") to assign a drive letter to the ext3 partition allowing him to see his files in windows. 

Steel: Try shutting gutsy down properly, then boot into windows and see if you can access the drive.

---

### Post by kelbizzle on 2007-10-26
[QUOTE=http://www.fs-driver.org/troubleshoot.html] I have installed the Ext2 IFS software and was able to create a drive letter for a desired volume of Linux. But when I try to access that volume I get an error message "The disk in drive X: is not formatted. Do you want to format it now?" (Of course I don't want to!) Or the content of the volume appears, but when I attempt to write something I get an error message "Access denied".

The ext2fs.sys driver did not mount that volume for some reason, or it mounted it read-only.

Please run the mountdiag diagnosis tool, which you can download here: [mountdiag.exe.]("http://www.fs-driver.org/download/mountdiag.exe")

Please run it at the command prompt and give it the letter of the drive you want to examine, for example:
mountdiag G:
The tool will give you a hint on how to resolve the problem. (Note: The mountdiag tool reads data only; it does not attempt to modify anything.)
If I use hibernate (suspend to disk) on Windows or Linux, I experience that on the next boot of Linux, the e2fsck utility runs and reports file system errors. Is there a bug fix or a workaround for it?

When you hibernate (suspend to disk) an operating system, the whole memory of running programs is stored on disk including opened file handles. It is restored on resuming the computer from hibernation. Thus the *Windows boot manager* usually does not offer the boot menu if you have hibernated Windows before, because you are not allowed to boot another OS.

One way of looking at this is that file systems remain mounted and files remain opened when the computer is switched off following a hibernate command.

It is not possible to implement a file system driver which can deal with a file system that is being changed by other operating systems at the same time that it is mounted by the file system driver itself.

It means that you should shutdown Windows before booting Linux and vice-versa. You can use hibernate (suspend to disk) in Windows only if you resume Windows subsequently. Furthermore, you can use hibernate (suspend to disk) in Linux only if you attempt to resume Linux subsequently. But you cannot mix the two operating systems. [/QUOTE]

There ya go

---

### Post by steelklvr on 2007-10-26
Excellent, thanks for your help.

Thankfully it's an easy fix.

---

### Post by kelbizzle on 2007-10-26
your welcome brothers, don't forget to mark your thread [solved]("http://ubuntuforums.org/showthread.php?t=578430&highlight=marking+threads+solved.")

---


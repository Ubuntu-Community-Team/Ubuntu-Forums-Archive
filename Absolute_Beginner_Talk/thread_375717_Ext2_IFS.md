---
title: "Ext2 IFS"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by NaCl on 2007-03-04
I tried using Ext2 IFS so Windows can read and write data on my Ext3 partition. When I transferred some file with Chinese filename to the Ext3 partition, all the part of the filename with Chinese characters turned ???. Is there a way to make it work? So I am just using a shared FAT32 partition for now.

---

### Post by kelbizzle on 2007-03-04
[QUOTE=http://www.fs-driver.org/troubleshoot.html] When I access to an Ext2/Ext3 volume on Windows, file names with language-specific characters appear distorted.

It is probably caused by an activated UTF-8 encoding in your Linux installation. You may check it by the locale tool (on Linux):
locale
When it outputs something, which ends with "utf8" in the line "LC_CTYPE=", UTF-8 encoding is enabled. Unfortunately, the current version of the Ext2 IFS software does not support UTF-8 encoded file names. (The driver always uses the current code page of Windows.) [/QUOTE] there ya go.

---

### Post by NaCl on 2007-03-04
Okay, thanks.
But what does it mean by "The driver always uses the current code page of Windows."

Since ext2 ifs doesn't support unicode, is using fat32 or writing ntfs drives on linux the only solutions?

---

### Post by feistybird on 2008-07-08
> **NaCl said:**
> Okay, thanks.
But what does it mean by "The driver always uses the current code page of Windows."

Since ext2 ifs doesn't support unicode, is using fat32 or writing ntfs drives on linux the only solutions?

Now it does: 

[http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html)
> Ext2 Installable File System 1.11

Detailed list of changes:

    * Now offers support for Windows Vista/Vista x64 and the x64 versions of Windows XP and Windows 2003 Server. Includes drivers with a digital signature for Windows Vista x64.
    *** UTF-8 encoding added.**
    * Global read-only option added.
    * Support for hash indexed (htree) directories added (utilizes the so-called dir_index feature).
    * New configuration components for creation and deletion of any drive letter that greatly improves the plug-n-play functionality. When a drive is removed, the corresponding drive letter is deleted. Configuration of drive letters using the Windows mountvol utility is now supported (except on Windows NT 4.0).
    * File names that start with a dot "." character are treated as hidden.
    * Supports GPT disks if the Windows version used also does.
    * Bug fixed that, on rare occasions, caused the computer to hang up on opening of directories.
    * Bug fixed that prevented the Ext2 driver from supplying the FILE_ATTRIBUTE_NORMAL attribute flag for files that lack an attribute value.
    * Bug fixed that had as an effect that opening of a file or directory was not denied if its disposition information is set (delete pending).
    * Bug fixed that could cause a blue screen upon removal of a drive.
    * Bug fixed that had as an effect that the volume was not upgraded correctly upon writing a file larger than 2 GB.

operating system: 	Windows NT 4.0/2000/XP/2003/Vista (both x86 and x64 platform)
release date: 	01-28-2008
size 	1.38 MB
file: 	[Ext2IFS_1_11.exe](http://www.fs-driver.org/download/Ext2IFS_1_11.exe)

---


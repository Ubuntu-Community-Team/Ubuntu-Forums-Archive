---
title: "Viewing files from another OS partition"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by pcostanza on 2007-03-12
I have a Vista/Ubuntu system and don't have any idea how to play the music files in Ubuntu that are on the Vista partition.  I can see my network but there is nothing there when I click on it. I read some where that I have to 'mount' the windows partition but I don't know what that means or how to do this.  
Is what I want possible?

---

### Post by overdrank on 2007-03-12
> **pcostanza said:**
> I have a Vista/Ubuntu system and don't have any idea how to play the music files in Ubuntu that are on the Vista partition.  I can see my network but there is nothing there when I click on it. I read some where that I have to 'mount' the windows partition but I don't know what that means or how to do this.  
Is what I want possible?

Hi let me see if I understand you, you have a windows system and a ubuntu system networked? Or do you have a dual boot system on one computer?

---

### Post by crispy_420 on 2007-03-12
It sound like dual boot to me. Then you need to have the proper drivers to read the Win partition. I don't have Vista but I'm guessing it uses NTFS. There are some drivers that work at a risk of messing up the file system. Sure people say they are stable but if you browse the forums you will find many people that have trashed their file system (eg. drive not recognized). 

If you have the space to spare, I would create a FAT32 partition. That way you can move files to it that you paln on sharing between the OS's. Or better yet, a removable drive. Be it a USB stick or hard drive.

---

### Post by pcostanza on 2007-03-12
Sorry I wasn't clear.  It's a dual boot Vista/Ubuntu and I'd like to browse to a Vista folder to play music.  Is that doable?

---

### Post by crispy_420 on 2007-03-13
Depends on a few items.

First what is Vista's native files system, NTFS? If so then there are drivers to be able to mount that format. I would look at being able to read only. Why? I have read to many posts about people that used alpha/beta software to provide read/write, and have lost all. Just search these forums for ntfs.

Also what format for music? You have to make sure you have a supported format or the option to install the correct codecs (mp3, ogg, etc.).

---


---
title: "Do I need to do anything special to move MP3's from Ubuntu 7.10 to a NTFS partition?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-03-31
Hi,

I am using Soundcoverter to change M4a's to Mp3's.  When I copy them to windows & check the folder size, the size windows reports is incorrect.  When I try to move the files to another directory, I get an error message that says I cant.  

Are Linux made MP3's not compatible with NTFS?  

I make them in Ubuntu, then copy them to my NTFS partition in ubuntu.  When in windows it doesnt allow me to move it for some reason.  

It says cannot read from the source disk.  It is a NTFS partition that has windows installed on it.
Any ideas?

Thanks,
Rich

---

### Post by Cypher on 2008-03-31
You are going to notice a difference in the reported sizes of files between Linux and Windows and that has to be do with the native filesystem differences. The way EXT3 and NTFS deals with files with their overhead is the reason, but that shouldn't necessairly cause any problems.

Once you copy the files from Linux to Windows, as the Windwos user you should have full access to it and should be able to do what you want within Windows as there shouldn't be a lock on the file anymore. 

Nothing about MP3s made in Linux should make them incompatble on any other device/OS.

---

### Post by NR1224 on 2008-03-31
that is an interesting way of moving files, what i did was create a 10gb fat32 partion with gparted and copied all my music to it so that windows and linux can use them

---

### Post by forrestcupp on 2008-03-31
That's strange because I store all of my mp3's from Ubuntu on my Windows NTFS partition and don't have any trouble.

Do you use Vista?  If so, I have a sneaking suspicion that it has to do with Vista's crappy UAC and security features.  I had similar problems and I found 2 solutions.  1. If you just put your files in somewhere in your user folder, that doesn't happen because you have permission to do anything you want there.  2.  I disabled the UAC and all of that, and I never had trouble again.

---

### Post by stchman on 2008-03-31
> **RichTJ99 said:**
> Hi,

I am using Soundcoverter to change M4a's to Mp3's.  When I copy them to windows & check the folder size, the size windows reports is incorrect.  When I try to move the files to another directory, I get an error message that says I cant.  

Are Linux made MP3's not compatible with NTFS?  

I make them in Ubuntu, then copy them to my NTFS partition in ubuntu.  When in windows it doesnt allow me to move it for some reason.  

It says cannot read from the source disk.  It is a NTFS partition that has windows installed on it.
Any ideas?

Thanks,
Rich

No, you need to install the ntfs-3g package.  This will allow you to write to NTFS partitions.

I have a write up on partition mounting and fstab editing.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

MP3s are MP3s no matter what filesystem you are on.

---

### Post by english on 2008-03-31
Hi

I have no problemo's with this.

 I create mp3s using SoundKonverter storing them on my Ubuntu install then I manually move them to my windows install and they play fine i guess you're converting directly to the windows partition.

Good Luck

---

### Post by RichTJ99 on 2008-03-31
Hi,

I am using XP Pro.  Though it is on a dual boot (make that tripple boot system).  I have XP, Vista & Ubuntu.  The files were made in ubuntu, then copied to the XP partition, while in Ubuntu.  The problems started when I booted into XP & tried to access the files.

Interestingly enough, the file count is different in XP vs Ubuntu (on the same files).  Size is different too (but that makes sense).

---

### Post by RichTJ99 on 2008-03-31
I think some of my issues are related to how Linux makes the MP3 file name (adding * or ? or other characters into the name).  Windows cant handle that at all.

---

### Post by forrestcupp on 2008-04-01
> **RichTJ99 said:**
> I think some of my issues are related to how Linux makes the MP3 file name (adding * or ? or other characters into the name).  Windows cant handle that at all.

It must be the software you're using.  I've never run into that before.

---

### Post by RichTJ99 on 2008-04-02
I ended up using Easytag for the renaming & then copying to a Fat32 drive, then copying over to windows & everything is fine.

---


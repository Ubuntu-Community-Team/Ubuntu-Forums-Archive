---
title: "finding windows files?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by StageMgr2Stars on 2006-02-21
So I was discussing with a friend about how I wanted to transfer all my music over to my linux os (I am dual partitioned on the c:) from xp. He told me that there is a way to find your xp stuff on linux. Is there really a way to get my files on XP while using linux?

---

### Post by aysiu on 2006-02-21
Sure. See the fourth link of my signature.

---

### Post by StageMgr2Stars on 2006-02-21
[QUOTE=aysiu]Sure. See the fourth link of my signature.[/QUOTE]
I dont know what mounting is or how to use it... what is it?

---

### Post by aysiu on 2006-02-21
[QUOTE=StageMgr2Stars]I dont know what mounting is or how to use it... what is it?[/QUOTE] "Mounting" is basically like creating a Windows "shortcut" or a Mac "alias" for a partition.

If you "mount" your Windows partition at /home/stagemgr2stars/windows, you can just open up your file browser and go to your Home folder and click on a folder there called *windows* and you'll see your Windows files.

---

### Post by abhaysahai on 2006-02-22
[QUOTE=StageMgr2Stars]So I was discussing with a friend about how I wanted to transfer all my music over to my linux os (I am dual partitioned on the c:) from xp. He told me that there is a way to find your xp stuff on linux. Is there really a way to get my files on XP while using linux?[/QUOTE]

If you are using Ubuntu there will be an icon on your desktop ( something like hda1 or  hda2) these are the windows partetion that ubuntu has mounted for you. Well if the windows partetion is NTFS then you might need to use sudo to access the files. 

In gnome-terminal you can see all the files in /media/hda1 ( or whatever is the hda number) 

If you are using SATA hard disk the partetion will be /media/sdaX

---

### Post by StageMgr2Stars on 2006-02-22
[QUOTE=aysiu]"Mounting" is basically like creating a Windows "shortcut" or a Mac "alias" for a partition.

If you "mount" your Windows partition at /home/stagemgr2stars/windows, you can just open up your file browser and go to your Home folder and click on a folder there called *windows* and you'll see your Windows files.[/QUOTE]
I messed it up :-/ I unmounted both hda1 and hda2... I think it was on 2... bah. I got lost where I had to re-write that stuff. is there a simpler way to do this or can you explain it better to me? now I have 2 unmounted hdas :(

---

### Post by StageMgr2Stars on 2006-02-22
Q: How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4. To mount Windows partition

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

   5. To unmount Windows partition

sudo umount /media/windows/



I found that here :[http://ubuntuguide.org/#accessnetworkfolderswihoutmount](http://ubuntuguide.org/#accessnetworkfolderswihoutmount)

and thats worked but I dont have hda1 or 2 listed anymore. but it did work b/c its all in the windows folder

---


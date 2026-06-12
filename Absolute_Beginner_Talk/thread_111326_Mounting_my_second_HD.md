---
title: "Mounting my second HD"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-02
I've just about got Ubuntu up and running, but...

I'm running it from a small hard drive (hdd1).  My data is all on a larger drive (hda1) which is also my Windows boot.  I can get at the data by mounting hda1 to a folder, from the terminal.

But I don't want to do that.  I'm a simple soul and like nice, friendly GUIs.  So...what do I have to do so that:

[LIST][*]hda1 is permanently mounted on startup - and stays mounted.
[*]It shows up as a storage device icon in Computer
[*]It shows up within Nautilus
[*]It is available as a location in Browse dialogs within applications[/LIST]

...in other words <blush>...so that it works the same as in Windows.

Oh...and at the risk of scorn from the Linux mafia ;) ...I'd *prefer* to be able to do this configuration via a GUI.

---

### Post by diggs on 2006-01-02
oooh! oooh! me too! I wanna know!

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=Edward The Bonobo]I've just about got Ubuntu up and running, but...

I'm running it from a small hard drive (hdd1).  My data is all on a larger drive (hda1) which is also my Windows boot.  I can get at the data by mounting hda1 to a folder, from the terminal.

But I don't want to do that.  I'm a simple soul and like nice, friendly GUIs.  So...what do I have to do so that:

[LIST][*]hda1 is permanently mounted on startup - and stays mounted.
[*]It shows up as a storage device icon in Computer
[*]It shows up within Nautilus
[*]It is available as a location in Browse dialogs within applications[/LIST]

...in other words <blush>...so that it works the same as in Windows.

Oh...and at the risk of scorn from the Linux mafia ;) ...I'd *prefer* to be able to do this configuration via a GUI.[/QUOTE]

You can't have all you want (aka it won't show up as a storage device in the "Computer" - its in your media file- and you can't add it using a GUI) but here are the directions to be able to read (impossible to write to) a NTFS partition:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Sorry if it involves editing some config file with the command line- that is the reality.

---

### Post by trueboy on 2006-01-02
Here is the answer.... fasten in to your seat belt....

first you need to create somewheree to "mount" your second hard disk (for me that was by creating a directory called /mnt/F-Drive)
You then need to modify the file /etc/fstab and tell it about your second hard disk

Here is a sample from my /etc/fstab file where I set it up on miy computer (Note I have only set it up to be "read only" as I do not trust writting to NTFS)

/dev/hda1       /mnt/C-Drive    ntfs    ro,users,umask=002  0       0
/dev/hdb1       /mnt/F-Drive    ntfs    ro,users,umask=002  0       0

You can repace the ntfs with "auto" and make the linux guess what the file system is (it get's it right most of the time).

I hope this helps.

---

### Post by Edward The Bonobo on 2006-01-02
Thanks...but I'm sceptical...

So...there was no advantage to me in making the move over to Linux after '98 became unstable just one time too often?:confused: 

I'd intended to keep my main (Windows) disk going while I got the hang of Ubuntu.  But...basically I now have a big disk sitting there that I can read from...provided I'm willing either to type a mount command every time or to edit scary files I've never even heard of....but still won't be able to write to?  Damn!  I'd imagined the transition might be more user-friendly!

Any other ideas?  The HD will be FAT32 if it's any help.

---

### Post by rwt on 2006-01-03
check your help files
5.10 starter guide/windows partitions has all the info you need

---

### Post by Suger on 2006-01-04
Open a terminal, type sudo fdisk -l and type the result here. If you were in Win 98, I seriously doubt you're harddisk would be in ntfs, must be in fat32

---


---
title: "I need to uninstall ubuntu"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by IsleOf on 2007-06-08
Im selling My PC to a mate and getting a laptop. He uses My PC a lot anyway and wants me to keep my programs on it but remove Ubuntu first.

My XP disk when i go into automated recovery mode asks for a floppy disk. I dont have a floppy disk drive nevermind a floppy disk. I cant get by this point. How else can i sort out my MBR. Problem being ive already went ahead and formatted the two Ubuntu partitions #-o. I dont want to switch my computer off in case it doesnt boot.

---

### Post by original_jamingrit on 2007-06-08
Does it boot with GRUB?

---

### Post by IsleOf on 2007-06-08
I havent tried it yet. Too scared in case it does not boot at all. Should Grub still work?

---

### Post by Bohlio on 2007-06-08
I think grub is on your "/" partition. If you formatted that ext3 partition, you probably wont be able to run grub. I know once you get into windows you can type "fixmbr" or somthing like that into the command prompt... but i dont know how you'd get into windows...

---

### Post by original_jamingrit on 2007-06-08
It may try to work, but then act funny because you formatted your drives.  (Your GRUB files are on the drives you formatted, so it will only start to boot with GRUB and then give you an error).

One way of resurrecting the MBR is to download/burn a bootable MS DOS cd, and then type (note the space)

```
FDISK /MBR
```

at the DOS command prompt.  This will remove GRUB from your MBR and set it up to boot your windows partition like it would before Ubuntu was installed.

There may be an easier way of doing this in GRUB, but I'm not aware of it.

After all that, you should *probably* be able to get back into windows.  Wait untill someone else agrees with this method first, because I'm not totally sure it will work fine.

---

### Post by original_jamingrit on 2007-06-08
Sorry for the double post again, my last one today.

go to [http://www.allbootdisks.com/download/iso.html](http://www.allbootdisks.com/download/iso.html), and look at the list for a bootable DOS disc image download.

---

### Post by Kibe Frito on 2007-06-08
Boot with your Windows CD and at the recovery console type FIXMBR. It will clear your MBR.

---

### Post by Kibe Frito on 2007-06-08
Or FIXMBR I guess...

---

### Post by IsleOf on 2007-06-08
Cheers guys.

Problem using the windows installation recoverry mode is after i try to get to it it asks me for a bootable floppy. I havent got a floppy drive nevermind disk 

Will look into the other methods

---

### Post by Kibe Frito on 2007-06-08
Don't use the automated mode, press R for the console and type the command. It should not ask for any disk at all.

---

### Post by IsleOf on 2007-06-08
> **Kibe Frito said:**
> Don't use the automated mode, press R for the console and type the command. It should not ask for any disk at all.

You know i was just going to ask if automated recovery is the same as hitting 'r' and going to recovery?
Cheers for that.:D

---

### Post by IsleOf on 2007-06-08
Sorted. The XP disk i was using didnt have a recovery mode in it for some weird reason. Luckily i found another one.

Thanks. I shall be back in a few weeks with a new laptop and a fresh set of problems:D

---

### Post by stchman on 2007-06-08
> **IsleOf said:**
> Im selling My PC to a mate and getting a laptop. He uses My PC a lot anyway and wants me to keep my programs on it but remove Ubuntu first.

My XP disk when i go into automated recovery mode asks for a floppy disk. I dont have a floppy disk drive nevermind a floppy disk. I cant get by this point. How else can i sort out my MBR. Problem being ive already went ahead and formatted the two Ubuntu partitions #-o. I dont want to switch my computer off in case it doesnt boot.

So are you wanting to get rid of Ubuntu and reinstall XP?  If so then boot up the install CD of XP and it will allow you to fdisk the drive.

As far as keep your programs what does that mean?  Do you dual boot this PC with XP and Ubuntu.  If that is the case you will need a Win98 boot disc and run fdisk /mbr to clean out the MBR.

---


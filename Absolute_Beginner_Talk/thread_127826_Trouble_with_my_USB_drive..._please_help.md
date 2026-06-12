---
title: "Trouble with my USB drive... please help"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by NewGroove on 2006-02-09
Hi, hoping someone can shed some light on my problem... right after I installed Ubuntu and rebooted, I inserted a Sandisk Cruzer Mini USB drive and an icon appeared on the desktop. Wonderful!

Ever since then however, when I insert it nothing happens. I can mount the drive to something such as /mnt/removable using this command I found on another post:

sudo mount /dev/hda2 /mnt/removable -t vfat -o iocharset=utf8,umask=000

It was much more convenient the other way however. Now, if I click on Places > Computer, I can see the drive sitting there next to the CDRom drives and filesystem. Clicking on the USB drive icon gives me the message "Unable to mount the selected volume. Error: given UDI is not a mountable volume." Right-clicking on the drive and then the permissions tab tells me that it's owned by root, but neither the owner, group or others can write/execute anything with it. It says at the bottom of the permissions tab that I'm not the owner, so I can't change these permissions.

Can anyone help me know what's wrong? Does this have to do with why the drive won't appear on the Desktop anymore? How do I change permissions on something like this. Thanks so much for your help!

Mike

---

### Post by Mustard on 2006-02-09
If you mount the drive on a directory in /media it should still show up on Desktop.  For example /media/removeable

I'm no expert on this, but have just learnt a few things from experiencing similar issues as yourself.  Breezy Badger users have been having quite a few problems with USB devices not automounting, so your problem might just be an extension of that.  Someone might come along with better advice later, but I reckon I could fumble my way through some ideas on how you could get it functioning. :)

First of all I would create a mount point in /media...

```
sudo mkdir /media/removeable
```

Then I would attempt to mount it manually on that mount point.

My USB drive is mounted using this command...

```
sudo mount -t vfat /dev/sda1 /media/usbdrive -o user,uid=1000,gid=1000
```

For you its going to be different as your device name is /dev/hda2 and your mount point is now going to be /media/removeable.  The uid and gid values tell the system that the device can be read by that particular userid and groupid.  By default you should be uid 1000 and gid 1000, as its the id assigned to the first user created on the system.  

I wonder if you could paste the output of this command in this thread...with your usb drive plugged in.

```
sudo fdisk -l
```

Thats going to show all the partitions on your system.  You can enclose it in this forum code to make it look neat in the post.. [noparse]```
..your code in  here...
```[/noparse]

Something you might like to look into, is that in the System>>System Tools>> Configuration Editor there is a setting in there somewhere (I haven't been able to find it lately), which controls which things appear on your desktop.  I don't know whether this has been changed at any stage on your system, but it might be worth having a look.  Unfortunately I can't remember where it is exactly. :)

As for the automounting problem.  I'm still looking for a good solution myself.  I haven't seen one lately.

---

### Post by firenurse4 on 2006-02-09
I had similar problems before (I had the same error message you are reporting) and it was with a dameon called Gnome Volume Manager. I wound up fixing it by completely removing the dameon resarting and the reinstalling it.  Since then it has worked without a problem.

---

### Post by Mustard on 2006-02-09
[QUOTE=firenurse4]I had similar problems before (I had the same error message you are reporting) and it was with a dameon called Gnome Volume Manager. I wound up fixing it by completely removing the dameon resarting and the reinstalling it.  Since then it has worked without a problem.[/QUOTE]

I'm just trying that out myself.  I notice that its removing ubuntu-desktop too, which I know is pretty harmless unless you are doing an dist-upgrade, but I might try and reinstall that afterwards.

---

### Post by Mustard on 2006-02-10
Hmm..no luck with reinstalling gnome-volume-manager.  Its not recognising my USB drive at all at the moment, but its been a while since I have tried to connect it.

-edit-

Heh..well its working now that I realised I was plugging the wrong connector into my USB hub. :)  So I would say the gnome-volume-manager thing is definitely something worth trying. I'd reinstall ubuntu-desktop again though afterwards.  If you don't have ubuntu-desktop installed when the final release of dapper comes out and you try a dist-upgrade, its going to cause some problems I would think.

---

### Post by atoponce on 2006-02-10
[quote=Mustard]Hmm..no luck with reinstalling gnome-volume-manager.  Its not recognising my USB drive at all at the moment, but its been a while since I have tried to connect it.

-edit-

Heh..well its working now that I realised I was plugging the wrong connector into my USB hub. :)  So I would say the gnome-volume-manager thing is definitely something worth trying. I'd reinstall ubuntu-desktop again though afterwards.  If you don't have ubuntu-desktop installed when the final release of dapper comes out and you try a dist-upgrade, its going to cause some problems I would think.[/quote]

Just a question:  what brand of computer are you using?  On my HP laptop, sometimes the USB will work, and sometimes not.  I have to unplug and plug back in, or alternate USB ports before I can get the device to work, regardless of OS.  Just curious.

---

### Post by Mustard on 2006-02-10
I'm on a desktop machine.  It's an AMD chip on a Soltek motherboard. I've never updated the BIOS either. :)

```
 *-core
       description: Motherboard
       product: 75FRV
       vendor: SOLTEK
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.0
          slot: Socket-A
          size: 1800MHz
          capacity: 3GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow

```

Just for everyones information.  I've booted up today and the drive is not on my desktop. I'll just unplug it and plug it in again....yep...it comes up now.  Its so hit and miss. :)

---


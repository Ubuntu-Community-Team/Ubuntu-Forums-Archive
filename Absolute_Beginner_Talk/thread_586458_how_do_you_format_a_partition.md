---
title: "how do you format a partition?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Narv on 2007-10-22
Hi,  I made a mistake when I was upgrading feisty to gutsy, and now have both of them on my laptop and its subsequently running slowly and I want to get rid of one of them.

It doesn't have an internet connection, so I did it from CD.  I've been told I can format a partition, but I can't see how you do that and I've spent ages looking through the menus.  I'd be really grateful if someone could explain it to me in basic terms.

Cheers

---

### Post by hyper_ch on 2007-10-22
use the manual partitioning.

Once you're in there, you'll see the primary and logical partitions. The one you want to format, select it with the arrow keys and then press enter.

Then you can set the file system format (ext2/3, swap, encrypted, ...) and the mounting point and also whether it shall be formatted.

---

### Post by Narv on 2007-10-22
ok, thanks.  But how do I get into the manual partitioning bit?  Is there a menu somewhere?  Or is it before its booted up?

---

### Post by hyper_ch on 2007-10-22
You are not isntalling it? I mean you have it already installed?

---

### Post by Narv on 2007-10-22
Sorry if I'm not being clear.  

Yes, I have both versions installed.  I've only started using Ubuntu recently, so I'm still finding my way round.  I just don't know where to find the manual partition thing.

---

### Post by mikeyphi on 2007-10-22
> **Narv said:**
> Hi,  I made a mistake when I was upgrading feisty to gutsy, and now have both of them on my laptop and its subsequently running slowly and I want to get rid of one of them.

It doesn't have an internet connection, so I did it from CD.  I've been told I can format a partition, but I can't see how you do that and I've spent ages looking through the menus.  I'd be really grateful if someone could explain it to me in basic terms.

Cheers

Just confirm that you installed Gutsy instead of upgrading to Feisty?
Have you got a LiveCD?
To delete a partition you need to run gparted or equivalent. Without an internet connection you need this on a CD. I believe it's on the LiveCD

---

### Post by hyper_ch on 2007-10-22
well, install gparted:

```

sudo apt-get install gparted

```

That's a graphical partition editor.

It will list all your disks and their partitions.

Then, I think the one you want to format/delete is already mounte, you'll have to find the device designation of that drive in gparted. It will most likely be something like  /dev/sdaX

Once you have that, you need to unmount that partition. Otherwise gparted can't do anythign with it:

```

sudo umount /dev/sdaX

```

Once unmounted, you can have it fromat from gparted or delete that partition and enlarge another one with the free space)

---

### Post by stella2657 on 2007-10-22
hi, not all installed programes show up in the menu, check - system, preferences, main menu first and see if the box is ticked -if not search synaptic and install.

---

### Post by Narv on 2007-10-22
MikeyPhi, I was upgrading from feisty to gutsy.  But instead of just upgrading, I now have both of them.  That would be fine, but the machine is running too slow now.

hyper_ch, thanks for the advice.  But that sounds like I have to download gparted.  The laptop doesn't have an internet connection.  Is it possible to download it and burn a cd?

---

### Post by Narv on 2007-10-22
Mikeyphi, I missed the bit where you mentioned the Live cd.  Yes, i do have one of those, so I'll try that later.

Cheers guys.

---

### Post by Paqman on 2007-10-22
Since you don't have an internet connection, you won't be able to get Gparted, which is what you'd normally use.

However, you could just reinstall using the disk you have. Except this time get rid of the partitions you don't want.

---

### Post by Narv on 2007-10-22
Sounds like a good idea.  I'll give it ago.

---

### Post by ADK1 on 2007-10-23
Hey everyone,

I'm kind of new to Ubuntu and have a similar problem... I'm unsure of myself, so I'm asking for help. Here's my situation:

I have 5 partitions according to the Gusty liveCD partition editor:

NTFS - 74gb
ext3 - 70 gb
ext3 - 2.04gb
extended - 1.59gb
linux-swap - 164 Mib
linux-swap - 1.42 Mib

I'd like to keep the NTFS, and get Gusty running on the rest of the drive. I'll give you the background story in case it's helpful:

3 months ago I installed xp, then Feisty, dual partition style. XP had a breakdown and I had to reinstall it, which defuncted Grub as the default OS chooser (it went straight into windows). So I followed a guide that helped re-instate Grub. It worked. (I'm not sure if that's an important bit of the story)

Then when Gusty came out, I tried to format the partition Feisty was using so that it could be a fresh version of ubuntu... I tried to do that by selecting the 70gb ext3 partition (in the Gusty installation process) and extending the slider to 100%.

But when I boot, GRUB loads and gives me the exact same options I had before installing Gusty. It's as if it wasn't even there. I don't really know what to do... I just want a dual boot XP/Gusty machine but I don't know what to do to achieve that.

Thanks for any help!

Alex

---

### Post by bigboy_pdb on 2007-10-23
Narv, if all you want to do is reformat the partition then you can use the command "mkfs.ext3 -L *label_name* *device*" where *label_name* is the name that you want to be displayed when the drive is mounted and *device* is the device for the partition. Use "mount", "df", "sudo fdisk -l" or "gedit /etc/fstab" to figure out which device is the one that you want to delete and if it is mounted. If it is mounted then if there is an icon for the drive, you can right click it and select unmount, or if there is no icon, you can use the command "sudo umount *device*". You can then use the "mkfs.ext3" command to reformat the partition.

ADK1, you should be able to use the LiveCD to remove those partitions, but if you're having a lot of trouble then you can use "fdisk" to delete the partitions.

**NOTE**: You can get out of "fdisk" without changing the partitions by entering "q", and entering "m" produces a list of commands and the letters that can be entered to use them.

You can do this by typing "sudo fdisk *device*" where *device* is the hard drive that you want to delete the partitions on. If you only have one hard drive then it should be either /dev/sda or /dev/hda (you can use "sudo fdisk -l" to list your hard drive information). For example, if your first hard drive is /dev/sda then you'll want to type "sudo fdisk /dev/hda". Once you've run "sudo fdisk *device*", enter "p" to print your partitions. Enter "d" to delete partitions and type the numbers of the partitions that you want to delete. For example, if you want to delete the partition for /dev/sda6 then type "d" (and hit enter) and type "6" (and hit enter). Type "p" to list your partitions to make certain that you haven't deleted the Windows drive. If you're unhappy with the results enter "q" to "quit without saving changes", otherwise enter "w" to "write table to disk and exit".

---


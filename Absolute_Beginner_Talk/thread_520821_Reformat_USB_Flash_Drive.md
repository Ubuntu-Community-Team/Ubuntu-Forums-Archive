---
title: "Reformat USB Flash Drive"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-08-08
I am trying to reformat my USB Flash drive, because it is giving me problems with readonly again, so I want to make it ext3 via GParted, but the big problem is, it won't format it.

I unmount the volume, and select Format > ext3
I then click apply, it asks for confirmation, I click Apply, the drive remounts and then gives me an error in Gparted stating that it can not reformat the drive.

 I don't know what to do, and I really need to try reformatting it...

Thanks,
Dr Small

---

### Post by Hospadar on 2007-08-08
I'm not sure about this, but I think that many flash memory devices can only be formatted with certain filesystem types.  I used to have a flash drive that only supported fat32.

If you are just trying to clean the drive off, try reformatting it fat32 and see what happens.

---

### Post by Dr Small on 2007-08-08
Same exact thing. It attempts to reformat it, and right before it does it, it auto-mounts and gives it an error. I've formatted this same usb drive to ext3 once before to erase it, but now it seems like I can't...

---

### Post by ayenack on 2007-08-08
In GPareted delete the drive first then apply then try to re-format and see if this makes any difference.

If the above did not work you can do this. From Terminal. Make sure that the drive is unmounted.


sudo unmount /dev/sda1 (where /dev/sda1 is your usb drive)

To Format it.
sudo mkfs.ext3 /dev/sda1 (where /dev/sda1 is your usb drive)


If you want to give it a label.
sudo e2label /dev/sda1 your-label (where /dev/sda1 is your usb drive)

If you don't know where your USB device is type this and it'll list your drives.

sudo fdisk -l

From terminal you can use fdisk to create partitions or delete partitions etc. If you type m when in fdisk it will display your options.

sudo fdisk /dev/sda1 (where /dev/sda1 is your usb drive)

---

### Post by Wiebelhaus on 2007-08-08
Install ntfs-3g & gui from package manager & setup to read/write settings at boot

Install gnome partition manager from add/remove and use that to format it in fat32 for cross platform use.

---

### Post by Hospadar on 2007-08-08
Is the drive mounting as read-only? if that's the case you wouldn't be able to format it.  are you running gparted as root? (with sudo).

---

### Post by Dr Small on 2007-08-08
Umm, how would I be able to reformat the drive if I deleted it?
I don't want to do anything to make my usb worse off.

---

### Post by Dr Small on 2007-08-08
I tried deleteing it, and then making a new ext3 partion, or whatever, and the same thing happened....

---

### Post by Wiebelhaus on 2007-08-08
> **Dr Small said:**
> I tried deleteing it, and then making a new ext3 partion, or whatever, and the same thing happened....

what's the exact error?

---

### Post by ayenack on 2007-08-08
To change permission on the drive type this in terminal.

gksudo nautilus

Then navigate to the drive right click it and select permission and then your user name.

---

### Post by Dr Small on 2007-08-08
It says I have permissions, and I've done that sort of thing many a times, but it doesn't help. It's like the drive is readonly, so back to basic problem 1. How can I reformat it, because it keeps giving me an error, because it keeps auto-mounting it while trying to reformat it.

Dr Small

---

### Post by Dr Small on 2007-08-08
[SOLVED]
(I'll change the topic after I make my post)

Here's how I solved it.

I looked at the occurance of events, and saw that it was auto-mounting the drive while formating it, cause the error because it was mounted. I have no idea why it did this, but that's just the way things happened. 

So, I edited my user account and made it so I couldn't access external devices and logged off.
(System > Administration > Users & Groups > [username] > Properties > User Privilages > [Uncheck] Enable Access to external devices automatically)

Then I plugged in my USB after I logged back in, went to GParted, selected the drive, and reformatted it. It worked perfectly, I went back through the settings, and checked the option that I unchecked in my account, logged back off, logged back in. Plugged the USB in again and then it worked.

That seemed to be a work around for the auto-mounting problem, while it tried to reformat the drive.

Dr Small

---


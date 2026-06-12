---
title: "Boot ubuntu from thumbdrive"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by sheshbabu on 2006-08-12
Hello all!
         I'd like to carry ubuntu along wherever i go,but i dont want to carry the live cd,so i need to know whether i could install ubuntu on a thumbdrive and boot it [COLOR="Gray"](from the thumbdrive)[/COLOR] on any computer and use it.

---

### Post by Tomosaur on 2006-08-12
It's possible, if the PC you plug into is able to boot from USB.

---

### Post by sheshbabu on 2006-08-12
> **Tomosaur said:**
> It's possible, if the PC you plug into is able to boot from USB.

so can i keep my other files(text,pics,music..) along with the OS file?

---

### Post by Tomosaur on 2006-08-12
Not unless you partition your thumb drive. You will need to actually install the OS to the thumb drive, which requires formatting it to ext2 or ext3.

---

### Post by sheshbabu on 2006-08-12
> **Tomosaur said:**
> Not unless you partition your thumb drive. You will need to actually install the OS to the thumb drive, which requires formatting it to ext2 or ext3.

so,do i have to format my thumbdrive before installing ubuntu?, cant i just keep the OS files and other files side by side?:confused:

---

### Post by Tomosaur on 2006-08-12
You need to create a partition in your thumb drive which is formatted as ext2 or ext3. You may also need a swap partition. If your thumb drive has a large enough capacity, you can keep all your existing files in a partition of their own, but to install linux on it, you will need to give it its own partition, which, depending on how large your drive is, may mean you need to scrap all the existing files.

You may want to consider DSL (Damn Small Linux) for this, since the size of it is...well, damn small, and you're much more likely to be able to keep your existing files.

---

### Post by sheshbabu on 2006-08-12
> **Tomosaur said:**
> You need to create a partition in your thumb drive which is formatted as ext2 or ext3. You may also need a swap partition. If your thumb drive has a large enough capacity, you can keep all your existing files in a partition of their own, but to install linux on it, you will need to give it its own partition, which, depending on how large your drive is, may mean you need to scrap all the existing files.

You may want to consider DSL (Damn Small Linux) for this, since the size of it is...well, damn small, and you're much more likely to be able to keep your existing files.

Size is not a problem i think, i've 1gig of space,and one more question- i've read somewhere that the size of the swap space must be atleast double of that of RAM,does this rule apply here too?

---

### Post by Tomosaur on 2006-08-12
That's still the 'recommendation', but it's a lot less vital nowadays. I should think 512mb of swap should be perfectly fine, but again, you'll need to decide for yourself. I still think Ubuntu is NOT the right distrobution for this.

---

### Post by sheshbabu on 2006-08-12
> **Tomosaur said:**
> ....I still think Ubuntu is NOT the right distrobution for this.

But it is very compelling!!!, IMHO other distros dont even come near to its ease of use(alredy tried suse and fedora),anyway thanks for your support :D

---

### Post by UbuWu on 2006-08-13
This is perfectly possible. Instructions for doing this: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Btw. I don't think it is wise to create a swap partition on an usb drive.

---

### Post by C.S.Cameron on 2007-06-08
Just plug it in, go to bios, boot, set as primary hard drive and second to CD in boot order.
(I unplugged the other hard drives first as I was a little nervous).
Inserted the CD and rebooted.
When Ubuntu came up I chose install, 45 minutes later it was done.
Removed the CD, rebooted, and it worked.
It's cool, I have been neglecting my work and family to play with this thing.
I think there are a lot of possibilities,  like installing project folders and specialty applications on other thumb drives, (or other micro chips). 
Cork

---


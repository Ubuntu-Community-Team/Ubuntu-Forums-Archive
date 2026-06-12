---
title: "Uninstalling Xubuntu"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Houli on 2008-03-15
How do I go about completely removing Xubuntu and formatting the drive as FAT32. I want to restore the Windows MBR as well while doing this.

---

### Post by forrestcupp on 2008-03-15
Are you dual booting, or is Xubuntu the only thing on there?

If Xubuntu is the only OS on there, just try installing Windows and it should format the hard drive for you and set up the boot loader.

If you are dual booting, use [the Super Grub disk](http://supergrub.forjamari.linex.org/) to restore the Windows boot loader, and use GParted LiveCD to format your Linux partition to whatever you want.

Sorry it didn't work out for you.

---

### Post by neurostu on 2008-03-15
the easiest way is to just use the windows install cd and have it recover the mbr, (IF you have windows installed)

If not then just install windows!


Use the gparted live cd to reformat the drive!

---

### Post by Houli on 2008-03-15
Cool thanks for your help. I have got another problem though. In the Xubuntu installer around 90 something percent it says a fatal error. It has something to do with GRUB. Got a solution?

---


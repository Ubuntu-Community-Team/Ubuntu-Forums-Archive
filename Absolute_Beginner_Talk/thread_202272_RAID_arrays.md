---
title: "RAID arrays?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Thundercat on 2006-06-23
Hi all,
My second question about Kubuntu...

I have a RAID card in my mahcine with 6 drives configured in RAID 5. It is set up and works under WinXP but doesn't appear in the storage media window under kubuntu. 

It does show in the drive manager thing, but it shows each of the individual drives, and 2 of them show a volume they are listed there as hde1 and hdj1 
on the text part of bootup it showed some errors regarding the disks in the array, I didn't make a note of the errors yet, but just wanted to ask for any general advice for now regarding RAID arrays under kubuntu??

I'm typing this from work so apologies for my vagueness, I will provide more details when I'm at home but it will help if people can ask me specific questions because I don't really know what info to provide...

---

### Post by chrestomanci on 2006-06-23
Most likely it is software raid that just provides some IDE interfaces, and releys on the windows driver to do all the parity calculations and present it as a single volume. There is linux software avalable to do the same thing, but you will not be able to share the volume with windows in a dual boot system.

Alternatively, you could buy a hardware raid card, that will do the parity calcualtions onboard, and present a single volume to any OS. The price of XFX cards have droped, and get good reviews.

---

### Post by Apple 101 on 2006-06-23
When you boot from the install CD/DVD, isn't there an option for RAID in one of the menus?  In the desktop, open the menu bar, and there will be an option there too (I think)..

---

### Post by Thundercat on 2006-06-23
It is a seperate raid card that hosts the drives, The array is all configured through a BIOS interface (seperate from the Motherboards BIOS)
I will make a note of the messages that came up about the RAID disks on startup, they might be something to do with it.

---

### Post by clarkth on 2006-06-23
[QUOTE=chrestomanci]The price of XFX cards have droped, and get good reviews.[/QUOTE]
What are some other hardware raid cards that will work with Ubuntu (either 5.10 or 6.06)?

---


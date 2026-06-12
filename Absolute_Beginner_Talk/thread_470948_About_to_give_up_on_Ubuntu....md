---
title: "About to give up on Ubuntu..."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Bleubear on 2007-06-11
Well I have tried many ways to get this thing to work on my system and I am out of ideas. I am trying to install with the txt version of fiesty due to I have a ATI Xcard. So during the install I get as far as detecting network and then it just hangs. I even let it sit there for 1/2 hour seeing if it would do anything, but nothing. I even ran a memory test as well as a check cd test and the memory passed as well the cd was verified. Any help would be appreciated.

i am running a Athlon 64x2 3800+, asus nforece4 mobo, 2gig ddr400 corsair, ati x800 gto pci-e, wd cav 200gig sata and a matrox 250gig sata(not raided).

---

### Post by edwardLS on 2007-06-11
This sounds very similar to a problem my son was having with an AMD laptop.  He finally figured out a way to get things installed by setting:
     acpi=noacpi (or something to that verbiage)

I am not near his laptop, and he is at work currently so I can't ask him.  If you think that could be your situation, let me know and I will get the exact particulars when I can.

---

### Post by Bleubear on 2007-06-11
where would I set this, still fairly new to the Linux?

---

### Post by edwardLS on 2007-06-11
Again, I am going from memory from a discussion I had with my son about his situation.

I believe he stated that when the Live CD menu comes up right after booting from the CD, he pressed the F11 key, and then he was able to enter additional parameters into the boot string.

---

### Post by Inxsible on 2007-06-11
You can change it in the /boot/grub/menu.lst
At the prompt type in ```
sudo nano /boot/grub/menu.lst
``` 
Change the line acpi to noacpi and see if it works. If that doesn't work, some people have had success by changing it to acpi=off.
 
I am sorry I dont remember the exact format of how the line looks in the menu.lst as I am not on my Ubuntu machine at the moment.

---

### Post by Bleubear on 2007-06-11
Well I tried finding the code line to change acpi to no acpi, all I was able to do is creat a new file through nano and the document was blank. However during this process I was able to find the process that I keep getting stuck on. I got a error when I tried to load debconf preconfigurationfile; it said that it was missing. Could this be due to it was a bad file I downloaded from the mirror site?

---


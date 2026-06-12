---
title: "USB Flash Drive"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by joshb86 on 2007-05-20
Hi. I have a new usb flash drive and i've been trying to get it working. First it would mount and showup on the desktop.... but i couldn't write to it. Then i followed some  steps on these forums and found to format it as fat32. It was default in fat16. SO i used gparted and formatted to fat32. Then it wanted to create a disklabel. The default is msdos. So i went with that.....failed. So then i went through the list and tried all of the options. All of them fail! So i cant do a thing now until it has a label. It appears in gparted as unallocated space.


/dev/sdb


lsusb__

Bus 004 Device 003: ID 1043:8012 iCreate Technologies Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


i can see the drive under computer as generic usb flash drive. But when accessing it i get ...


Unable to mount media
There is probably no media in the drive.




 I appreciate any help. Thanks

---

### Post by PhilJ on 2007-05-20
did you get a cd with it for windows?

if you did and  have windows or can access a windows machine  try reformatting it using its own format program.

I had problems with one I formatted using Ubuntu which afterwards showed up as a cd and I couldnt access it.

Philj

---

### Post by joshb86 on 2007-05-20
I just tried that. Even in windows the drive is unreadable. It appears under my computer as a removable drive... but can't access it and the software it came with can't read it either. Tried a right click> format and it does nothing.


Any other ideas?

---

### Post by hpalma on 2007-06-03
I'm also experiencing this. Any news on how to solve this ?

---

### Post by joshb86 on 2007-06-04
hpalma... mine turned out being a toasted drive after all.

---

### Post by david_kt on 2007-06-04
> **joshb86 said:**
> hpalma... mine turned out being a toasted drive after all.

Follow below steps:
1. Plug in on your linux box
2. Unmount your usb drive (but do not plug out)
3. Use gparted to format to whatever filesystem you want
4. Mount it again and see if you could write on it

DK

---

### Post by Outrunner on 2007-06-04
People usually format their flash drives as FAT16, just thought I'd let you know. I hope it was not mounted while you formatted it(or was it)?

Sorry, i can't offer much advice about this because I don't have much experience with this.

---

### Post by joshb86 on 2007-06-04
Hi david. gparted won't allow me to format it. All it does is ask to create a disk label in which it fails everytime.

---

### Post by joshb86 on 2007-06-04
Yeah originally i now feel like i should have left it alone. But when it was fat16 to begin with i couldn't access or write to it in linux or windows. Something was wrong with mine to begin with i think.

---

### Post by dellboy on 2007-06-04
i would say the flash drive is not working i would take back to whee you got and get a new one

---

### Post by joshb86 on 2007-06-04
I've actually got half of my refund. It came from over seas and they wanted me to ship it back at my cost. Which was almost as much as what i paid for it. They then wouldn't refund me the full amount and only gave me half.

---

### Post by david_kt on 2007-06-04
> **joshb86 said:**
> Hi david. gparted won't allow me to format it. All it does is ask to create a disk label in which it fails everytime.

Are sure you have unmount it? You could also try to use ubuntu live cd to format it. If still fail, it might be really a defective usb drive.

DK

---

### Post by boldexplorer on 2007-07-10
there is one last thing you can try before taking it back. 
If you have a windows machine in the control panel and Administrative tools you may be able to format the drive and create a new partition on the drive thus making it usable again!

---


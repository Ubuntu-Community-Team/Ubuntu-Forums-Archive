---
title: "Floppy and Hard drive questions"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by ComputerPsi on 2007-05-15
I am new to linux, so I am probably doing something wrong. First, the floppy drive - I tried to open it with Ubuntu.. It took the system about a minute to "look" at the floppy (it kept reading the floppy). Then it changed the icon of the drive to a floppy disk. (It was just a white sheet icon before). Then I tried to open it again. Inside, none of the files were visible. It is in FAT12 format. I tried quick formating it. Nothing happened. Now I cannot format it anymore.
Next, I turned off the computer and switched a CD drive with another hard drive. I turned on the computer and Ubuntu wasn't able to show me anything inside of the drive. Do I have to configure something?

Thank You,
ComputerPsi

---

### Post by crispy_420 on 2007-05-16
I assuming a compatible format fith linux right? Then you have to mount it.

---

### Post by Big_Croc7 on 2007-05-16
For the hard disk, can you run the following command with the HD connected and post the output here?
```
 sudo fdisk -l 
```

---


---
title: "Read Only Maxtor One Touch External Hard Drive Help!!!!"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Shivasdance121 on 2007-09-05
Hi! 
I'm new to Linux/Ubuntu. My brother downloaded it onto my computer for me. I haven't had any problem with it except I can't get my Maxtor One Touch External Hard Drive to work. I've browsed through the thread on the same topic and I still can't get it to work (probably because I just don't know what the hell I'm doing). I downloaded NTFS, but it still is read only. Could someone walk me through it?? 

ALSO, when I plug in an ethernet cable (that works PERFECTLY on my friend's Macbook Pro) it connects but won't load the browser... why is this? Do I have to configure something?? 


Thanks so much. Also, sorry I'm such a newbie. I just hate windows............... and ubuntu is so much better. :)

---

### Post by Panganat on 2007-09-05
downloaded ntfs?? do you mean you formatted to NTFS? - Is your one touch pw protected. familiar with Acomdata where pw has to be entered or disabled to see fat32 partition. usb connection by the way. How are you connected?

---

### Post by wolfen69 on 2007-09-05
```
sudo apt-get install ntfs-config
```
applications>system tools>ntfs config

---

### Post by Shivasdance121 on 2007-09-05
I did this: sudo apt-get install ntfs-config in the terminal. I then clicked "enable write support for external drive." However, I am still unable to write to my external hard drive. Also, when i "eject" my external is says that it is writing to the disk and then there is an error message that says that I cannot eject it. 
No, my one touch is not pw protected. It is a USB connection. 
I'm connected to the internet through wireless. 

Thanks!! 





> **Panganat said:**
> downloaded ntfs?? do you mean you formatted to NTFS? - Is your one touch pw protected. familiar with Acomdata where pw has to be entered or disabled to see fat32 partition. usb connection by the way. How are you connected?

---


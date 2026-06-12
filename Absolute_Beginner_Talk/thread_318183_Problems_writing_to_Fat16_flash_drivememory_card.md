---
title: "Problems writing to Fat16 flash drive/memory card"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by lodp on 2006-12-13
Hello,

I've got problems writing to a new 512MB SD Memory card with my card reader. The card is formated Fat16. It mounts fine, but anything I copy to it is gone the next time I plug it in (even if I click 'safely remove' before unplugging).Writing to the card works fine in Windows. 

I also tried a 1GB USB pen drive (also new, right out of the box), which is formated Fat16 as well. Same thing -- when you drag something over, it shows up, you can even open it in some instances, but next time you plug it in -- nothing there.

I formated the pen drive to Fat32 in qtparted, and now it seems to be working. But for the memory card (SD Card), the fat32 option isn't available in qtparted -- there's only fat16, ext2, ext3, swap.

Is there a known issue with Fat16 and flash drives? the effect seems to be pretty robust on my system, but i couldn't find anything in the forums..

---

### Post by meng on 2006-12-13
Make sure you unmount ("eject") before you unplug. Also it doesn't hurt to wait 5-10 seconds before you unplug.

---

### Post by lodp on 2006-12-14
thanks for your comment -- but as i said, i did unmount the volume first (clicking 'safely remove' in kubuntu), and waiting a couple of seconds after that (until the LED on the card reader/pen drive stopped flashing) didn't change anything either...

---

### Post by meng on 2006-12-14
Ah sorry, I didn't read your original post carefully enough.

---

### Post by crazedgremlin on 2007-06-16
exact same problem here!  except not really.  Kubuntu comes up with a list of processes that it says I should quit or change the working directory of before I am able to eject the sd card (512 mb).  What's strange is that all of these processes are owned by root.  the first one is init.
I don't know what's going on here.

---


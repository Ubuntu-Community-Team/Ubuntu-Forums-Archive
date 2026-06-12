---
title: "help configuring hp officejet 6310xi using samba"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Jesus4life0412 on 2007-06-03
hi

i installed that printer on the main computer fine. but i cant figure out how to install it on my wireless network?
i have also tried the driver for hp officejet printers in synaptec package manger and enabled lan detection.i have a windows wireless network samba detects both computers fine but on the wireless laptop it will not find the printer help me figure this out please.

---

### Post by pappapump on 2007-06-03
Make sure that the printer is shared on the windows machine, then it will appear as a share on Ubuntu.
Then when you install a printer it should show up on the list.
Choose the default driver if it matches your printer, then Ubuntu will install the driver.
If it's listed.

---

### Post by Jesus4life0412 on 2007-06-03
it is and it works fine in windows wirelessly and ubuntu just on the main computer

---

### Post by pappapump on 2007-06-03
Was your Wireless device autodetected with your laptop?
Or did you have to use ndiswrapper?

---

### Post by Jesus4life0412 on 2007-06-03
auto

---

### Post by pappapump on 2007-06-03
Did you get a listing for your printer using the printer setup program?
If so, did it install for you?
I also see that you enabled lan detection, if you chose that instead of wireless that will stop you dead cold.
Deselect hardwired connections and leave it open for wifi.

---

### Post by Jesus4life0412 on 2007-06-03
ok i unchecked detect lan. now i just have share printer select and if i select local or detected printer it doesent find it. i also tried network printer but i dont know the address on my ubuntu. if i find it will that help? if so what would the address look like?

---


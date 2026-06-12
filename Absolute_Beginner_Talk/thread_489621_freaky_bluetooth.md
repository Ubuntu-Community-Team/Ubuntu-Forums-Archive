---
title: "freaky bluetooth"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-07-01
hello all 

i have nokia 6630 cell fone ..., 

i want to make connection betweeb it and my laptop i download all required packages and every thing is ok i use OBEX to send file from laptop to the cell fone but i cannot send files from mobile to the laptop it just starts to connect and then sending failed 

here is the output of connect operation 

root@adam-laptop:/etc# hidd --connect 00:13:FD:BA:0E:64
Can't get device information: Success

any body can give me advice abot that ? ?

---

### Post by black_ice on 2007-07-01
no replay :( please i neeeeeeeeed it urgently

---

### Post by comradekingu on 2008-07-07
I followed [this]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu") guide.

PC-> mobile works, but the other way around doesnt on nokias.

However if you leftclick the bluetooth-icon you can select browse devices. (You will even get access to the C: (aswell as E: )) From there you can transfer files from the mobile (and the other way around)

Its just a quick fix, but it works. Bluetooth isnt bug-free, but i expect this will be better in the future.

Also, it helps to authenticate from both the machine and the mobile end.

PC: Bluetooth-->Preferences--> entrust

---


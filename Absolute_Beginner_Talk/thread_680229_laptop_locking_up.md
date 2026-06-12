---
title: "laptop locking up"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by octane03 on 2008-01-27
computer is a Gateway 450 ROG and after about an hour of using it in linux doing anything from browsing internet to playing games it locks up and i haft to reboot then it lasts abour 30minutes until it locks up again 
one thing i did notice is with windows the fan would run alot now that i have UBUNTU it runs about every couple minutes for literally 2 seconds on then off

if it helps at all i am running Ubuntu 7.10

any advice please
Thanks

---

### Post by red_Marvin on 2008-01-28
Could you open a terminal window type *dmesg > dmesg.log* but do not press enter. Then use it and wait for it to freeze up.
When it happens try to get to the terminal again and then press enter to run the program.
Then reboot your computer and post the contents of the dmesg.log that should have been created in your home folder.
It might also help if you post the output of the terminal command *lshw*.

---

### Post by octane03 on 2008-01-29
> **red_Marvin said:**
> Could you open a terminal window type *dmesg > dmesg.log* but do not press enter. Then use it and wait for it to freeze up.
When it happens try to get to the terminal again and then press enter to run the program.
Then reboot your computer and post the contents of the dmesg.log that should have been created in your home folder.
It might also help if you post the output of the terminal command *lshw*.

i dont use the laptop all the time and when i do its not for too long but when i do i will do that and post up
thanks

---

### Post by octane03 on 2008-02-13
> **red_Marvin said:**
> Could you open a terminal window type *dmesg > dmesg.log* but do not press enter. Then use it and wait for it to freeze up.
When it happens try to get to the terminal again and then press enter to run the program.
Then reboot your computer and post the contents of the dmesg.log that should have been created in your home folder.
It might also help if you post the output of the terminal command *lshw*.


ok i was finally on the laptop long enough for it to lock up again but i could not get back to terminal due to it being minimized and the bottom bar was gone all i could due is see my desktop

i let it sit for about 7 minutes and it did nothing 

rebooted and the first time power and the fan turned on but it nothing showed up on the screen soo i powerd off then on again and it booted fine and working.

could it be overheating?
while using it the fan barley ever comes on

---

### Post by houstonbofh on 2008-02-13
Some laptops have software controlled fans.  Start in the BIOS and see if you can control the fan at all.  If not, you will need to search on your laptop to see what tool is needed for you fan, and if it is in the repos.  I have an old Dell that is this way.  I was able to set the fan to always on, and it works well, if not for long on battery.

---


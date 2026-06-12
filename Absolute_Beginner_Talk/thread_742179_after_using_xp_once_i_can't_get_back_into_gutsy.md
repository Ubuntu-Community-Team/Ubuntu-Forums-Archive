---
title: "after using xp once i can't get back into gutsy"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Daverobb on 2008-04-01
I've been using ubuntu almost exclusively for over a year now.  I ws just in xp to use one program - came out and restarted grub into gutsy - then got an error message saying that it couldn't find my /home drive.   It then pputs me into a different gutsy login screen with access to the terminal but i can't get in - it keeps giving me that home drive error message.

Am running the two systems on an older hp pavillion with 2 HD - #1 is 40g for windows and #2 is a bigger (160?) that has gutsy on it.  Still have access to windows but when i look in the my computer list, the #2 drive doesn't show although it is there in the device manager.  

need help!

---

### Post by abhiroopb on 2008-04-01
In windows you probably wouldn't be able to see the gutsy partition as it is a different filesystem. What I suggest FIRST is use a liveCD to backup your data, just in case.

Basically insert the LiveCD let it load up as normal, then when you have a usable desktop, go to the filesystem and look for your gutsy partition and backup your data. Here you should also be able to see if everything is ok with your /home folder (e.g. if its still there!).

See how this works first and let us know!

---

### Post by Daverobb on 2008-04-01
I've done as you suggested but i can't boot off of the live cd because it immediately goes into the grub loader to the dual boot option.  am i missing something or is there a interrupt key i can use??

---

### Post by philinux on 2008-04-01
Go into the bios and make boot from cd the first item in the boot order.

---

### Post by Daverobb on 2008-04-01
Did that and got into the Live CD - i perfromed the check on the cd and ran it.  Once in I can see the original drive volume there but i keep getting kicked out of ubuntu and back to a login screen - at first i have a few minutes but then it keeps cycling me out again and again.

---

### Post by mikeymo1741 on 2008-04-01
Did you Hibernate out of Windows or shut down?

---

### Post by Daverobb on 2008-04-01
shut down

---

### Post by Daverobb on 2008-04-02
update - did eventually get the live cd working but it remained really buggy - finally formatted entire ubuntu drive and tried a brand new reinstall of gutsy but it freezes somewhere at or near the partitioning - has done this probably 10 X now and will not install.  If anyone has any further clues, feel free.

btw, my machine runs on an Athlon 1.3 chip with 1meg of RAM.

---

### Post by Daverobb on 2008-04-02
oops, 1 gig,obviously:oops:

---

### Post by Daverobb on 2008-04-03
worked fine through safe graphics mode but frustrating still

---


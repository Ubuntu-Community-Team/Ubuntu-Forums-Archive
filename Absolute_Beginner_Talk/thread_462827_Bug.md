---
title: "Bug"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-03
i recently loaded ubuntu 7.04 .now i am dual booting it with windows XP .after pressing the option to use ubuntu OS i get a screen(for 1-2 secs) where it's written .
> .......MP-BIOS BUG-8254 timer not connected.... 
then everything runs fine.
what does that mean?

---

### Post by hellmet on 2007-06-03
Try this thread::
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)
This is similar to::
[http://help.lockergnome.com/linux/17-13-nforce-57-MP-BIOS-bug-8254-timer-connected-IO-APIC-ftopict369780.html](http://help.lockergnome.com/linux/17-13-nforce-57-MP-BIOS-bug-8254-timer-connected-IO-APIC-ftopict369780.html)

---

### Post by pardesi on 2007-06-03
thanks.But i **couldn't get anything** out of it:( .i am a newbie.also my compuetr specifications are
intel   pentium d 2.88Ghz,160GB SATA, 1MB RAM. PLEASE help.

---

### Post by hellmet on 2007-06-03
Just try the 3rd and the 8th posts. Try your best. The instructions are quite clear there. If you've trouble understanding the basics of ubuntu, you should probable search / post in the Absolute Beginner Talk and try to learn the distro's basics well. Its a steep learning curve, I can understand, but you'll have fun during the process. I bet. :D

---

### Post by pardesi on 2007-06-03
how does one go to the grub boot screen??

---

### Post by gunbladeiv on 2007-06-03
first start ur pc/laptop.
After the POST your screen will appear like ..

Loading Grub 1.5

then you click up or down arrow on your keyboard to stop the default timer.
then read the instruction there.  From here i think you can follow the intruction on the other threads.  Read the instruction.  That's all you need to do.

---

### Post by pardesi on 2007-06-03
i have HP INVENT  so i dont get any command like loading GRUB

---

### Post by gunbladeiv on 2007-06-03
then as soon as your laptop power up just keep clicking the up or down button until your screen stop at the boot loader.

---

### Post by pardesi on 2007-06-05
i went to the terminal then typed the code 
```
 sudo gedit /boot/grub/menu.lst
```
then it asked me for my password and i gave it .then i was directed to another screen my my grub boot menu appeared .then beside the option "#defoptions=" where it was written splash start i wrote "noapic"
then i went to the page of original terminal and i wrote 
```
update grub 
```.
then rebooted the computer and stil i get the same thing written before i get the ubuntu page which asks me for my password...HAve i gone wrong somewhere??:(

---

### Post by pardesi on 2007-06-05
> **pardesi said:**
> i went to the terminal then typed the code 
```
 sudo gedit /boot/grub/menu.lst
```
then it asked me for my password and i gave it .then i was directed to another screen my my grub boot menu appeared .then beside the option "#defoptions=" where it was written splash start i wrote "noapic"
then i went to the page of original terminal and i wrote 
```
update grub 
```.
then rebooted the computer and stil i get the same thing written before i get the ubuntu page which asks me for my password...HAve i gone wrong somewhere??:(
i forgot to write i also saved the file which poened in gedit after i wrote "noapic" and finally when i write update grub it shows
```
bash: update: command not found

```

---

### Post by pardesi on 2007-06-05
someone please.:(:(

---

### Post by rajeev1204 on 2007-06-05
> **pardesi said:**
> i recently loaded ubuntu 7.04 .now i am dual booting it with windows XP .after pressing the option to use ubuntu OS i get a screen(for 1-2 secs) where it's written .

then everything runs fine.
what does that mean?


Enter the bios and under bios functions set ioapic to enabled .   

But i dont know what that does but enabling apic  gets rid of that message .

---

### Post by pardesi on 2007-06-05
but how do i update a change i have made in the grub menu ( i basically wrote noapic in the "#defoptions=" options besides splash screen.)

---

### Post by gunbladeiv on 2007-06-05
just reverse what you've done.
edit what you've change by deleting the noapic word.save and update grub

---

### Post by pardesi on 2007-06-05
that was how it was before and still it showed the problem.well how to update grub???

---

### Post by gunbladeiv on 2007-06-05
i've never update grub before but i suppose the command is update-grub (as root)

---


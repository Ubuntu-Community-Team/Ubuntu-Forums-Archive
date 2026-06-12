---
title: "Returning to Windows"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by rev-ortell on 2007-03-01
I've been burned in the past with a version of Linux base monitoring system, PC Cop. I installed it on a computer to monitor internet traffic at church. I got rid of all of those older pcs, and in the process I reformatted all of the hdds to Windows 98SE EXCEPT that Linux system. All it would do is go to the prompt: GRUB. I gave up, piece mealed it and was done. 

I am currently downloading Ubunt 6.10. IF I install this baby and decide that it is not for me (doubtful that this will be the outcome) HOW do I return to bogged down Windows XP?

Thanks, 
Leary and Weary

---

### Post by Kateikyoushi on 2007-03-01
Delete the partitions first then to remove grub.
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

---

### Post by rev-ortell on 2007-03-01
Thanks. One follow-up question... how do you delete the partitions? Isn't that an option as you run the Windows CD?

Sorry for the lack of knowledge here.

---

### Post by Kateikyoushi on 2007-03-01
There are system administration tools in XP like disk management to remove the partitions or can use the ubuntu live disc's gparted as well.

---

### Post by ComplexNumber on 2007-03-01
> **rev-ortell said:**
> I've been burned in the past with a version of Linux base monitoring system, PC Cop. I installed it on a computer to monitor internet traffic at church. I got rid of all of those older pcs, and in the process I reformatted all of the hdds to Windows 98SE EXCEPT that Linux system. All it would do is go to the prompt: GRUB. I gave up, piece mealed it and was done. 

I am currently downloading Ubunt 6.10. IF I install this baby and decide that it is not for me (doubtful that this will be the outcome) HOW do I return to bogged down Windows XP?

Thanks, 
Leary and Weary
ubuntu comes as a liveCD. you can try before you install.



> **rev-ortell said:**
> Thanks. One follow-up question... how do you delete the partitions? Isn't that an option as you run the Windows CD?

Sorry for the lack of knowledge here.
it will guide you how during the install. in the meantime, just pop in the ubuntu disk and see if you like it and if all your hardware is detected.

---

### Post by rev-ortell on 2007-03-02
BIG THANKS... They mentioned the LiveCD trial thing, but I did not see it. I'm done downloading the program and will burn a CD here and try the trial side of things.

Blessings

---


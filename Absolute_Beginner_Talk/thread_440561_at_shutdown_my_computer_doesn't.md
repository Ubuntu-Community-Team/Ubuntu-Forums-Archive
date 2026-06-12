---
title: "at shutdown my computer doesn't"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by finalfrontier on 2007-05-11
at  shutdown  my  computer  doesn't  shutdown  it go's as far as the progress bar
when the progress bar stops showing activity i still see ' UBUNTU '  on my screen
and my computer doesn't shutdown  i have to press the power button
i'am  using a pc with an older AMD processer

---

### Post by jrusso2 on 2007-05-11
open a terminal window and type
sudo gedit /etc/modules
it will ask for your password enter it.

at the bottom of the file

add a new line with the following statement:

apm power_off=1

then save and reboot, and voilá! the computer will shut down correctly I hope.

---

### Post by finalfrontier on 2007-05-12
THANK YOU  jrusso2  your tip worked my computer shuts down now  !

---

### Post by Nikusan on 2007-05-19
I've got a similar problem, adding that module doesn't work. Any ideas?

---

### Post by confused57 on 2007-05-19
> **Nikusan said:**
> I've got a similar problem, adding that module doesn't work. Any ideas?

Maybe this will work:
[http://ubuntuforums.org/showthread.php?t=428363](http://ubuntuforums.org/showthread.php?t=428363)

---

### Post by Nikusan on 2007-05-19
Thanks for the tip, but no luck with that idea either. Below are the three things I've tried, they're all mentioned a number of times in many threads similar to this one.
[LIST]
[*]tried adding "apm power_off=1" to /etc/modules
[*]tried adding -hP to the shutdown command in /etc/acpi/powerbtn.sh (at the bottom)
[*]tried adding acpi=force to the kernel line in /boot/grub/menu.lst
[/LIST]


I've also tried various combinations of the above, with no success.

---


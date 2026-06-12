---
title: "Problem with E35M1-M"
date: 2011-10-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by vaton4 on 2011-10-10
Fresh installation of Ubuntu 11.10 (Ubuntu 11.04, Fedora 15, Fedora 14, ....) on Asus E35M1-M freezes during boot, but only if rebooted after one or more suspend-resume cycles.

After initial boot, everything works as suspected. Suspend & resume works perfectly (tested both PS2 and USB keyboard wakeup). Problems begin if I shutdown or reboot system (no matter which way - both Reboot and Shutdown from GUI, command 'reboot' from CLI, CTRL+ALT+DEL, short push of POWER button).

After reboot there is BIOS screen, but no GRUB menu. I can see just black screen with blinking underline cursor in the left top corner. For about 12 seconds cursor stays on first line, then jumps to the second line and here stays for about 4 minutes. Then the following BIOS error message shows up:

   Reboot and select proper Boot device or Insert Boot Media
   in selected Boot Device and press a key.

System does not boot even after switched off and on using the POWER button (i.e. +5VSB stays on). If I press CTRL+ALT+DEL in this state, hardware restarts so I see BIOS initial screen, but then I get black screen with cursor again. 

System gets bootable again only if (and always if) is manually reset by the RESET button or power is completely cycled off and on (by unplugging power cord, for example).

Sequence is as follows:

1. Initial state: PC power cord is disconnected from outlet.

2. Connect power cord to outlet and Press the POWER button.
   BIOS starts, then system boots.

3. Login as arbitrary user, click icon in the right top corner, select Shut Down...
   and click 'Restart'. System correctly restarts.

4. Login again, click icon in the right top corner, but now select Suspend.
   System goes to sleep mode.

5. Press any key on keyboard. System wakes up, everything works as expected.

6. Now click icon in the right top corner, select Shut Down... and click 'Restart'
   again. System goes down, displays BIOS screen but then frozes.
   After about 4 minutes, the following BIOS error message shows up:

      Reboot and select proper Boot device or Insert Boot Media
      in selected Boot Device and press a key.
 
7. Press RESET button. System boots as expected until next suspend-resume cycle.

AFAIK the error message comes from BIOS and says the BIOS can not find boot disk!!!
I do not know boot  sequence in details, but expecting the BIOS knows  from where to boot  every time, not just after PC powered on or reset by  button. So why BIOS can not find boot disk after system got trough suspend-resume sequence? Would somebody explain what is going here
:confused:

EDIT:
Today I have replaced Ubuntu  by Fedora 14 and then Fedora 15. The same behaviour.

EDIT 2:
Made giant step forward. "Discovered" pm-utils, so now I can check  things in CLI.
As expected, pm-suspend command "somehow" suspends system,  but following resume operation fails.

EDIT 3:
Tested on fresh install of Ubuntu 11.10. Nothing changed.
Seems it is the kernel or Asus EFI Bios problem.
Still nobody cares ????

---


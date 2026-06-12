---
title: "URGENT: Windows 7 / Ubuntu Restore Issue."
date: 2011-12-03
forum: Any Other OS
---

### Post by JF382 on 2011-12-03
I have a Sony Vaio laptop that has the factory restore Win 7 OS on the hard drive. I installed Ubuntu, but I wanted to just go back to Windows 7, so in the restore process, I just selected Factory Format, so everything with the computer would be back to normal. But now when it boots it says grub loader <boot error> or something along those lines, i dont think i have the exact of what its saying, but that should help somewhat. what can i do to get windows 7 back, because your supposed to hit the f12 key but its not even working now after the whole factory format thing. please help. ANY SUGGESTIONS, would be apprecited.

---

### Post by Basher101 on 2011-12-03
Your Windows bootloader got overwritten by grub. You will need a windows installation disc or repair disc in order to fix the now broken MBR to the default one. 

if you do not have a windows repair disc there is a (possible) workaround to get to your windows (if it was not reset yet) to make a repair disc:

1. reinstall Ubuntu

2. boot into windows via grub menu

3. use the recovery tools to burn the dics

4. delete the ubuntu partition, reboot and pop in the windows repair disc you just made

5. follow the steps on the repair menu and it should fix you MBR


if this wont work you must get a windows CD from someone else that has the same windows version like you (basic, home, home premium or ultimate)

---

### Post by 3Miro on 2011-12-03
You need to restore the Windows MBR:

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

If you don't have a windows CD, you can check this link:

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

They recommend this CD, although I have not used it and I don't know how well it will work.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

### Post by cariboo on 2011-12-03
Moved to Other Distro/OS Talk, as this is a Windows question.

---


---
title: "need help getting windows  xp bootable again"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by rogersmith84 on 2005-07-27
I installed the Lilo boot system when i installed ubuntu and it got rid of my windows xp boot....how can I get Windows xp to be bootable again?

---

### Post by jeremy on 2005-07-28
Boot from the Windows XP CD and press the "R" key during the setup in
order to start the Recovery Console. Select your Windows XP installation
from the list and enter the administrator password (if you have one). At
the input prompt, enter the command "FIXMBR" and confirm the query with
"y". The MBR will be rewritten and GRUB will be uninstalled. Press
"exit" to reboot the computer.

---

### Post by rogersmith84 on 2005-07-29
I have done all that but when it boots, LILO gives me a red boot screen but only gives me the option to boot into linux.  I was hoping that there was some way to edit LILO to acknowledge XP.  It is really weird too because I have reinstalled windows and deleted the Linux partitions, but it is still trying to load linux.  It gets about half way through and then it says something about panic and doesnt load linux all the way.  and when i put in the windows cd and don't press enter to boot into the cd, it will load into XP.  When i dont have the cd in it try to boot linux.....it is really strange.  My firend seems to think the reason my dual boot didnt work is because i had windows installed on a different hard drive than linux.  but when i reinstalled it, i put it on the hard drive that i had linux on.  I have no clue what is wrong....I dealt with linux a little in High School but that was red hat and i was dealing with a single boot server with diskless workstations. anywho.  Hope someone can help.

---

### Post by nic2 on 2005-07-29
I have had a similar problem before and fixed it by zero-filling the MBR.  I downloaded a utility from the vendor's website (Seagate in my instance) which allows you to create bootable stiffies; once booted you follow the procedures to zero-fill the MBR or complete HDD.

Ps. I am also a newbie so this might not be the only option available to you (but please post a response to let me know if this worked).  Good luck!

---

### Post by rogersmith84 on 2005-07-29
[QUOTE=nic2]I have had a similar problem before and fixed it by zero-filling the MBR.  I downloaded a utility from the vendor's website (Seagate in my instance) which allows you to create bootable stiffies; once booted you follow the procedures to zero-fill the MBR or complete HDD.

Ps. I am also a newbie so this might not be the only option available to you (but please post a response to let me know if this worked).  Good luck![/QUOTE]


you wouldnt happen to have the link to this utility would you.  I also have 2 seagate hard drives which i am working on.  I also don't quite understand what you mean by zero-filling MBR(Master Boot Record)

---

### Post by Kapre on 2005-07-29
[QUOTE=rogersmith84]you wouldnt happen to have the link to this utility would you.  I also have 2 seagate hard drives which i am working on.  I also don't quite understand what you mean by zero-filling MBR(Master Boot Record)[/QUOTE]


This also happened to me (actually many times when I was experimenting with Knoppix and Fedora).If you have a boot disk of WinMe or Win98, try booting from it and when your on the prompt type fdisk /mbr. Worked for me.

 O:)

---

### Post by nic2 on 2005-07-30
[QUOTE=rogersmith84]you wouldnt happen to have the link to this utility would you.  I also have 2 seagate hard drives which i am working on.  I also don't quite understand what you mean by zero-filling MBR(Master Boot Record)[/QUOTE]
Link to download utility:
 [http://www.seagate.com/support/disc/drivers/discwiz.html](http://www.seagate.com/support/disc/drivers/discwiz.html)

Link to webpage explaining the term 'Zero Fill':
[http://www.seagate.com/support/kb/disc/faq/ata_llfmt_what.html](http://www.seagate.com/support/kb/disc/faq/ata_llfmt_what.html)

---

### Post by rogersmith84 on 2005-08-01
[QUOTE=Kapre]This also happened to me (actually many times when I was experimenting with Knoppix and Fedora).If you have a boot disk of WinMe or Win98, try booting from it and when your on the prompt type fdisk /mbr. Worked for me.

 O:)[/QUOTE]


Great this worked and ubuntu is gone!!!!  I will try soon to do the duel boot thing again....just hope it works right this time lol..  Thanx for the help!!

---


---
title: "Grub Boot Help"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by rey1321 on 2006-12-24
[SIZE=2][B]Need help, can't boot into my system due to ERROR 18, I installed Dapper, I using the live CD to log on in this forum. I did a little search about error 18 and this what i found:

ERROR 18: Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

I have 80GB on my system!

OK,  now that I found the problem mi question is how to solve it.Here are my 2 possible solution.
1) Try to Update the BIOS.
2) Try to move the boot partition to the front, or at least to the appropriate range.

Since I can't update my MOBO Bios, cause I using the live CD, my only solution is #2, I know I can reinstall the system again ,but I have important files That I don't want to erase when formatting.

My question is how can I solve this problem, using the live CD.

Please help me![/B][/SIZE]      
         [IMG]http://ubuntuforums.org/images/uf/misc/progress.gif[/IMG]                                                                                                                            [[IMG]http://ubuntuforums.org/images/uf/buttons/edit.gif[/IMG]]("http://www.ubuntuforums.org/editpost.php?do=editpost&p=1927459")

---

### Post by dbbolton on 2006-12-25
does the grub menu come up at all, or does it just go straight to that error message ?

if the menu comes up, can you boot windows, or whatever else you have installed ?

---


---
title: "restore windows boot?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by ELD on 2007-02-27
Hi all i just used partition magic 8 to delete the swap and linux partion on my drive, just wondering how i restore the windows boot, as i think grub would have been deleted as well so im scared to turn my pc off incase i cant boot windows?

---

### Post by george29 on 2007-02-27
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

grabbed that from a quick google search of the terms "fix winXP mbr"

---


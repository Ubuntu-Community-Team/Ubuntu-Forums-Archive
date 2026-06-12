---
title: "Problems with dual booting!"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by jackhack on 2007-05-16
Well.. it goes without saying that i had no idea what i was doing when i installed ubuntu but i had a windows installation already and it is on the primary HDD. I went and installed Ubuntu on the secondary HDD and now grub just decides automatically to boot into Ubuntu and doesnt even give me the option to go to windows. i looked in menu.lst and the "hidden" command was disabled via #.  Any suggestions?

---

### Post by vtel57 on 2007-05-16
When you allowed GRUB to be installed, it installed itself on the main drive's Master Boot Record. Don't mess with the "Hidden" entry. That's something entirely different. There should be an entry in the GRUB boot screen for Windows. You have about 8 seconds to scroll down that screen with your arrow keys. Windows is usually at the bottom of the menu.

---


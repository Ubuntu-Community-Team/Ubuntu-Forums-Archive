---
title: "Editing menu.1st in xubuntu"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by stefcep on 2008-03-05
I need to edit the menu.1st text file beacsue I can only boot with the noapic kernal option.  I can open the menu.1st file and edit it but I can't save the changes, because I don't have permission.  How can i edit and save.  (I knew how to do it about a year ago, but now i've forgotten)

---

### Post by aidanr on 2008-03-05
Open a terminal and type in the following:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo mousepad /boot/grub/menu.lst
```
Find the line that says:
# defoptions=quiet splash
And add noapic to the end of the line, save and exit and then do:
```
sudo update-grub
```

---


---
title: "How to boot into Windows installed on a seperate SATA drive"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by planC on 2007-10-01
Is there some other code, cos I tried the following from Feisty guide and it didn't work. sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

    * Append the following lines at the end of file. 

title           Windows XP on SATA drive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

    * Save the edited file 

    * Finally, do 

sudo update-grub
How do I save ? can't find out anywhere. 
Can anyone help?:)

---

### Post by kyphi on 2007-10-01
When you have the menu.lst open, at the top left it says File.  Click on that and then click save on the drop down menu.

---

### Post by logos34 on 2007-10-01
try:

> title Windows XP on SATA drive
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

[B]
sudo fdisk -l[/B] (lowercase L)

should show a ([COLOR="Red"]*[/COLOR]) symbol in 'Boot' column of windows partition.

---


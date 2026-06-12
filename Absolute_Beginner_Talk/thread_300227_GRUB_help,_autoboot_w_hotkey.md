---
title: "GRUB help, autoboot w/ hotkey"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by aswells on 2006-11-15
I am trying to set up grub so that It automatically loads the default without showing the OS list, but still be able to see when I need to, similar to how BOIS works. 

I tried setting timeout  0   it loaded the default, but I was not able to get to the list when I needed to. Any help would be appreciated.

---

### Post by steve.horsley on 2006-11-15
Use the command **gksudo gedit /boot/grub/menu.lst** and find this section of the file:
> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Remove the leading # from that third line. You can put the timeout back to your preferred value.

---

### Post by aswells on 2006-11-15
I thought hidemenu did something else, thanks for clearing that up!

---


---
title: "Scripts"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-10-29
Hi Everyone.

I just installed Gusty on two machines. One office system and the other is my notebook at home. After installation, i found one difference between the two. 

The notebook at home with fresh 7.10 installation has an option on right click called "Scripts" which when selected give me 4 options 

=> gedit-root
=> root-nautilus-here
=> search-here
=> scripts folder

I have used these options when i had fiesty installed on my system and honestly found then extremely convenient and useful. I still find the same scripts option on my fresh Ubuntu install at home. 

However, at work on my computer, i do not find these options when i right click inside the file manager / explorer. 

The only difference between the installations at home and work is that at home, i used Fiesty in the past and had a separate /home partition. While the installation at work is a completely new installation. 

Could anybody tell me why this is happening and how i could enable these options at work? 

Thanks a lot in advance.

Cheers,
Harry

---

### Post by Cochise on 2007-10-29
open your home folder on your home pc and press ctrl + h to show hidden files and then open the folder .gnome2 and copy the nautilus scripts folder to the same folder on your work pc, that should do it

---

### Post by erginemr on 2007-10-29
You may also consider installing Nautilus add-ons / extensions for these jobs instead of using scripts. They show up directly on the context menu (right click) on files, folders and empty space.

For Nautilus in Root: sudo aptitude install nautilus-gksu
For Console in Any Folder: sudo aptitude install nautilus-open-terminal
For the Search Addon: [http://www.getdeb.net/release.php?id=482](http://www.getdeb.net/release.php?id=482)

There are several others in the repositories.

---


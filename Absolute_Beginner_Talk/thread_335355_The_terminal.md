---
title: "The terminal"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by shadowphoenix on 2007-01-10
I would like to know how do i enlarge the size of the terminal because i am running under the failsafe terminal mode therefore i need to enlarge the size of the terminal in order to run photorec whereby i have accidentally deleted my home folder.I have deleted the home folder through this command 

rm-rf /home/user/mount

Please someone please let me know how can i recover my home folder or have my home folder and run under the GUI mode.Because i can't run in the GUI mode once the home folder is deleted.

---

### Post by mohjlir on 2007-01-10
You need to restart your machine and select the 'repair' kernel on the grub menu as your computer is booting. From this, you will get a root login. Do the following:

adduser yourname
adduser yourname admin

Then, you should be able to log in with the gui again and use sudo. You have to be a bit careful with the shell, it's powerful. Oh, and if you had anything important in your home folder that you don't have a backup of... my sentiments to you.

---


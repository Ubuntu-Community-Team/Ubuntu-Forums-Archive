---
title: "Cannot load grub after instilling windows"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2007-10-07
I wiped one of my hard drive stupidly using windows.   so now the windows start up screen only shows up.
I used this coding to set things up:

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit






Now after setup (hd0) I get this print out
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition


Any help? please? I feel naked without linux:(

---

### Post by taurus on 2007-10-07
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by anubis2814 on 2007-10-07
I used xp not vista so this really isn't helping

---


---
title: "[SOLVED] Can't delete a swap file which is causing problems"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by RobHK on 2007-11-22
(Blue italics indicates quoted text)

I went to edit GRUB using sudo vi /boot/grub/menu.lst.

The terminal returned:
[I][COLOR="Blue"]"E325: ATTENTION
Found a swap file by the name "/boot/grub/.menu.lst.swp"
          owned by: root   dated: Thu Nov 22 19:05:59 2007
         file name: /boot/grub/menu.lst
          modified: YES
         user name: root   host name: office
        process ID: 6287
While opening file "/boot/grub/menu.lst"
             dated: Thu Nov 22 10:41:44 2007

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /boot/grub/menu.lst"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/boot/grub/.menu.lst.swp"
    to avoid this message.
"/boot/grub/menu.lst" 170 lines, 4792 characters
Press ENTER or type command to continue"[/COLOR][/I]

It was clearly case #2 so I tried to recover as suggested. 
This did not work so I went to delete the swap file but was told I did not "*[COLOR="Blue"]have permissions to change it or its parent folde[/COLOR]*r".

---

### Post by bodhi.zazen on 2007-11-22
delete the file as root with either 

suod rm -f /path/to/file

or

gksu nautilus -> navigate to and delete

---

### Post by RobHK on 2007-11-22
Thank you! Done.

---

### Post by RobHK on 2007-11-22
Another (related) problem which is new: I can't mount any of my NTFS partitions.

I can get permission but then I get an error message which I can't post directly as it is a graphic so I uploaded it to:

[http://www.filecrunch.com/file/~wlrna7](http://www.filecrunch.com/file/~wlrna7)

(You have to scroll down a little to see the download button, then wait 20 seconds.)

It doesn't only apply to the USB partitions, so I can't use the "Safely remove hardware" option, and I'm just confused by the command line instructions.

---

### Post by Dr Small on 2007-11-22
Check your Account Permissions, under Users and Groups and make sure you have all permissions in there.

---

### Post by RobHK on 2007-11-23
Thanks.

After leaving all night, running Windows this morning and rebooting into Ubuntu, the problem seems to have gone away. :)

---


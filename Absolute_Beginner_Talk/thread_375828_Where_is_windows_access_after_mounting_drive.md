---
title: "Where is windows access after mounting drive"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-03-04
After following these instructions to mount windows drive:

 How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

    * Save the edited file 

Now where do I go to access the windows files? I went to media/windows and it's empty! Where else could it be?

I thought it would be in  Places > Network Servers.

---

### Post by PartisanEntity on 2007-03-04
Have you looked in Places > Computer ?

You could also look in Places > Computer > Filesystem > media

---

### Post by Kateikyoushi on 2007-03-04
No it won't be in network servers for sure. Could you post the output of the following command ?

```
fdisk -l
```

---

### Post by geovino on 2007-03-04
Yes, It's showing up now, but I had to reboot. Nobody tells you that! Now I know. Thanks.

Now the icon shows up on the desktop and Places > Computer. Can I remove it from the desktop so its only in Places > Computer?

---

### Post by PartisanEntity on 2007-03-04
Yes you can, you have to launch Configuration Editor then go to apps > nautilus and there you can unclick volumes_visible

The configuration editor should be under Applications > System Tools

---

### Post by geovino on 2007-03-04
Thanks, but I don't have Configuration editor in my System Tools. But I found i tby gonig to the terminal and typing
$ gconf-editor.

How can I add it to the Systems Menu?

---

### Post by PartisanEntity on 2007-03-04
Try this: 
1. right click on Applications and select Edit Menus
2. click on System Tools and find Configuration Editor on the right, make sure the box is ticked

Then Config Editor should show up in the menu

---

### Post by geovino on 2007-03-05
Got it...Thanks:)

---


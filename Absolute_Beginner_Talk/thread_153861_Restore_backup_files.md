---
title: "Restore backup files"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-04-01
I was wondering exactly how to restore backup files that I've created when following some of the instructions in threads that I've followed.
For example when I edited my menu.lst I was given the commands:
           cd /boot/grub
           sudo cp menu.lst menu.lst_backup
in order to edit my grub menu to boot windows with a second hd.
Fortunately, everything worked and I know it's good practice to backup files
when editing.  Would I just do:  cp /boot/grub
                                 then:   mv menu.lst_backup menu lst
to replace the edited menu.lst with the backup that was made?

Thanks

---

### Post by Qrk on 2006-04-01
```
cd /boot/grub
sudo cp menu.lst_backup menu.lst
```

Its the same process for creating the backup, but in reverse.

---


---
title: "CHANGING OS initiation? oh no!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by donamai on 2007-04-20
Hi,

I recently found the GRUB HOW-T0 section so that I could find information on how to change the default OS a the boot up.

I followed the steps on how to change the number in the #set line but I don't think I did it right. 

I also followed the steps on backing up the GRUB file before I did this so I am sure I can go back to the way it was before... right?


The problem now is that the computer does not go to the OS I want and the Ubuntu , default OS, does not start... it just says mounting hh8 or something like that and then it gives the command line. Not any clue as to  what to do here.

So I come to you guys to ask the following questions:


Where do I go to fix the initiation of the Ubuntu default system?

After fixing it how can I change the from the default OS to the want I want. Most of the instructions in the GRUB HOW-TOs lack on specifying where exactly you have to go to make changes.

Thank you for your help

---

### Post by Origin415 on 2007-04-20
Is it possible for you to post what your grub's menu.lst says?

I am not sure what you are talking about with a #set line, near the top of the file there should be a line that says:

```
default                0
```

or some other number, that is what you are changing

---

### Post by raja on 2007-04-20
To return to the grub menu that you have saved, you may have to boot with a live cd. To change the default choice in the grub menu, you have to change the value of 'default' in /boot/grub/menu.list. Count the position of the OS you want in the listings in the menu.list file. Remember that the numbering starts from 0. Also remember that when you get a new kernel, you will have to change the value of default again.

---

### Post by mikewhatever on 2007-04-20
What happens when you hit Esc button during the timer countdown? Do you see the menu? Choose the OS you want from it manually.
If that does not work, (it actually should) restore your menu.lst to the default state from the backup you made. Lets say you called it munu.lst_backup.
You can boot into recovery mode (or type this in the terminal) and type
> sudo cp /full_path_to_file/menu.lst_backup /boot/grub/menu.lst

---

### Post by donamai on 2007-04-20
Thank you for your answers. 
> 
Is it possible for you to post what your grub's menu.lst says?

I don't know if I can do it ORIGIN now the when the system starts the system only display on my screen loading hh8

So I am not aware of how to even get that info for you.

but maybe you could tell me how to reset the OS so the backup GRUB that I created is put in place again.

Do you guys know how to do this from the boot up choices?

Please let me know

---


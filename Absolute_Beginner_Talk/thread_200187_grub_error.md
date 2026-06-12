---
title: "grub error"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Heretic on 2006-06-19
I successfully installled Ubuntu 5.10 to an external laCie usb hard drive. GRUB detected Windows on my primary drive. It said it would be safe to install it in the master boot record of my primary drive. Well, I boot up, and GRUB encountered an error and will not do anything else.

Help. ](*,)

---

### Post by Winblowz on 2006-06-19
What GRUB error is it? (the number) Also post what it said.

---

### Post by Heretic on 2006-06-19
GRUB Error 21. I not even able to use my PC....

---

### Post by Heretic on 2006-06-19
Just need help on what i need to edit from menu.lst

I want it to be directed at m sda hard drive [external usb]

---

### Post by catlett on 2006-06-19
Your menu list doesn't appear to be the problem. If it was yoiur menu list you would still be able to get into the menu and the error would happen when you chose an entry and it went to the wrong partition.
If you don't even get to the grub menu you have a bigger problem than a menu list. Grub is not installed correctly.

If you can edit your menu list, How sre you doing it? Do you have a live cd running?
Yoiu can try to reinstall fron the live cd,

---

### Post by Heretic on 2006-06-19
Im currently running the Live CD right now.

---

### Post by confused57 on 2006-06-19
Here's a howto on installing Ubuntu on an external usb hd:

[http://www.ubuntuforums.org/showthread.php?t=80811&highlight=USB+hard+drive](http://www.ubuntuforums.org/showthread.php?t=80811&highlight=USB+hard+drive)

I would hope there is an easier way?

---

### Post by catlett on 2006-06-20
Great! You'll be the first to try this.

Open the terminal. Enter ```
sudo grub
``` This will give you a grub prompt. It will say grub> in the terminal. Enter find this at grub>
    ```
  find /boot/grub/stage1
``` Now whatever the answer is enter next. If it hd0 use thst if it is hd1 use that. I'm going to put question marks but you put the numbers that you got from the find command . 
AT grub> enter this ```
root (hd?)
``` And finally at the grub>```
setup (hd?)
``` and finally to get out of grub enter at grub> ```
quit
``` 

The grub manual saya this should work. I haven't tries it myself yet. It can't hurt anything. Either it will work or it won't.

Good luck. I hope it helps. Reinstalling sucks.

---

### Post by acht on 2006-06-20
what is error 13, then just tried a reinstall and got error 18.

---

### Post by anaconda on 2006-06-20
What if you repair windows mbr (make it like it was before you installed grub) You can do this by booting with windows CD and go to rescue/repair, and type fixmbr (or was it fixboot..)

And then go to your bios, and change the boot order so that it boots from USB first and windows second.. Then you could install grub to your USB-hdd. And when the USB-hdd is connected you could choose which OS you want to boot, and When it isn't connected windows would boot normally..

Just an idea..

---


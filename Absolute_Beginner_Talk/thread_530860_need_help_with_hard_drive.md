---
title: "need help with hard drive"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by linuxnewbie1113 on 2007-08-20
my 20 gb hard drive recently filled up. I tried restarting the computer because it wouldn't allow me to delete files. When I tried signing back in it told me there wasn't enough memory to perform task. How can i transfer, or delete files booting from live cd on another hard drive? Also is there anyone for me to log in to my account from the live cd???

---

### Post by leedsdevil on 2007-08-20
did you try the CD?(boot ). sounds like you dont have the room for paging ram i would try to slave another drive in or slave that drive and see what you get ive done that same thing in windows so i ran another drive with a fresh OS and clean up the other drive and then booted back. i hope that may help im still new to Ubuntu and how every thing works

---

### Post by linuxnewbie1113 on 2007-08-20
yea thats what i figured, but im having trouble installing ubuntu on my other hard drive. Its only 10 gb and its really old everytime i try booting from it i get an error 21. Guess ill have to keep trying. How do i change which drive is my primary?

---

### Post by leedsdevil on 2007-08-20
ok the flat wide cable is the one u need to disconnect at first install the other drive (chk the jumper setting) then go int o the bios and set it so CD is first in the boot then install ubuntu once installed and working shutdown set ur jumpers to how u want them primary 2ndary or cabe select means where and how the cable is placed in the back further one out is slave closer to the board is primary hope this helps

---

### Post by Aishiko on 2007-08-20
the jumpers on the Hard Drives if they are on the same IDE cable (assuming of course IDE) but if you mean the one used for booting well you do a new install on a second hard drive and then you if it's like windows boot into the new install instead of the old is all

---

### Post by leedsdevil on 2007-08-20
You got it bud thats what i meant to say but i wanted to make sure that i didnt mis a step hehe im go for that i know what im doing even if i dont i just look good doin it LOL:lolflag:

---

### Post by linuxnewbie1113 on 2007-08-20
thanks for all the help im tryin' this right now.

---

### Post by Aishiko on 2007-08-21
let us now the results and what you had to do to get it working.

---

### Post by linuxnewbie1113 on 2007-08-21
Well i finally got ubuntu installed on the other hard drive but when i try to but it up it won't load. It stops on the grub menu with an error 21 can anyone help me to fix that or tell me what it is

---

### Post by logos34 on 2007-08-21
> **linuxnewbie1113 said:**
> Well i finally got ubuntu installed on the other hard drive but when i try to but it up it won't load. It stops on the grub menu with an error 21 can anyone help me to fix that or tell me what it is

Boot from the live cd and post the output of 

sudo fdisk -l (lowercase L)

Go to Places>Home Folder and double-click on the root partition of the drive you just installed ubuntu on (the 10GB?).  

Open up the /boot/grub/menu.lst file on that disk.  Post it.  

Which disk is listed first in the Bios hard disk boot order?

---


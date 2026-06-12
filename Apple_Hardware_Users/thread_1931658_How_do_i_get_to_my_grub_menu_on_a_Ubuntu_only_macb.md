---
title: "How do i get to my grub menu on a Ubuntu only macbook?"
date: 2012-02-25
forum: Apple Hardware Users
---

### Post by fremantle on 2012-02-25
I am trying to get to my plop boot manager through grub, but it seems like its impossible to open my grub2 menu while booting. I have a macbook with only Ubuntu 11.10 on it, so no rEFIt or anything. i tried holding right shift, left shift keys but to no avail. Any help?

---

### Post by Haventfoundme on 2012-02-26
When it boots up wait for the gray screen to go away. 
After that you should get a black screen with a flashing prompt at the top left hand corner of the screen. 
Hit the "tab" key on your keyboard and the grub menu should come up.
*You could just start hitting the tab key from the gray screen unitl the grubmenu comes up. 
Enjoy!

This worked on a white Macbook Unibody 6,1 (2009), Ubuntu 11.10 x86_64. 


FYI if you don't like the way Grub looks: 
/etc/default/grub line number 25 'GRUB_GFXMODE=1280x800' 
This is so that grub can display using the max resolution for my laptop.

---


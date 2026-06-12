---
title: "Ubuntu wont start"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-22
Hi. my problems started after configuring the x server. i configured the x server because i didnt have direct rendering wich i need if i want to install beryl.so i configured the x server and now ubuntu wont start. it starts to load but when the ubuntu logo (now kubuntu im trying it out) comes up it just freezes there. what can i do i am working from a live cd now.

---

### Post by igknighted on 2007-02-22
> **hempa said:**
> Hi. my problems started after configuring the x server. i configured the x server because i didnt have direct rendering wich i need if i want to install beryl.so i configured the x server and now ubuntu wont start. it starts to load but when the ubuntu logo (now kubuntu im trying it out) comes up it just freezes there. what can i do i am working from a live cd now.

When you get to grub hit 'e' on the Ubuntu login choice.  Then erase any kernel options (such as quiet and splash) and it will show you everything that is happening.  Report back what the last thing it says before it freezes is.

---

### Post by hempa on 2007-02-22
> **igknighted said:**
> When you get to grub hit 'e' on the Ubuntu login choice.  Then erase any kernel options (such as quiet and splash) and it will show you everything that is happening.  Report back what the last thing it says before it freezes is.

i dont get a login choice grub just starts to load ubuntu right away. my login choice comes later when ubuntu is loaded and im typing my password. then i can choose to start ubuntu or kubuntu but i cant get there, becaus the freeze comes before that when grub has already started to load ubuntu.

---

### Post by annda on 2007-02-22
i believe igknighted wants you to hit 'e' in grub - to edit the boot option you have chosen (that is, your ubuntu linux/kernel)

EDIT: sorry, i read your post again and it seems you have 0 delay in grub. you will probably need to correct that first - since it won't even let you boot to recovery mode!

---

### Post by igknighted on 2007-02-22
> **hempa said:**
> i dont get a login choice grub just starts to load ubuntu right away. my login choice comes later when ubuntu is loaded and im typing my password. then i can choose to start ubuntu or kubuntu but i cant get there, becaus the freeze comes before that when grub has already started to load ubuntu.

Try hitting escape right after the BIOS POST screen to bring the menu up, sometimes it is hidden and this should unhide it.  Otherwise, boot the liveCD, mount your partition, and edit the grub menu.lst file manually to not be hidden and have like a 10 second delay.

---


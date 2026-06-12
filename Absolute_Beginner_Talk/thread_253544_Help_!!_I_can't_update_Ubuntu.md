---
title: "Help !! I can't update Ubuntu"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by ISPGUY_01 on 2006-09-08
I need help. I have 2 really Big issues.

First issue.
Everytime I try to update ubuntu I get this message 

E: Archive directory /var/cache/apt/archives/partial is missing. 
How do I fix this issue.m  For this issue I have tried the Apt-get Clean and auto clean commands but that has not fixed the problem.
Any thoughts

Seconed issue.
I have a Dual Boot System. Windows XP and Ubuntu Linux 6.06
The Keyboard will not work in the "Grub" Menu. Once I arrive at the Kubuntu log on screen on can use my Keyboard. 

My Son is freaking out because all his School work/Games are in Windows XP.

Please help.

Thanks
Patrick

---

### Post by whizbaby on 2006-09-08
> **ISPGUY_01 said:**
> 
First issue.
Everytime I try to update ubuntu I get this message 

E: Archive directory /var/cache/apt/archives/partial is missing. 
How do I fix this issue.m  For this issue I have tried the Apt-get Clean and auto clean commands but that has not fixed the problem.
Any thoughts

Don't now how you lost it but does generating it by hand change anything?
**sudo mkdir /var/cache/apt/archives/partial**
> 
Seconed issue.
I have a Dual Boot System. Windows XP and Ubuntu Linux 6.06
The Keyboard will not work in the "Grub" Menu. Once I arrive at the Kubuntu log on screen on can use my Keyboard. 

I guess you've got an USB keyboard? In this case you would have to search a little in your BIOS for an option allowing USB-keyboard (or device) emulation at boot time.(can't know how it's called in your BIOS but it should sound/look similar)

---

### Post by ISPGUY_01 on 2006-09-10
Nope I  have a regular ps2 Keybaord. A strage thing happned. Omce I was in Ubuntu my Mouse did not work. When I switched my regualr mouse for a USB mouse, The USB mouse worked in Ubuntu.

Once I reboot my PC I I get my Standard HP screen with f-1 F-8 and F-10. 
My keybaord will not work in this screen, Then the next screens shows "GRUB" and here my PS2 keybaord does not work. But Once I get to the Ubuntu Screen I can type in my username and password. It's Wired.

I am now able to update Ubuntu and tried to reinstall Grub but that did not work. Any suggestion  on how to fix this issue ?

---

### Post by toasted on 2006-09-10
> **ISPGUY_01 said:**
> 
Once I reboot my PC I I get my Standard HP screen with f-1 F-8 and F-10. 
My keybaord will not work in this screen, 

This screen has nothing to do with the operating system. Check your keyboard and make sure its plugged in completely. Sorry, but sometimes its the simple things. Try another keyboard if needed. You will have to get working at the hardware level before it will work at the software level. Could be a bad keyboard or a bad motherboard too. Lets hope its unplugged  :)

---

### Post by ramcosca on 2006-09-10
> **toasted said:**
> This screen has nothing to do with the operating system. Check your keyboard and make sure its plugged in completely. Sorry, but sometimes its the simple things. Try another keyboard if needed. You will have to get working at the hardware level before it will work at the software level. Could be a bad keyboard or a bad motherboard too. Lets hope its unplugged  :)
Keyboard isn't unplugged. He just said it works when Linux is running, but otherwise it doesn't.

---

### Post by ISPGUY_01 on 2006-09-10
I unplugged my keyboard and even used my wife's Keybaord. No luck. Like I said. Once I get to the Log on screen I can use my Keybaord. If I am in the HP screen or the Grub menu that shows me my boot options I cannot use the keybaord.

What if I switch to Lilo ?

---


---
title: "Another dual boot question"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Airnorm on 2007-03-27
So I have had a great time working with the basic commands from the command line and I have read a lot of info from the site about dual boot problems but my issue is simple and not addressed in the dual boot tutorial. 

I downloaded and installed the alternet desktop i86.iso from the ubuntu site. I used the grub to choose the OS that I would like to use. 

My problem is that grub boots the linux kernal directly to the comand line. I would like grub to boot to the desktop. I can navigate directories and look for files but I don't now how to find Gnome  let alone boot it. so what can I do? the command line is fun but I would like to get work done as well.  Thanks for your help. norm

---

### Post by Hossie on 2007-03-27
Normally Ubuntu boots into gdm (the graphical login manager). Do you have a "2" in your kernel options (look in /boot/grub/menu.lst)? Did you change something in your inittab? Did you change something in your init.d / rc.d?

---

### Post by canadianwriterman on 2007-03-27
Are you sure you didn't download and install the server edition instead of the desktop edition?

---

### Post by Airnorm on 2007-03-27
thanks for your quick response. 
I installed ubuntu-6.10-alternate-i386.iso

Also I did do a single boot install on another hard drive and it booted right into the desktop login screen so that was awesome. Just the dual boot hard drive is giving me the issue. I am also on the windows side of my hard drive right now so I will have to check later as to the "2" when I can get to my second computer and check. Any other ideas or what the command is supposed to look like if I were to edit the grub file. and a little help on making the edit though i think I have the info from the grub tutorial from the main ubuntu site . Thanks for your help. :popcorn:

---


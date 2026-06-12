---
title: "ubuntu noob... questions"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Mr.Bojangles on 2007-01-03
Okay i tried to install fedora core 6, because i have installed FC4 on this laptop inspiron 1150

But when i tried ubuntu 6.10 it would do the loading kernel, etc.. and all that jazz, took it a while but then after it reached 100% it would still be loading the initrd so i waited... a while... and then it went to a complete black screen with the blinking underslash in windows, i know this mean (os is thinking...) so i waited, and waited, and then i waited more. nothing happened... so i did a little bit of research and found xubuntu a lite version whichc requires less. So now i am go to attempt to install this.. anyone know why ubuntu didn't install the first time? i didn't see a system requirements for it. any help or advice for a first timer would be nice.

thanx,
Bojangles.

---

### Post by TooRight on 2007-01-03
The same thing would happen me. It turns out there was nothing at all wrong with the install; the problem was the driver for the ATI graphics card my comp has, lol.

Try running each of these lines  one at a time at the command prompt and hit Enter after each line:

> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig force--initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now




*** press <Ctrl><Alt>F2 to get to the prompt ***

---

### Post by aberry5555 on 2007-01-03
if can't connect to the net yet you can change the drivers to the vesa drivers by doing the following. At the start of the Live CD press f6. Modify this line by deleting the word "splash" and after the "--" put a space and "break=bottom" (or bottom=break, i think it's the first but try either) now press enter and let the OS load up, ignore any error messages and wait for a prompt. When it prompts you to type something type "chroot /root nano /x11/xorg.conf" this will open up the x windows configuration file. Scroll down till you find the heading "device" this should show your graphics card and the driver it uses (quoted to the right). change the driver from"ati" (or whatever is in the quotation marks) to "vesa". now save and exit this program, by pressing something like ctrl+w then ctrl+x, I cant remember but the commands are along the bottom of the screen (save isn't called save, it's called write-out or something). Once you're back at the prompt type in exit and ubuntu should now load, then from there install ubuntu and load the required drivers.

---

### Post by Mr.Bojangles on 2007-01-03
Well i got xubuntu to install fine, now just having some trouble installing ndiswrapper so i can use my wireless card.

---

### Post by riven0 on 2007-01-03
> **Mr.Bojangles said:**
> Well i got xubuntu to install fine, now just having some trouble installing ndiswrapper so i can use my wireless card.

If you haven't already, take a look at [this howto]("http://ubuntuguide.org/wiki/Ubuntu_Edgy").

---


---
title: "[SOLVED] Changed Video Card and now get blank screen on reboot?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by lukejmorrison on 2007-08-27
I changed my video card using the advanced monitor & display settings and then rebooted and now I get a blank screen. Is there a way to get back to the default video card setup? And is there a way to determine what video card I have in my machine? It's a Dell Dimension XPS T500. The Dell site says nothing about the video card so I'm just guessing what is might be.

Luke

---

### Post by w4ett on 2007-08-27
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. 

To determine your video card/chipset your are using from the terminal type:

```
lspci
``` 

Then we can determine what driver to use with your card.

---

### Post by lukejmorrison on 2007-08-27
Do you also know how I can get my system to boot into the command prompt? Is there a hot-key sequence I need to press during boot?

This is excellent! I'll give it a try.

Luke

---

### Post by lukejmorrison on 2007-08-27
Do you also know how I can get my system to boot into the command prompt? Is there a hot-key sequence I need to press during boot?

This is excellent! :KS 

I'll give it a try.

Luke

---

### Post by w4ett on 2007-08-27
From the grub menu select 'recovery mode'....when in a GUI desktop <Ctrl><Alt><F1> will take you to a virtual terminal, also click on Applications>Accessories>Terminal

---

### Post by lukejmorrison on 2007-08-27
W4ett, How do you get into the grub menu? I'm assuming it comes up during the  boot sequence?

---

### Post by w4ett on 2007-08-27
Exactly...it looks like this..immediately after your Post screen:

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/5.png[/IMG]

---

### Post by lukejmorrison on 2007-08-27
thanks! I can't see that picture it's says I don't have access rights to that sever.

How do I mark this question as solved?

---

### Post by w4ett on 2007-08-28
Click on the "Mark Your Thread As Solved" link in my sig for instructions

Good Luck

P.S. I added a thumbnail .png so you can see the Grub Menu

---

### Post by lukejmorrison on 2007-08-28
BTW I followed the instructions in the sticky thread regarding ATI drivers in the latest Kubuntu install and now I was able to pick ati instead of Vesa and bump my resolution up to the highest my monitor can handle. 

Thanks a lot.

Luke

---


---
title: "Usb Mouse Problems (A4 Tech WOP-49), I have toshiba L100-194 notebook"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by bodzasfanta on 2007-01-03
Hey!

My name is Daniel and I write from Hungary, so sorry for my english.

My USB mouse usally blocked after just 2-3 minutes (mainly in Firefox!) and I can't get it to work.
I tried all of the USB ports but it doesn't work. The only thing that I can do to restart the notebook but it also not good cause the mouse does the same after few minutes. Someone told me to try the Ctrl-Alt-Backspace function, but it also doesn't help. I dont want to restart my notebook every 5 minutes (i dont like touchpad)
All the best! I hope someone can help me.

---

### Post by Mr.Hulot on 2007-01-24
Hi! 

I have the same laptop and I had the same problem as you.

If you are using your ethernet card, then that's your problem. 

Some guys here in the forum figured it out. You have to add to the kernel arguments this : irqpoll

try it, you may be in luck ...

---

### Post by mvaranda on 2007-01-25
I had 6.06 working fine in my daughter's laptop Toshiba M50-370.
However, because the Atheros 802.11 was dropping too many packets I decided to upgrate it to 6.10.

Atheros problem was resolved. However, I got the problem with USB Mouse as described.

Actually is the USB that gets screwed.  After the mouse crash even the memory stick does not work in any USB port when connected.

I hope Ubuntu guys fix that. the 6.10 looks very strong. I have it working fine in another laptop.

---

### Post by mvaranda on 2007-01-26
See if the description from 
[http://www.ubuntuforums.org/showthread.php?t=227412&highlight=Mouse+USB](http://www.ubuntuforums.org/showthread.php?t=227412&highlight=Mouse+USB)
works:


"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

---


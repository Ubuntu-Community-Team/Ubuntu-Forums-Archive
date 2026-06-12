---
title: "how to get keyboard working without keyboard support?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by pixelstuff on 2007-03-27
hi
My USB keyboard died and I replaced it, together with the mouse that came with the same usb transmitter with ordinary mouseprort/keyportport devices. Until the bootmenu everythings fine (this is why I am now typing from the XP partition...) but with the splashscreen mouse and kb are both gone. I tried recovery mode boot, hoping it would autorecgnize something but it did not. I could not  type anything at the commandline.
So what can I do ..... please? :icon_frown: I want to go back to the Ubuntu partition, I miss it so   much :cry: 
I quess I could access the xorg file from Windows with some tool, is that recommended? What can I do? Would a live CD help? I dont want to mess up the xorg. And what would I write into it anyways, for normal mouse/keyboard?
Thank you!

---

### Post by mahy on 2007-03-27
Boot Ubuntu Live CD, check its xorg.conf, and replace the one on your hard drive with the new one.

---

### Post by amantonas on 2007-03-27
Maybe dpkg-reconfigure xserver-xorg. I used that to configure my graphics at first, but it asks you about your keyboard and mouse.

---

### Post by pixelstuff on 2007-03-27
:cry: 

thank you for answering! 
mahy, I just tried to boot from the live cd but it recognized neither the keyboard nor the mouse. It only recognized my wacom tablet which is an usb device. 

amantonas, how can I do that without a keyboard? Can I access a terminal somewhere close to the bootsequence where it still works? I cannot type after the recovery mode is fully booted.

I am using older stuff from another PC now but I dont feel like buying new devices without knowing if they will work and how to get them to work.

:cry:

---

### Post by mahy on 2007-03-28
Can you try booting some other distro, e.g. SLAX, running the 'xconf' command (to let it configure X server) and then storing the xorg.conf? I see no reason why normal mouse and normal keyboard shouldn't work... :/

---

### Post by pixelstuff on 2007-03-29
Yes, I also tried Puppy Linux and copied the keybord section into the xorg. When I rebooted I ended up in an ascii decorated window telling me the xorg is broken and if I want to reconfigure. Not possible of course without a keyboard :cry: I was too tired and left it alone. I am too noob to now why the lines that worked in Puppy would not in Ubuntu and I havent got the file here because I am at work now. 
By the way, I am going to buy a new keyboard today, I would be thankful for any buying tips  ;)

---

### Post by pixelstuff on 2007-03-29
so, back home and typing... here for those with a similar problem: I bought a keyboard with an usb/ps2 adaptar (for more possibilities) and one of a famous brand, Logitech. I changed the xorg.conf from Puppy back to its old state and ubuntu booted normally and recognized the keyboard. I still have no mouse but with the wacom tablet I can work and will figure it out somehow. :popcorn:

edit: and to get the ps/2 mouse and keyboard to work I had to disable usb keyboard and mouse support in the bios

---


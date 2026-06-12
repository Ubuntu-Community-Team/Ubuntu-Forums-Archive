---
title: "Large Console and no Loading/Shutdown screens (7.10)"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Amadeo on 2007-10-18
Hello all,

I've just installed Ubuntu 7.10 on this old Inspiron 5000.  Everything is working so far except I believe I am having some resolution problems.  After the GRUB menu, the screen is completely black until X loads and then everything seems fine again.  The same happens when I try to shut down, except for a second or so, I see some text on the screen in huge letters, then it disappears and goes black again until the laptop turns off.  

If I move to a console, the text is gigantic again and covers the entire screen.  The LCD on the laptop is 1024x768.  Not really sure what's going on since I'm pretty new to this whole thing.

Hope someone can help!

---

### Post by Technoviking on 2007-10-18
Do you know what type of video card you have?

---

### Post by Amadeo on 2007-10-18
> **Mike said:**
> Do you know what type of video card you have?

Yes, this is a laptop with an old ATI Rage Mobility P!

Edit:
I should note that when I try to play with the new screen/resolution config tool, I end up with some strange square in the upper left corner of the screen.  Almost looks like a barcode. I also notice that it vanishes after I open a terminal window and start to type anything...

---

### Post by ovitz on 2007-10-18
I'm having this problem too. In 7.04, I had added vga=773 to grub and the loading screen displayed just fine. Now in Gutsy, no matter what vga mode I try, the loading screen is just blank. 

Thanks in advance!

---

### Post by Technoviking on 2007-10-18
> **ovitz said:**
> I'm having this problem too. In 7.04, I had added vga=773 to grub and the loading screen displayed just fine. Now in Gutsy, no matter what vga mode I try, the loading screen is just blank. 

Thanks in advance!

I think you are on the right track, on my old ati card I had vga=721. I suggest doing a google search with vga= and grub, and see what comes up.

---

### Post by Amadeo on 2007-10-18
I've just tried using every vga= mode I could find, but none of them seem to change anything. :(

---

### Post by ovitz on 2007-10-18
> **Amadeo said:**
> I've just tried using every vga= mode I could find, but none of them seem to change anything. :(

Same here. :(

---

### Post by Amadeo on 2007-10-19
Day two! Hoping someone has some new helpful info. :)

---

### Post by jorge.py on 2007-10-19
hi to everyone..

i have the same problem, with a HP nx6115, ATI 200M card, i try the vga=791 option but no changes..:(

this is my entry in menu.lst:
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0cefb248-a46d-4479-bb2c-8bb4e6df89db ro vga=791

please someone...

---

### Post by Amadeo on 2007-10-21
I got wireless working on my laptop and have seen no updates that might fix this issue.  Still hoping someone might know what the problem is.  It seems quite a few people are having this problem!

---

### Post by mihai.ile on 2007-10-21
Acer 1694WLMi with ATI x700
Exactly same problem
A quick fix is needed here.

---

### Post by RedSquirrel on 2007-10-21
This is a known issue. 

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

I would advise you to read the thread, well, at least the last third of it or so.

The following procedure worked for me:

  1. 

```
sudo nano -w /etc/initramfs-tools/modules 
```

and add fbcon and vesafb

  so my /etc/initramfs-tools/modules looks like:
  fbcon
  vesafb

  2. 

```
sudo update-initramfs -u -k all -v
```

  3. 

```
sudo nano -w /etc/modprobe.d/blacklist-framebuffer

```
change the line "blacklist vesafb" to "# blacklist vesafb"

  4. reboot and everything is fine

I used vga=791 in the kernel options.

---


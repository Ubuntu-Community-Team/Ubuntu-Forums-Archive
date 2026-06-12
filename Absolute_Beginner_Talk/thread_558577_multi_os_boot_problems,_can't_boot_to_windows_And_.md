---
title: "multi os boot problems, can't boot to windows? And graphics really ****** up..."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Tilulii on 2007-09-24
As you can see from the screenshot (attatched) something is wron... ATI 9800+, and AT7 motherboard, AMD 2200+... Kind of hard to read the screen :)

I'd like to boot to weindows, but can't do it, as my keyboard doesn't work on in my bootmenu anymore. Annoying, at the least!

---

### Post by BaffledMollusc on 2007-09-24
> **Tilulii said:**
> As you can see from the screenshot (attatched) something is wron... ATI 9800+, and AT7 motherboard, AMD 2200+... Kind of hard to read the screen :)

I'd like to boot to weindows, but can't do it, as my keyboard doesn't work on in my bootmenu anymore. Annoying, at the least!

If your keyboard doesn't work at the boot menu, it doesn't sound like an Ubuntu problem. What did you do immediately before the problem occurred?

---

### Post by Tilulii on 2007-09-24
I can't relly recall. It stopped working at some point, needed to use my WinXP, but relized yesterday that I can't! Havent touched the bootmenu in a while, until the screen got garbled, and I thought to check it out, if it is possible. Could not do anything anymore. 

My keyboard is a Logitech, that sucks *** anyway, and I put a USB-hub in between, as my USB-slots are behind the computer, and I keep my computer in the closet (hate the noise, and it's ugly :), but I ripped the hub away. Still no connection of the keyboard. As soon as Ubuntu kiks in, the keyboard works! Sheisse. Need to force it to boot to Windows, but my Linux skills are next to none...

Edit:

This forum is censored. Way to go.

Bad word are **** ***.

---

### Post by louieb on 2007-09-24
Check your BIOS settings see if legacy USB support is enabled. 

Sorry you can't express your thoughts without cussing.

---

### Post by Tilulii on 2007-09-24
Can't enter my BIOS, as my keyboard doesn't work when I boot up. Just checked it :)
And the USB-thingie is on, as I have checked it earlier, and the boot menu has been working. That's the weird part here. I think my stupid USB-hub did the thing. Have to figure it out somehow, or another.

And it's not about the problem of not being able to express myself, it's just the fact that useless censorship feels, well, ridiculous?

Yay
Elmo and the Acid Monitor!

---

### Post by rolnics on 2007-09-24
I know you'll probably hate this idea, but . . . . . . . have you tried plugging you mouse / keyboard into you base, rather than through your usb hub? In the past I had my keyboard 'n' mouse plugged into a hub until I needed to get to my bios!

---

### Post by Tilulii on 2007-09-24
The hub is long gone, as soon as I suspected it was the problem (extra nice if you happen to have only one USB-device :), so that is gone. Hub was there only to ease the change of songs on my MP3-player. Had the songs there for 1,5 months, ultimate laziness, too much effort to move the computer. Physically...

HAve to trysome other jacks, if they would work, something like a 1,1-jack.

---

### Post by louieb on 2007-09-24
Humm. Your keyboard worked at boot up in the past and the display was ok also.  Is that right?  Kinda sounds like a hardware problem. Had any thunderstorms your way lately?  Can you get your hands on a PS2 keyboard? Do that and check you BIOS then. 

anyway you can modify your /boot/grub/menu.lst to boot XP first.

find your XP entry its probably at the bottom. and put a copy  between the lies that read:. 
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
       ....      your xp entry goes here  ....
### BEGIN AUTOMAGIC KERNELS LIST 

```

Its a pain but if you really need to get to XP then that should work.

---

### Post by Tilulii on 2007-09-24
Got it to work. Found a jack that said 'hell yeah!', and got it to boot to XP. The same problem is there, screen is half garbled, so seems like monitor is screwed. Got this one for free ( I hate computers, so I logically also hate buying computers even more :) from my friend. It had some problems in the past, they were gone, but seems like they are back.

Funny thing is, when I got the bootmenu to work, changed to XP, and now the mouse and keyboard doesn't work in XP :)

Nicenice. More tweaking and working and cursing. Well, C'est la vie!
Almost solved, that is...

---


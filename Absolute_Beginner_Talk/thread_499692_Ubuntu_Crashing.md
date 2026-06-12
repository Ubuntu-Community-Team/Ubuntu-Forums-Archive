---
title: "Ubuntu Crashing"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-12
Ubuntu 7.10 keeps crashing/freezing.
It has happened twice today
The first time I was installing a few things and talking to people on Gaim IM.
Then most recent time I was downloading 2 things using wget on the terminal, and for the other I was using firefox. And I was talking to people on gaim. Any help?!!
It's seems to run fine otherwise. And it's random.

---

### Post by Seisen on 2007-07-12
If your talking about Gutsy Gibbon then yes it will tend to crash because its being tested right now for bugs. If your talking about Fiesty, well thats a different story.

---

### Post by blithen on 2007-07-12
Sorry, it's Fiesty

---

### Post by Seisen on 2007-07-12
Are you running Beryl or Compiz? Also what are the specs of your computer

---

### Post by blithen on 2007-07-12
I don't know what you are asking about the beryl or compiz but my specs are

2.10Ghz AMD Anthlon 3000+ Processor
1.5gig ram
Gnome: 2.18.1 (Ubuntu 2007-04-10)
What else do you need?

---

### Post by Seisen on 2007-07-12
What kind of graphics card do you have?

---

### Post by blithen on 2007-07-12
Geforce FX 5500

---

### Post by Seisen on 2007-07-12
How and what drivers did you install, if you did?

---

### Post by blithen on 2007-07-12
I installed the nVidia accelerated drivers.

---

### Post by Seisen on 2007-07-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It might be related to this bug, did you have this problem before you installed the drivers?

---

### Post by djchandler on 2007-07-12
> **blithen said:**
> I installed the nVidia accelerated drivers.

Go System Administration, then the restricted drivers  selection, and disable the restricted driver.

---

### Post by blithen on 2007-07-12
No, yesterday I reformatted my computer, 'cause I was running xubuntu, and I was looking at Ubuntu, and switched to that. And immediately installed the drivers, and installed my game, and started playing that. And I did have the problem up until recently.

---

### Post by blithen on 2007-07-12
> **djchandler said:**
> Go System Administration, then the restricted drivers  selection, and disable the restricted driver.

Why?

---

### Post by blithen on 2007-07-12
bump

---

### Post by djchandler on 2007-07-13
> **blithen said:**
> bump

The restricted drivers are not open source, and can't be fully supported because the vendor won't divulge driver source code and other tech specs to the open source community. There's no way to ensure compatibility with open source applications. Go back to the open source driver, and see if that stops the crashes.

One more thing. I have found that recovering your system from a crash is easier if you simulate a complete power failure. Use the switch on the power supply in the back, next to the power cord, or unplug the power cord, or turn off the switch on the power strip or surge protector. A hard drive with no power cannot write random data to hard disks and foul up the master boot record or file allocation database/tables. Don't use the reset button from an unrecoverable system crash. I learned that back in my Mac days when System 6 could get all fouled up using reset, or a soft re-boot. 

DJ

PS no more tonight.

---

### Post by Cappy on 2007-07-13
Try boot params:
```
noapic nolapic
```

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Does Alt+Control+BACKSPACE work when it freezes?

---


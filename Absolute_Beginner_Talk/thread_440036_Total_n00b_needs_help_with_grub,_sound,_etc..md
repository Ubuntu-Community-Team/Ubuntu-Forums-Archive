---
title: "Total n00b needs help with grub, sound, etc."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-05-11
When I initially start up my computer I have to quickly catch the grub menu (I only get 2 seconds!) and I have to go in and edit the kernel by removing "quiet splash" and then I can boot up successfully.  How can I change this?

Also I have no sound aside form the system beep.  

Sorry for the seemingly dumb questions...I am overwhelmed by all the information there is out there!

---

### Post by proalan on 2007-05-11
you can alter the grub settings via the terminal

```
gksudo edit /boot/grub/menu.lst
```

and comment out the quiet splash by putting a '#' in front of the line (without the quotes)

not sure about your sound issue without more details

try installing ALSA if you've not already done so

---

### Post by bean77 on 2007-05-11
> **proalan said:**
> you can alter the grub settings via the terminal

```
gksudo edit /boot/grub/menu.lst
```

and comment out the quiet splash by putting a '#' in front of the line (without the quotes)

not sure about your sound issue without more details

try installing ALSA if you've not already done so

This is what I got when I did that.  Sorry I'm not getting this...be patient!

lydia@lydia-desktop:~$ gksudo edit /boot/grub/menu.lst
Error: no "edit" mailcap rules found for type "application/*"
lydia@lydia-desktop:~$

---

### Post by proalan on 2007-05-11
my bad

should be 
```

gksudo gedit /boot/grub/menu.lst
```

'gedit' is the standard text editor program

---

### Post by bean77 on 2007-05-11
OK so before I do it I want to make sure this is what it should look like:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=492c3ad5-3088-4d48-bd4a-57edd1334e17 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

### Post by Henry Rayker on 2007-05-11
> **bean77 said:**
> OK so before I do it I want to make sure this is what it should look like:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=492c3ad5-3088-4d48-bd4a-57edd1334e17 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I believe it should look like this:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=492c3ad5-3088-4d48-bd4a-57edd1334e17 ro #quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

You only want to get rid of the "quiet splash" right?

---

### Post by proalan on 2007-05-11
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic #root=UUID=492c3ad5-3088-4d48-bd4a-57edd1334e17 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

change that to

```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=492c3ad5-3088-4d48-bd4a-57edd1334e17 ro splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

just remove 'quiet'

sorry I'm not fully awake yet, but that should take care of your boot problem

---

### Post by bean77 on 2007-05-11
Great! Thank you!

---

### Post by proalan on 2007-05-11
for your sound problem try
```

sudo apt-get install alsa
```

if its already installed check your sound mixer settings via typing in 'alsamixer' in the terminal

---

### Post by bean77 on 2007-05-11
OK, I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by proalan on 2007-05-11
hmm seems alsa is installed. 

What soundcard do you have?

---

### Post by bean77 on 2007-05-11
It's in my motherboard, right?  I have an MSI pm8pmv

---

### Post by bean77 on 2007-05-11
Bumping to see if anyone can help me...I really appreciate all the input so far!

---

### Post by bean77 on 2007-05-11
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This what I have...

---


---
title: "Asus K55V Function keys"
date: 2013-02-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Sam Lowry on 2013-02-07
Hi,

have a problem with some of the function keys on my Asus K55V: brightness (FN + F5 / F6) and wireless (FN + F2) don't work. I need at east the brightness keys to work.

OS is Kubuntu 12.10. Already updated the kernel to 3.7.6 which activated all other function keys except the mentioned ones. 

I tried  the grub update solution ([http://askubuntu.com/questions/207568/every-function-key-on-laptop-works-except-for-brightness](http://askubuntu.com/questions/207568/every-function-key-on-laptop-works-except-for-brightness)) but without any result.

I also checked the key signal with xev and acpi_listen and figured that the keys are not sending any signal at all so no way to write a script or something.

Any suggestions?

---

### Post by Sam Lowry on 2013-02-07
Finally, I at least found a way to adjust brightness on the command line using

> 
Backlight adjustment for LCD can be done in two ways: 
* values 0 - 4095:
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness(suggested here [http://ubuntuforums.org/showthread.php?t=2005756](http://ubuntuforums.org/showthread.php?t=2005756))

The other methods echoing to */sys/class/backlight/acpi_video0/brightness *or using* xrandr *did not work for me.

Only thing I'm missing now is: how to get the signal from the FN-keys? ...

---

### Post by Sam Lowry on 2013-02-08
Really no one? I know there are some real Pros around here. Can someone give me some hints/keywords/tutorials/pages how to approach this? I'm absolutely new to driver-issues but have some programming and computer skills. So I'd like to at least understand the problem and maybe try to solve it.

What I know:
1. I can adjust the brightness with echo (see above), ergo backlight adjustment should work.
2. I have an entry in my keymap for backlight adjustment, so should work
3. The non-working function key signals don't show up neither in xev nor acpi_listen
 
So I guess the problem is that the kernel does not recognize the keys at all. 
From one point of view, as far as I understand it, the configuration/communication should be done by the acpi-driver. On the other hand, if acpi_listen does not recognize the keys wouldn't thatindiacte that it's not acpi-related?

So questions:
1. Is it right, that the acpi-driver is the one that's defining the action for each keystroke?
2. If so, then it means the acpi driver is the problem, right?
3. Where do I get more information about the acpi-driver and how it works exactly and how to debug it?
4. if it's not the acpi-driver, what else could it be?

Long text, many questions, little knowledge ... hope someone enlightenes me ;)

---


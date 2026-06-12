---
title: "ps2 keyboard and ubuntu 6.10"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by richie06 on 2007-03-04
I recently downloaded and ubuntu 6.10 and ran the live CD the install when i booted up I found that I had use of my mouse without any problems but soon discovered that my keyboard was not working. checked cabling ok. and caps key was working ok. tried changing keyboard in system preferences. made no difference. after a bit of investigation i found that turning num lock off before ubuntu starts loading allows the keyboard to work.  

does anyone know of any permanent fixes for the as it will get quiet annoying having to remember to turn num lock off every time i want to boot into ubuntu

keyboard is a standard ps2 microsoft multimedia keyboard
mobo is gigabyte GA-8I945GMF-RH
1gig ram
his radion 1650 turbo ED




I have previously used and installed ubuntu 6.06 lTS and several other flavours of Linux without having this issue occur. does anyone know a fix for this as it. 


please note i am a newbie when it comes to things like recompiling kernels ETC

thanks for you help

---

### Post by hardyn on 2007-03-04
you should not be having trouble with it. USB i could see, but PS2

does the keyboard work in dos or windows?

try a different keyboard?

---

### Post by mrmonday on 2007-03-04
In your other Distributions which keyboard layout do the use? is it the same as in Ubuntu? if not I think there is an option somewhere to disable it... I will look now for you.

---

### Post by richie06 on 2007-03-04
i have tried all all different keyboard layouts that i thought would be suitable(all microsoft ones) and a few generic


i can reboot system and load into windows and keybaord works ok, have tried ubuntu 6.06 and its working no probs i can reboot system and put koppix live cd in and keyboard will load ok. and currently have version of mepis installed that on another partition that is working ok.

---

### Post by dreager on 2007-03-04
same problem here. USB Keybord won't work with either alternate or live cd. I'm stuck.

---

### Post by FesterHead on 2007-03-05
I had a similar problem with getting a ps/2 keyboad to work with 6.10.
I resolved it based on information in another post:

For each use of the LiveCD:
When the grub countdown appears, press "Esc" to get a listing, press "e" to edit the kernel, add "usb-handoff" (without the quotes) after "ro" (I also removed quiet to get more bootup feedback), "enter" to accept then "b" to boot.

After installation:
Edit the grub menu list as sudo and put in the "usb-handoff" parameter.

---

### Post by wietse_nieuwland on 2007-07-12
For me this did not work. Going back to kernel 2.6.17.11 did!

Have a nice day!

Wietse

---


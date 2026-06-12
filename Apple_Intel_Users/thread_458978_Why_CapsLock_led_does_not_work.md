---
title: "Why CapsLock led does not work?"
date: 2007-05-30
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-05-30
Hi All!

Why CapsLock led doesn't work on my iMac with Ubuntu Feisty?
I thought this feature is not software-dependent. :(

---

### Post by joselin on 2007-05-30
Does not work in mine too and i couldn't find too much info on this. But i wanted to subscribe this thread.

Regards.

---

### Post by ronocdh on 2007-05-30
Have you guys had any luck with Num Lock? There have been reports that on the MacBooks (first gen, I believe) the Num Lock can be turned on and off by connecting and disconnecting USB peripherals, such as a mouse. Wow, what an annoyance! Please let us know if you guys experience anything like this, too.

I have once or twice had my Caps Lock light work in Ubuntu, but given my frequent reinstalls for fun, I haven't been able to trouble shoot what's different. =/

---

### Post by anujseth on 2007-05-30
I second what ronocdh says ... i too have had them working some times ... and through my frequent re installs and re partitioning i first believed that selecting the US-English Macintosh keyboard gets them to work. And it did a few times to ... but now it doesnt seem to work. Any way the lights always work with Live CD. Strange.

Ohh yes I had the num lock and caps lock lighting thing on USB devices also. This happens when you delete the Mac OS X partition completely(not EFI) and run Ubuntu.

---

### Post by .bashrc on 2007-05-30
Just to confirm that it worked in Edgy.

---

### Post by ivesjd on 2007-05-30
I just hit my num-lock to see if it lit up and it did! Then I remembered Im in OS X :-\"

---

### Post by fractalzero on 2007-05-31
Try looking through the different keyboard layouts. IIRC under the default layout the capslock key doesn't light, but there's a layout where it lights up as usual.

---

### Post by Ubivetz on 2007-05-31
I'm using Russian layout
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,ru"
	Option		"XkbVariant"	",winkeys"
	Option		"XkbOptions"	"grp:ctrl_shift_toggle,grp_led:scroll"
EndSection

```

Another problem is when input language is Russian, ctrl-c/ctrl-v keys don't work as expected.

---

### Post by andrewbossie on 2007-06-01
i have a first generation mac book and my caps-lock and num-lock both work fine

---

### Post by themoebius on 2007-06-01
I have the Macbook Pro core 2 duo with feisty and I can confirm that neither the caps lock or num lock LED work

---

### Post by tchorix on 2007-06-01
I have a macbook pro first generation. In the beginning the Capslock was working fine, but not the LED... Since I don't really use capslock, I set it as composing key and everything works fine. For the numlock. It doesn't work at all.... and I also had the problem with the usb turning the numlock on, but I haven't been able to reproduce this problem anymore since I updated to the new linux kernel 2.6.20-16.... and I really tested it. I hope the problem is gone forever, and that next update will allow me to turn on/off the numlock at will.

cheers
Tch

---

### Post by ivesjd on 2007-06-01
I have 1st gen macbook and num lock and caps lock led's work fine (and I am in Ubuntu this time!)

---

### Post by Azathoth_ on 2007-06-03
It seems to work with last revision of the kernel on Feisty (revision 26)

---

### Post by ivesjd on 2007-06-04
Tried to use num-lock last night. The led works but the num-lock key itself doesnt do anything :( not that big a deal on a macbook (since the number layout is awkward to use). But just thought I would post it.

---

### Post by tideline on 2007-06-14
My num lock came on after hibernation, but the system wouldn't reall wake up.  Neither work for me atm.  However, I have a strange red light coming out of my headphone jack on the side.... anyone know what that is?

---

### Post by thonuz on 2007-06-14
pro core 2 duo, cap lock and num lock work without any configuration here.

---

### Post by thully on 2007-06-15
I can confirm that the root of all caps-lock/num-lock problems on Macs is...mouseemu - the program that emulates right-click/middle-click.  If you uninstall it (and use something else for right-click like multi-finger tap or xkbmap), this will fix the issue completely.  I heard this somewhere and confirmed it on my MacBook.

---

### Post by kzm. on 2007-06-15
i recognized that if i install mouseemu my caps-led stops working.. may be the case here. deinstall mouseemu and it works again

---

### Post by Ubivetz on 2007-06-15
Yes! It works on my iMac 17"!

Could someone put this hint to the Wiki?

---

### Post by joselin on 2007-06-16
Works for me too on 24" iMac. Great!!!!

---

### Post by idn on 2007-06-16
Works on my MBP Core Duo

---

### Post by kzm. on 2007-06-17
i actually would like to know the best solution so far to have the mouse behave like under osx (option+click=right click), without any problems.
whats this "xkbmap" or "multi-finger tap"? any experiences and how-to's?

---

### Post by Ganonzote on 2007-06-17
I have the same problem on macbook core2duo, during booting the keys work fine, when booting is about 80% of progress it doesn't, i think it could be a incompatible module loading or something similar, i will try to boot without splash and quiet mode and see what load when it breaks.

---

### Post by ivesjd on 2007-06-29
I just reinstalled and my capslock light wasnt working. I uninstalled mouseemu and it worked.

---

### Post by grim1234 on 2007-07-01
It's not working for me just after installing 7.04 with a macintosh gb keyboard layout.

---

### Post by thully on 2007-07-01
Remove mouseemu (sudo apt-get remove mouseemu in a terminal) - it conflicts with the LED.
However, you will lose F11 middle click/F12 right click, though two-finger tap for middle click/three-finger tap for right click works fine.  If you want a key for middle/right click, you will have to try something else like xkbmap (info should be somewhere in the archives or on google) to map the keys.

---

### Post by Ubivetz on 2007-07-02
> **Ganonzote said:**
> I have the same problem on macbook core2duo, during booting the keys work fine, when booting is about 80% of progress it doesn't, i think it could be a incompatible module loading or something similar, i will try to boot without splash and quiet mode and see what load when it breaks.
Maybe you haven't update your EFI firmware through OSX Updates?

---

### Post by imputerate on 2007-07-13
On a vanilla pc desktop: ubuntu 7.04. 
In the terminal,
Caps Lock LED lights up.
BUT the keyboard delivers only lower case letters.
AND complex passwords [e.g. for ssh login] cannot be typed in from the terminal keyboard, using Shift.
NB these passwords work fine in an xterm window, or even in the terminal, if I have ssh'd into the ubuntu box from another computer.  

[Scroll Lock and its LED word fine]

---

### Post by russo.mic on 2007-07-26
Just confirming that removing mouseemu got both keys working.

Although, I think i'd rather have mouseemu.

Hmmmm....

Russo

---

### Post by xjgnsdof on 2007-11-23
I had this same problem on a Compaq Presario V2000 and a custom built PC with a Kensington keyboard. Removing mouseemu worked on both rigs. Nice.

---


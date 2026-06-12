---
title: "[SOLVED] dual monitor nvidia geforce fx 5200"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2008-02-02
i have the above stated video card 

xorg does not recognize this card but if i manually add it under >  sudo dpkg-reconfigure xserver-xorg
it work fine and even sees my monitor's  two matching westinghouse 19" lcd's

only thing if i try to use both monitors i cant seem to get  ti to happen there are a few things that happen if i try the system>administration>.screens and graphics

this sees one monitor at 1400x1050 resolution and calls it custom 1 and the other at unknown 640x480 and it will not let me use it 

during another attempt at getting it to work i was able to get both monitors up and working but monitor 1 has a size bigger than the monitor its self, so when the pointer moves to the edge of the screen the whole screen pans to the side top or bottom

and during another attempt i have completely killed x and had to do >  sudo dpkg-reconfigure xserver-xorg
 from the terminal during boot up to get back into the graphical part (what is the term for this? ) 

i suppose there will be a ton of questions and ill try to answer them as best as i can thank you

---

### Post by overdrank on 2008-02-02
> **rexxxlo said:**
> i have the above stated video card 

xorg does not recognize this card but if i manually add it under it work fine and even sees my monitor's  two matching westinghouse 19" lcd's

only thing if i try to use both monitors i cant seem to get  ti to happen there are a few things that happen if i try the system>administration>.screens and graphics

this sees one monitor at 1400x1050 resolution and calls it custom 1 and the other at unknown 640x480 and it will not let me use it 

during another attempt at getting it to work i was able to get both monitors up and working but monitor 1 has a size bigger than the monitor its self, so when the pointer moves to the edge of the screen the whole screen pans to the side top or bottom

and during another attempt i have completely killed x and had to do  from the terminal during boot up to get back into the graphical part (what is the term for this? ) 

i suppose there will be a ton of questions and ill try to answer them as best as i can thank you

Hi and have you tried the nvidia-glx  driver and also Envy.

---

### Post by rexxxlo on 2008-02-03
im not sure how to check if i have the nvidia glx driver 

and envy i just tried today  it seemed to do what it was supposed to do ?

---

### Post by overdrank on 2008-02-03
> **rexxxlo said:**
> im not sure how to check if i have the nvidia glx driver 

and envy i just tried today  it seemed to do what it was supposed to do ?

HI and this command should let you verify the nvidia driver is install ```
cat < /etc/X11/xorg.conf |grep Driver
```
Example
   Driver         "kbd"
    Driver         "mouse"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "nvidia"
And if you are using the nvidia driver then use this command for the nvidia settings to configure the dual monitors ```
gksudo nvidia-settings
```

---

### Post by rexxxlo on 2008-02-03
> lolo@lolo-desktop:~$ cat < /etc/X11/xorg.conf |grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"
        Driver          "vesa"
        Driver          "nvidia"



how is this ?

---

### Post by rexxxlo on 2008-02-03
> gksudo nvidia-settings

this fixed everything wow thanks that was easy thought i would be doing commands for a week.

is there any way to disable my onboard gpu ?
the bios just give the option to choose what one is first during boot.

---

### Post by PinkFloyd102489 on 2008-02-03
There should be an option in your BIOS to select the primary display device.

---

### Post by rexxxlo on 2008-02-04
> **PinkFloyd102489 said:**
> There should be an option in your BIOS to select the primary display device.

check my last post i did that already. but if i do lspci it shows up 
and  gksudo nvidia-settings shows it too (its a nvidia too)

i want to completely disable it although im not sure if its a good idea or even possible.

---


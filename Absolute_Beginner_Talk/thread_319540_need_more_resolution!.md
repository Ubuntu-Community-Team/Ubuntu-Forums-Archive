---
title: "need more resolution!"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by TheOtherLinuxFreak on 2006-12-15
im running Xubuntu on a 233mhz pentium 2 with 192 mbram and i cant get the screen resolution any higher than 800 x 600. does any one no of a program that lets u make ur reselution higher?

thanx for the help

---

### Post by Exillo on 2006-12-15
It might be your monitor, what monitor do you have?

---

### Post by TheOtherLinuxFreak on 2006-12-15
a 17 in crt monitor made by hp. i tried it on a different moniter but it did the same. 800x600 is the highest choice in the menu where u pick ur resolution.

---

### Post by Exillo on 2006-12-16
Hmm, maybe it's just old hardware then although don't take my word too seriously. =/

---

### Post by pgatrick on 2006-12-16
You may need to edit /etc/X11/xorg.conf to include the higher resolutions. :-k

---

### Post by TheOtherLinuxFreak on 2006-12-16
i had windows installed in that same pc and it had more reselution. as for editing that file what do i add 2 it ??

---

### Post by TheOtherLinuxFreak on 2007-01-01
i looked at the file and it included the extra reselution. but where my display properys are, there is not any more reselution than 800 x 600

---

### Post by Jorge32 on 2007-01-01
try changin  the xconf with this```
sudo dpkg-reconfigure xserver-xorg
```
it also might be your video card, what model is it?

---

### Post by oilchangeguy on 2007-01-01
from the tabs at the top of the desktop have you tried, system, perferences, screen resolution?

---

### Post by kepos on 2007-01-01
which graphic card do you use?

i had the same problem with my nvidia, and all i have to do was just installing the right nvidia driver.

---

### Post by TheOtherLinuxFreak on 2007-01-01
its built in to the mother board. the motherboard is a dell optiplex gxa. an old pentium 2.

---

### Post by TheOtherLinuxFreak on 2007-01-01
> **Jorge32 said:**
> try changin  the xconf with this```
sudo dpkg-reconfigure xserver-xorg
```
it also might be your video card, what model is it?

i tried that and then i went xfcemenu -> settings -> display settings and it was the same as before.

---

### Post by TheOtherLinuxFreak on 2007-01-01
> **oilchangeguy said:**
> from the tabs at the top of the desktop have you tried, system, perferences, screen resolution?

where do u mean?

---

### Post by oilchangeguy on 2007-01-01
my fault, i guess xubuntu is laid out differently than ubuntu. i would think somewhere in there you would have these things available to you. not sure what the min system requirements are for ubuntu, you might consider upgrading to version 6.06. not 6.10 this is a test version that in reading here seems to have many problems, 6.06 is "lts" long term support (3yrs. as opposed to 3mos.)

---

### Post by TheOtherLinuxFreak on 2007-01-01
in the display settings u can change ur reselution but the it only lets u choose up to 800 x 600

---

### Post by MkfIbK7a on 2007-01-01
i know excactly what to do
sudo dpkg-reconfigure xserver-xorg
when it asks you about resolution only choose what it should be e.c. choose only 1024x768 deselect all other resolutions
next when it asks you something about simple medium advanced choose simple then choose 17 in monitor i had that excact problem and this is how i fixed it

---

### Post by TheOtherLinuxFreak on 2007-01-01
> **wert613 said:**
> i know excactly what to do
sudo dpkg-reconfigure xserver-xorg
when it asks you about resolution only choose what it should be e.c. choose only 1024x768 deselect all other resolutions
next when it asks you something about simple medium advanced choose simple then choose 17 in monitor i had that excact problem and this is how i fixed it

i tried that and it didnt work.
o yeah , is ur monitor 17 inches?

---

### Post by MkfIbK7a on 2007-01-01
yup

---

### Post by MkfIbK7a on 2007-01-01
oh yeah i forgot after doing that press control+alt+backspace this will restart your x server

---

### Post by TheOtherLinuxFreak on 2007-01-01
my screen just turned to a small square. i looked in the display settings but it only let me choose up to 800 x 600

---

### Post by MkfIbK7a on 2007-01-01
small square? did you restart the x server?

---

### Post by TheOtherLinuxFreak on 2007-01-01
well not smal but is was smaller than the screen. yes i restarted the xserver.

---

### Post by MkfIbK7a on 2007-01-01
hmm...........................................my mothers laptop had the same problem but i forget how i fixed it im sorry :(

---

### Post by TheOtherLinuxFreak on 2007-01-01
when u go to the display options on yours it shows more resolution than 800x600?

---

### Post by MkfIbK7a on 2007-01-01
of course my monitor is up to 1400 by 900

---

### Post by TheOtherLinuxFreak on 2007-01-02
ok. i need more reselution bcause when i use the internet, i can only see half of the page and i have to scroll to the side. it very anoing!

---

### Post by tuxcantfly on 2007-01-02
try installing binary drivers, if you haven't already done so; nvidia-glx for nvidia, and xorg-driver-fglrx for radeon, then do a sudo dpkg-reconfigure xserver-xorg and select nvidia or fglrx

---

### Post by TheOtherLinuxFreak on 2007-01-02
i have a ati built in the motherboard.  2mb:lol:

---

### Post by TheOtherLinuxFreak on 2007-01-02
where do i find drivers for it?

---

### Post by TheOtherLinuxFreak on 2007-01-02
can anyone else help me?

---

### Post by TheOtherLinuxFreak on 2007-01-05
does anyone know of a good website to find drivers for linux?

---

### Post by TheOtherLinuxFreak on 2007-01-09
i installed it on a different pc and it looks fine so how do i make it work on this one??

---

### Post by quartzy on 2007-01-09
You may have to turn the depth down, many monitors or video cards will only run higher resolutions with a lower depth.  I like it defaults to 24 so maybe turn it down to the next one which is.. 16?

---

### Post by TheOtherLinuxFreak on 2007-01-09
ok i  will try that

---

### Post by MkfIbK7a on 2007-01-09
yes the last question \

sudo dpkg-reconfigure xserver-xorg

asks you should be answered 16
this will turn down the depth then press 
ctrl+alt+backspace to restart the xserver see if that helps

---

### Post by TheOtherLinuxFreak on 2007-01-09
thanks!!!!!!!:-D :-D :-D :-D :-D :-D :-D  it worked!!!

---

### Post by MkfIbK7a on 2007-01-09
im glad and im sure qyartzy is also :)

---

### Post by TheOtherLinuxFreak on 2007-01-09
now when i rowse the web and i scroll down its choppy.  it doesnt do this on the other pc. now what do i change?

---

### Post by MkfIbK7a on 2007-01-09
what graphics card are you using it may need a driver...

---

### Post by TheOtherLinuxFreak on 2007-01-09
i dont know for sure....... but when i do xserver-xorg it said vesa.

---

### Post by MkfIbK7a on 2007-01-09
vesa is generic
 i think you are going to have to open your computer and read it of the card...

---

### Post by TheOtherLinuxFreak on 2007-01-09
its built into the mobo. but ill try to see it i can see anything,

---

### Post by MkfIbK7a on 2007-01-09
yes and maybe when you start the computer before grub it says your card name...
if none of this helps i suggest you use dillo or epiphany webbrowser...
could you post your ram and prossecor?

---

### Post by TheOtherLinuxFreak on 2007-01-09
pentium 2 266mhz
192mbram

---

### Post by TheOtherLinuxFreak on 2007-01-09
now i tried a diffrent web browser and it did the same.

---

### Post by MkfIbK7a on 2007-01-09
well im sorry but i dont think you can improve it considering the mhz of your proccesor...

---

### Post by TheOtherLinuxFreak on 2007-01-09
it worked before i did xserver-xorg.

---

### Post by TheOtherLinuxFreak on 2007-01-10
last night i put in a 333mhz prosessor and 256 mbram and now it works fine. thanks for all your help:)

---

### Post by Rui Pais on 2007-01-10
hi,
anyway you are still using a vesa generic driver... you could try to load ati module (drivers on linux are called modules) by editing you xorg.ong file and replace the line: 
Driver "vesa" with Driver "ati" 
Save and restart X.

If it works you could then try to go back to 24 (on your last replace the 16 as default option.

Modules/drivers are inside the folder */lib/modules/<your_kernel_version>/* 
Try (on dapper) 
```
ls /lib/modules/2.6.15-*/kernel/drivers/video/
```

You can load a modules doing (as an example):
```
sudo modprobe ati
``` (don't type the .ko extension name)
Auto completion (pressing TAB key) works on modprode too...

and see what modules are loaded with **lsmod**.

The comand **lspci** should give any information about your hardware, including video card (chip) models.

---

### Post by TheOtherLinuxFreak on 2007-01-10
oh yeahh.. i forgot to say that i found a name an the mothrbord and i tryed that driver in xserver-xorg and now it worked. so it was not the cpu, but the diffrent driver.

---

### Post by Rui Pais on 2007-01-10
> **TheOtherLinuxFreak said:**
> oh yeahh.. i forgot to say that i found a name an the mothrbord and i tryed that driver in xserver-xorg and now it worked. so it was not the cpu, but the diffrent driver.

Ah i should have gessed... :)
cpu only changes the speed of processes, the video resolution and quality of image are up to the modules/drivers.

---

### Post by PatrynXX on 2007-01-24
Had the same problem and followed what was written and it didn't do a thing until someone wrote that one had to restart the x server via control alt backspace.  Went poof.  had the big Nvidia Emblem show up.  Took a complete reboot to make it work right, but no more flicker screen.  I'd like it at 85 hz but 75 is better than 60.  I'm sorta new to linux.  I had Linspire before this, but a teacher suggested Ubuntu.  I've got a PVM switch to switch me back over to the other computer of mine which is the main lil XP.  Have no desire right now to go to Vista.  So far Ubuntu has been good and in this res better. :)  :guitar:

---


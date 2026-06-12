---
title: "why wont games work?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2007-11-29
i dopwnloaded 3 games so far that didint work....
americas army: the screen goes black
flightgear: wont start
vega strike: it starts and then shuts down and the computer gets stuck and i have to restart.
what can i do? i dont know what my video card is all i know is that its nvidia 6000 or something like that

---

### Post by getut on 2007-11-29
All of those are 3d games. 

1) What video card do you have?

2) If its a decent 3d performer are the correct drivers loaded? Drop to a terminal window and run the command below
```
glxinfo | grep renderer
```

Post back with info.

---

### Post by shayvasa on 2007-11-29
it says yes

---

### Post by getut on 2007-11-29
"Yes" usually isn't an output of that command.

Run the command and see what your renderer is.. it will usually be something to the effect of "NVidia something", "ATI Something", "Intel something" or software renderer.

If its software then either you don't have 3d card capable of those games or you don't have  driver problems for the card that IS capable.

---

### Post by shayvasa on 2007-11-29
yeah sory here it is:
OpenGL renderer string: GeForce FX 5200/AGP/SSE2

---

### Post by aheicher on 2007-11-29
i have the same problem:
Ive been trying to run EvE and it tells me that "Your OpenGL drivers do not appear to be setup correctly. Please check the documentation for your Linux distribution and your graphics card drivers to ensure proper installation." so i go to nvidia-settings and it tells me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " i ran the command and restarted the server (ctrl+alt+bksp) and  it did not work.  xorg.conf section on nvidia:

```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```

I have an : GeForce 6100 nForce 405/PCI/SSE2/3DNOW! (according to glxinfo | grep renderer)

i would appreciate any help you guys could give me....also in configuring openGL.
Thanks

Amd Semperon processor
Emachine T3626
Nvidia GeForce 6100 GFX card
Ubuntu 7.10 gutsy


Thanks

---

### Post by aheicher on 2007-11-29
*bump* 
anybody?

---

### Post by shayvasa on 2007-11-30
i really need help in this pla any1

---

### Post by aheicher on 2007-11-30
um....wow, this is a problem....HELP PLEASE

---

### Post by LowSky on 2007-11-30
Please be kind to us, we are only regular user like yourselves...

try using Envy to set up your dirvers, it works for ATI and Nvidia graphics cards

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Please try searching google or the forums for answers before making "HELP!!!" posts

---

### Post by Tomosaur on 2007-11-30
If you're on Gutsy, then go to System > Administration > Restricted Drivers Manager. It should recognise your nVidia card and offer to download and install the driver. The nVidia driver is 'restricted' because it is proprietary, and Canonical can't legally have it pre-installed for people.

---

### Post by aheicher on 2007-11-30
ill try envy...my bad about the help thing
tried envy, didnt work

---

### Post by LowSky on 2007-11-30
i just look up both graphics chips listed, because sometihing seems a little odd about the numbers you gave. first off Geforce 6100 is an on board grapihic chip. it isn't made to run graphic intense games. The Geforece FX 5200 is kinda old (about 4 years) and lowest model of the FX 5000 series... it might run some stuff, but nothing new.

You are trying to run high-end games on old/low end graphics chips. Sorry but your equiptment might not be able to run this stuff..

---

### Post by shayvasa on 2007-11-30
but why did it work in windows and in linux it doesnt...i could play AA in wndows but not in linux...why?

---

### Post by shayvasa on 2007-11-30
i have a theory and i need u guys to tell me if its possible this is the problem. i think the games work in windows because it doesnt have compiz fusion, and compiz fusion uses some ram. i have 512MB. so what i think happenes is that when i try to play a big game like AA it uses 100% of my ram and crushes. for example in linux without having anything open im using 40-50% and in windows im guessing it was 10-20%
can that be it?
how much does a 512MB chip can cost?

---

### Post by aheicher on 2007-12-01
a 512 isnt that expensive.  Your theory is possible....but then again I am not much of a linux buff myself.  I got a bunch of other games to work (AssaultCube, AlienArena, etc) but now any high up ones...

---

### Post by lightstream on 2007-12-01
> **shayvasa said:**
> i have a theory and i need u guys to tell me if its possible this is the problem. i think the games work in windows because it doesnt have compiz fusion, and compiz fusion uses some ram. i have 512MB. so what i think happenes is that when i try to play a big game like AA it uses 100% of my ram and crushes. for example in linux without having anything open im using 40-50% and in windows im guessing it was 10-20%
can that be it?
how much does a 512MB chip can cost?

I have no problems running games under Wine and I only have a 256 Mb card (although a little more recent than your model). 

I normally run the game in its own Xsession with a script like this:

```
#!/bin/sh

sudo X :3 -ac &
cd "~/.wine/drive_c/Program Files/Steam"
DISPLAY=:3 WINEDEBUG="fixme-all" wine steam.exe
```

Obviously this is for Steam, which runs perfectly. As does WoW. You'll need to change the last and second-from-last lines for your particular game.

However the games do run almost or just as smoothly even if I run them in the compiz X session - the main reason I do it this way is that my icons in my panel get messed up when Wine switches resolution. A little bit of overkill, but it works!

You can even kill your regular X session and run a script like this quite easily which would completely rule out compiz issues. To do so, go to a console login by hitting Ctrl-Alt-F1 and logging in. Then kill your current compiz X session with **sudo killall gdm**. Now run the script. In my case this makes surprisingly little difference to the frame rates, but it may be different for you.

Anyway, have you checked the game compatibility on the Wine Apps DB (google it)? You will find out whether or not your game can run there, and also there are a lot of useful tips that users post if you scroll down to the comments.

---

### Post by SunnyRabbiera on 2007-12-01
> **shayvasa said:**
> but why did it work in windows and in linux it doesnt...i could play AA in wndows but not in linux...why?

two different operating systems...
remember:
Linux is NOT windows
sometimes stuff like this happens, sometimes its not our fault too

---

### Post by shayvasa on 2007-12-01
i never said it was your fault....and light stream im trying to run games that dont need wine

---

### Post by SunnyRabbiera on 2007-12-01
> **shayvasa said:**
> i never said it was your fault....and light stream im trying to run games that dont need wine

I was referring to linux in general, I am no developer.
I have found that sometimes errors like this can occur on linux even if something says it has linux support.
Linux can be tetchy sometimes, but not all the time a problem is due to linux but whatever you try to run on it.
I am hoping you can get your issue fixed however, but this is one of the reasons why most dual boot as sometimes stuff does not work 100% under linux.
but its getting close, linux has progressed a lot over the last decade and it can only get better over time.

---

### Post by shayvasa on 2007-12-01
ok thanx...i am trying to dual boot but till then i wanted to play games and i cant :(

---

### Post by lightstream on 2007-12-02
> **shayvasa said:**
> i never said it was your fault....and light stream im trying to run games that dont need wine

doh, sorry...

so AA is available for linux?? <tootles off to Google> Don't have any good download links for it do you??

Edit: am downloading the other two games you mention as they look like fun, will let you know if I get any problems.

Do you have any issues running other less graphics-intensive OpenGL games, such as Neverball, or Billiard GL?

---

### Post by Tomosaur on 2007-12-02
> **lightstream said:**
> doh, sorry...

so AA is available for linux?? <tootles off to Google> Don't have any good download links for it do you??

America's Army is available for linux, but they don't release new versions of it for Linux any more. The current Linux version is a few versions behind the current Windows version.

---


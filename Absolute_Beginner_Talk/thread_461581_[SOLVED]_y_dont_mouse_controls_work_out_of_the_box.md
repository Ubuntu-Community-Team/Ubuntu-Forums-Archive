---
title: "[SOLVED] y dont mouse controls work out of the box on linux distros - discussion"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-06-01
something thats been bothering me 4ever on any linux distro sofar is the fact that your mouse forward back buttons browser or folder navigation dont work right out of the box. 
i'm not trying to diss here cause i love ubuntu, got everything to work with imwheel etc but why hasnt anyone made a little prog or something where you just get a graphical interface click all your buttons and assign them to the right function... 
i mean that functionality has been missing from every linux distro i've tried for years and no one seems to ever change that :confused: 
im just thinking that i shouldnt be too hard for some crack programmers to make it work right .

so what do you think about this ?

---

### Post by Hendrixski on 2007-06-01
I'd also like to know why the right click button doesn't work out of the box on my tablet :-(  nor the rotate button on the screen.

---

### Post by daimaru on 2007-06-01
yeah i just dont get it that no one ever put any effort in to solving this... i mean this should be a minor thing shouldnt it ? how hard can it be capture mouse click events and ask the user to define the function or something . this really annoys me :)

---

### Post by daimaru on 2007-06-01
bump

---

### Post by KIAaze on 2007-06-01
Are you talking about a mouse with more than 3 buttons?
Because I don't see how clicking left/right mouse buttons to go backward/forward is practical.

In that case, it might just be because a lot of people have simple 3 button mice. ^^

> nor the rotate button on the screen.
?
The scrool wheel? That works fine for me.
Or do you mean the middle button click to go up or down in a page by simply moving the mouse?
For this I also wonder why it's not implemented.
Probably because of the middle button paste function (which is also very practical).

If all mouse buttons and wheels are detected correctly, I also think it shouldn't be too hard to configure them, altough I have no idea how exactly this is done.

P.S: You can always use the mouse gestures extension for Firefox to easily go forward/backward and even more. :)

---

### Post by jimrz on 2007-06-01
> **daimaru said:**
> something thats been bothering me 4ever on any linux distro sofar is the fact that your mouse forward back buttons browser or folder navigation dont work right out of the box. 
i'm not trying to diss here cause i love ubuntu, got everything to work with imwheel etc but why hasnt anyone made a little prog or something where you just get a graphical interface click all your buttons and assign them to the right function... 
i mean that functionality has been missing from every linux distro i've tried for years and no one seems to ever change that :confused: 
im just thinking that i shouldnt be too hard for some crack programmers to make it work right .

so what do you think about this ?

maybe because there are so many different brands and models available.
BTW ... those extra buttons do not work OTB in windows either (not even those branded MS and sold under their name), you must install drivers (and what ever else the OEM feels like including in their "driver" cd) before you get full functionality. i much prefer a simple modification to my config file to the other way.

---

### Post by daimaru on 2007-06-01
> **jimrz said:**
> maybe because there are so many different brands and models available.
BTW ... those extra buttons do not work OTB in windows either (not even those branded MS and sold under their name), you must install drivers (and what ever else the OEM feels like including in their "driver" cd) before you get full functionality. i much prefer a simple modification to my config file to the other way.

hmm not quiet right there mate.... im not a microsoft fan, use ubuntu for everything only switch to windows if i really have to. but quite frankly a 7 button mouse (left right mousewheelup mousewheeldown mousewheelclick backward and forward button ) work out of the box on every mouse i've used so far. 
to clarify im talking about the browser back and forward functionality (history) as well as the folder history. 
scrolling up down in browser and folders on filesystem works out of the box on ubuntu too (at least with my mouse) but not the back forward stuff in folders or in firefox. 

as i said before i know how to get it to work but hey why do i have to edit my xorg.conf file adding crap like  1 2 3 6 7 5 4  (most of the time guessing until i get it right) and installing imwheel to make it work. :p 
just saying isn't it time for linux distors to include mouse functionality for more that 3 buttons.

---

### Post by jimrz on 2007-06-01
> **daimaru said:**
> hmm not quiet right there mate.... im not a microsoft fan, use ubuntu for everything only switch to windows if i really have to. but quite frankly a 7 button mouse (left right mousewheelup mousewheeldown mousewheelclick backward and forward button ) work out of the box on every mouse i've used so far. 
to clarify im talking about the browser back and forward functionality (history) as well as the folder history. 
scrolling up down in browser and folders on filesystem works out of the box on ubuntu too (at least with my mouse) but not the back forward stuff in folders or in firefox. 

as i said before i know how to get it to work but hey why do i have to edit my xorg.conf file adding crap like  1 2 3 6 7 5 4  (most of the time guessing until i get it right) and installing imwheel to make it work. :p 
just saying isn't it time for linux distors to include mouse functionality for more that 3 buttons.

sorry...I, too, have 7 button mice (mouses? what the hell is the correct plural for these things, anyway?) on each of my desktops (2 @ home + got 1 for my work one, as well) and always have to install the software to get them fully working in XP. not an MS fan either, but i do use their mice (also have 1 of their wireless usb mice for use with my laptop). the laptop mouse only has 3 buttons and does not require additional driver or s/w nor is any mod to xorg.conf required.

wouldn't it be something if EVERYTHING MS offers were at the outstanding level of quailty shown in their mouse/keyboard products. :)

---

### Post by daimaru on 2007-06-01
> **jimrz said:**
> sorry...I, too, have 7 button mice (mouses? what the hell is the correct plural for these things, anyway?) on each of my desktops (2 @ home + got 1 for my work one, as well) and always have to install the software to get them fully working in XP. not an MS fan either, but i do use their mice (also have 1 of their wireless usb mice for use with my laptop). the laptop mouse only has 3 buttons and does not require additional driver or s/w nor is any mod to xorg.conf required.

wouldn't it be something if EVERYTHING MS offers were at the outstanding level of quailty shown in their mouse/keyboard products. :)

LOL ::) weird i bought a habu gaming **** mouse (dont recommend it at all) from microcrap had loads of trouble with it but it did work right away at least the buttons :p the 2000dpi and 1000hz polling didnt work at all --> well thats microsoft for you, even their own products dont work out of the box on their own system without driver install or firmware update (which does not really work well) =D>

---

### Post by KIAaze on 2007-06-01
> **jimrz said:**
> mice (mouses? what the hell is the correct plural for these things, anyway?)
singular: mouse
plural: mice

It's good to know that the 7 button mouse can be configured correctly.
If it only requires installing "imwheel" and editing the Xorg.conf file, it should be possible to make a GUI for it (probably with PyGTK)(adding to the existing mouse config menu would make more sense) and put it into Gutsy (hopefully).

---

### Post by jimrz on 2007-06-02
> **KIAaze said:**
> singular: mouse
plural: mice

It's good to know that the 7 button mouse can be configured correctly.
If it only requires installing "imwheel" and editing the Xorg.conf file, it should be possible to make a GUI for it (probably with PyGTK)(adding to the existing mouse config menu would make more sense) and put it into Gutsy (hopefully).

thank you ;)

don't even need imwheel just
```

Section "InputDevice"
	Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
EndSection

```
in xorg.conf works for my IntelliMouse - 5 physical buttons (counts as 7 in xorg)

---


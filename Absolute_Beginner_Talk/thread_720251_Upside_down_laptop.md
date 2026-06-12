---
title: "Upside down laptop"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by BluePlum on 2008-03-10
So heres the pitch. I want to mounth MY laptop Upside on top of my desk so i can flip it down and watch movies. So basicly i have on board GPU and needa no how to make it so i can Flip the screen upside down and it'll be flipped everytime i start it up. This is possible in windows, Is it in ubuntu?

---

### Post by NightwishFan on 2008-03-10
I know there is settings somewhere that can do that. For me its like a nvidia control panel.

---

### Post by BluePlum on 2008-03-10
I dont have the nvidia control panel or any that i no of...

---

### Post by NightwishFan on 2008-03-10
If you have a nvidia card and restricted drivers its there somewhere i forgot where. At the moment I am of no use ill try to figure it out though. :KS

---

### Post by BluePlum on 2008-03-11
I HAVE AN ON BOARD GPU. it does not have a control panel i no about.

---

### Post by handydan918 on 2008-03-11
> **BluePlum said:**
> I HAVE AN ON BOARD GPU. it does not have a control panel i no about.
So? It could still be an nvidia...
Maybe if you post the output of lspci we can try to buy a clue for ya.

---

### Post by BluePlum on 2008-03-11
lspci? How i do that? Code?

And Im like nearly %100 sure it aint nvidia. Had it for ages. Dell Latitude d600..... if anyone wants to look up specs cause i dont no them :(

---

### Post by BluePlum on 2008-03-11
Anyones? yes i no im impatient :D

---

### Post by gobuntu on 2008-03-11
HI,

Rotate Screen is available at Preferences/Screen Resolution, but only if the hardware supports it, at least so it seems to be.

Typically, if in Windows you can rotate (and invert the screen) then you should be able to in Ubuntu, but probably NOT with enhanced effects enabled in "Appearances", perhaps.

Also, I don't think  that in Ubuntu the Rotation or Inversion remains in such a way that Ubuntu starts that way, you'd have to  go and choose rotation every time you turn pc ON.

I would like to know if it's possible, though, and how.

---

### Post by NightwishFan on 2008-03-11
I have an ONBOARD GRAPHICS CARD a well.  A nvidia geforce 6150se. I am sorry I assumed you were better informed and I did not wish to sound like I was patronizing you. Please just ask for more clarification. I really wish to help your problem, although it seems someone else has solved. I did not mean to complicate issues. Also I am running kde so it is a bit different for me to find a gui method.

---

### Post by BluePlum on 2008-03-11
> **NightwishFan said:**
> I have an ONBOARD GRAPHICS CARD a well.  A nvidia geforce 6150se. I am sorry I assumed you were better informed and I did not wish to sound like I was patronizing you. Please just ask for more clarification. I really wish to help your problem, although it seems someone else has solved. I did not mean to complicate issues. Also I am running kde so it is a bit different for me to find a gui method.

Dont be sorry just got lil angry soz. ill try the screen resolution thing in prefrenses. Do you no How to find out GPU? got laptop 3rd hand with no manual and it aint nvidia and im not sure.

---

### Post by jken146 on 2008-03-11
In a terminal: ```
lspci | grep VGA
``` should tell you what your graphics card is.

---

### Post by BluePlum on 2008-03-11
Wow.... i went into screen resolution and when i turn the screen upside down or left right it Just goes FLASH! then its my destop right way up but theres no Destop bar just icons and it doesnt respond anyway... Hmmm.. i waited like 3 mins and nothing happend so i restarted.... Theres always a problem when you over come one.

---

### Post by BluePlum on 2008-03-11
andrew@Andrew:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
 OOOO turns out i got an ATI... Told ya wasnt nvidia :P. Now all i needa no is why it freezes when i change it...

---

### Post by NightwishFan on 2008-03-11
I can think of a few reasons it might. One is it is not supported, and that seems likely. If you can, did you enable restricted drivers?

---

### Post by BluePlum on 2008-03-11
All effects work and i turned effects of before i did the thing and turned them on to try. and Effcts work... so probly supported. And it isnt in restricted drivers. Only some random thing was :P

---

### Post by NightwishFan on 2008-03-11
I would like to ask, have you rotated the display on Windows with this laptop?

---

### Post by BluePlum on 2008-03-11
No never tried. There two differnt OS so i dont think it would help. MAby in screen and graphics is there something i need to change?

---

### Post by NightwishFan on 2008-03-11
I wouldn't touch the screens and graphics without some help first. I was more seeing if it was a display issue or an OS/driver issue. I assume you just cannot rotate such a display. Try the search function for a similar thread perhaps, or wait for someone more knowledgeable to come. (I am still in the process of learning things as well and GNOME GUI isn't my strong suit.)

---

### Post by BluePlum on 2008-03-11
Searched but found nothing. Any smart people no? or no something that will flip the screen?

---

### Post by BluePlum on 2008-03-11
Help?

---

### Post by BluePlum on 2008-03-12
Anyone smart no how or whats wrong?

---

### Post by NightwishFan on 2008-03-12
edit

---

### Post by jordanmthomas on 2008-03-12
If you don't mind losing compiz (at least I have to since compiz does not respond), you can add this to 
system --> preferences --> sessions 
as a startup item:
```
xrandr -o inverted
```

This won't flip your screen until you log on, however.  
There should be a way to edit your /etc/X11/xorg.conf to use the randr module to do it as soon as X starts.  I am sleepy so I'll leave you to look it up, but it should be documented somewhere.

---

### Post by BluePlum on 2008-03-12
> **jordanmthomas said:**
> If you don't mind losing compiz (at least I have to since compiz does not respond), you can add this to 
system --> preferences --> sessions 
as a startup item:
```
xrandr -o inverted
```

This won't flip your screen until you log on, however.  
There should be a way to edit your /etc/X11/xorg.conf to use the randr module to do it as soon as X starts.  I am sleepy so I'll leave you to look it up, but it should be documented somewhere.

I did that then it went black and froze :( then when forced it to shutdown and turned on i logged in and Nothen... right way up :(

---

### Post by NightwishFan on 2008-03-12
Must not be compatible then. Sorry mate. :(

I keep my eyes open but I am on Kubuntu so its different.

---

### Post by BluePlum on 2008-03-12
> **NightwishFan said:**
> Must not be compatible then. Sorry mate. :(

I keep my eyes open but I am on Kubuntu so its different.

Thx nightwishfan uve been rly helpful thru whole thread. Heard of any programs that can do it? My GPU obviously isnt copatable with the ubuntu effect. All tho it can do cube and all that fine doesnt make much sence that it just cant display differnt angle....

---

### Post by gobuntu on 2008-03-12
> **BluePlum said:**
> Wow.... i went into screen resolution and when i turn the screen upside down or left right it Just goes FLASH! then its my destop right way up but theres no Destop bar just icons and it doesnt respond anyway... Hmmm.. i waited like 3 mins and nothing happend so i restarted.... Theres always a problem when you over come one.

Hi BluePlum

Go to System/Preferences/Appearances/Visual Effects

and in there click NONE (No visual effects, simple graphical environment).

Then (via Screen Resolution, etc.), your screen should hopefully rotate and not freeze as you say.

Hope that should do it.

---

### Post by NightwishFan on 2008-03-12
I will look now. I believe a screen rotation is something like how even though I have a common newer Nvidia, OpenSUSE assured me my max resolution was 1280x1024 or something. It is more like an actual display change than a compositor.

EDIT: What was said above might work actually. It might just be a compiz bug.

---

### Post by BluePlum on 2008-03-12
O does that mean my dream of having my laptop flip down is over..... :(

---

### Post by NightwishFan on 2008-03-12
I could not find any programs, however it is a bug on launchpad and it seems to perhaps be Compiz related. If it doesn't work on None effects, than you might not be able to use this until perhaps hardy is released.

---

### Post by BluePlum on 2008-03-12
AAAHHH an ubuntu bug..... Grrr'sss lol. Can we tell them to fix it asap somehow? heh's

---

### Post by prshah on 2008-03-12
> **BluePlum said:**
> lspci? How i do that? Code?

And Im like nearly %100 sure it aint nvidia. Had it for ages. Dell Latitude d600..... if anyone wants to look up specs cause i dont no them :(

It's ATI.

After completing ATI setup and installation, open a terminal and use the ```
sudo xrandr -o inverted 
``` command.

Note that if you have the VESA driver, this will not work.

To check for VESA: the command  ```
cat /etc/X11/xorg.conf | grep -i vesa
``` should be blank if you are not using VESA.

Cheers,
PRShah

---

### Post by BluePlum on 2008-03-12
> **prshah said:**
> It's ATI.

After completing ATI setup and installation, open a terminal and use the ```
sudo xrandr -o inverted 
``` command.

Note that if you have the VESA driver, this will not work.

To check for VESA: the command  ```
cat /etc/X11/xorg.conf | grep -i vesa
``` should be blank if you are not using VESA.

Cheers,
PRShah

I think u missed half the thread.

---

### Post by prshah on 2008-03-12
> **BluePlum said:**
> I think u missed half the thread.

Yes, it took me too long to type... but I think you have a VESA problem; do you think you need to check or are you sure that's not it?

Cheers,
PRShah

---

### Post by BluePlum on 2008-03-12
> **prshah said:**
> Yes, it took me too long to type... but I think you have a VESA problem; do you think you need to check or are you sure that's not it?

Cheers,
PRShah

VESA?

---

### Post by BluePlum on 2008-03-12
? :confused: ?

---

### Post by jordanmthomas on 2008-03-13
You've never said whether or not xrandr works right if you disable compiz first.
Does it?

---

### Post by prshah on 2008-03-13
> **BluePlum said:**
> VESA?

To check for VESA: the command
Code:

cat /etc/X11/xorg.conf | grep -i vesa

should be blank if you are not using VESA.

VESA is the default driver which is put in if the actual ATI (or nv or intel or sis or whatever) driver cannot be loaded.

---

### Post by BluePlum on 2008-03-13
> **jordanmthomas said:**
> You've never said whether or not xrandr works right if you disable compiz first.
Does it?

If you read the thread extre carefully you would of seen that it doesnt work with compiz diabled :P not being mean i meant that in a joking fasion

---

### Post by BluePlum on 2008-03-13
Yeah it was blank

assasin@Invisible-Assasin:~$ cat /etc/X11/xorg.conf | grep -i vesa
assasin@Invisible-Assasin:~$ 

And ive never updated my ATI GPU or any drivers because i dont no how. And i just Reformatted and reinstalled ubuntu and it didnt work :P

---

### Post by jordanmthomas on 2008-03-13
> **BluePlum said:**
> If you read the thread extre carefully you would of seen that it doesnt work with compiz diabled :P not being mean i meant that in a joking fasion
OK, I can't find that part of the thread, but I believe you I guess.

---

### Post by jordanmthomas on 2008-03-13
OK I just looked about on the internet and found that xrandr will only work with the open-source driver.  Are you using the ati / radeon driver or are you using flgrx?
```
grep Driver /etc/X11/xorg.conf
```

If you're using fglrx you'll have to switch to the "ati" driver.

---

### Post by BluePlum on 2008-03-13
DONT NO but im preety sure its ati radeon

---

### Post by BluePlum on 2008-03-13
Ok i tried with compiz off again to be 100% sure. When i enerd it nothing happend then i enterd it again and again then this came uo 10th time

assasin@Invisible-Assasin:~$ sudo xrandr -o inverted
sudo: timestamp too far in the future: Mar 14 02:37:19 2008
assasin@Invisible-Assasin:~$ 

Have i Broken ubuntu al rdy :(

---

### Post by jordanmthomas on 2008-03-13
1.  You don't need sudo
2.  To fix your (unrelated) sudo problem, 
```
sudo -K
```
Then you'll be able to use sudo again.

Instead of you maybe locking up X, what do you get if you type this?
```
xrandr -q
```

Mine gives me something like this:
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected ([COLOR="Red"]normal left inverted right [/COLOR]x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
```

The parts that say left, inverted, and right mean that rotation is possible.  If you don't have them your driver may not support it.

---

### Post by BluePlum on 2008-03-13
thx for helping realy appreciate it :D

assasin@Invisible-Assasin:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right)
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

And u fixed my sudo :D

---

### Post by jordanmthomas on 2008-03-13
Well, xrandr should work according to this I think, although it's odd that it can't find the physical size of your monitor.
If you're sure you've tried it with desktop effects (compiz) turned OFF and it still doesn't work then I believe you have found a bug.

---

### Post by BluePlum on 2008-03-13
The screen defaultly selected is Plug 'n' Play. Maby if i change this?  and other info 1024x768 reso and 60hz :P

---

### Post by BluePlum on 2008-03-13
Been an hour :P

---

### Post by BluePlum on 2008-03-13
2 hours......

---

### Post by jordanmthomas on 2008-03-13
Sorry, I don't live on the forums, had other things to do, and don't know what to do from here.

---

### Post by BluePlum on 2008-03-13
> **jordanmthomas said:**
> Sorry, I don't live on the forums, had other things to do, and don't know what to do from here.

Yeah soz got bored sick 2day nothen 2 do... So if i change the screen from plug 'n' play to somethen will that help? And ill update ubuntu see if that helps, Just reinatlled... Dont think it will cause tried yesterday with Updated ubuntu. Is there any way to update ATI gpu>

---

### Post by BluePlum on 2008-03-14
Bump! :D:KS

---

### Post by BluePlum on 2008-03-16
been2 days so bump!

---

### Post by BluePlum on 2008-03-16
So if i change the screen from plug 'n' play to somethen will that help? And ill update ubuntu see if that helps, Just reinatlled... Dont think it will cause tried yesterday with Updated ubuntu. Is there any way to update ATI/radeon gpu?

---


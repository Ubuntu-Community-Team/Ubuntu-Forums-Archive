---
title: "IAA (Installation Adicts Anonymous)"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Lightsman on 2007-02-02
Hi, (clears throat) my name is Lightsman and I've been trying to install Linux for three days now. (Not a consecutive 72 hours cause I had to go to work. :(~ My kids have bad habits like . . . um . . . eating.)I just want to have my breakthrough. You know like many others around here have when they finally get to see something other than black screens with white text and error codes. Oh the days of DOS. I am becoming sudo-literate though in the process. Pun shamefully intended.

So heres what we're dealing with: 
Pavilion Pentium 4
1G ram
2.6 GHZ
80G master
120G slave (partitioned for the uberbootoo)
intel integrated graphics blah blah (disabled)
Nvidia GeForce 5200FX w/256mb ram (currently unrecognized by either ubunto or Kubuntu)
G15 usb keyboard (hasn't presented a problem)
Huh, oh yeah Windows XP (Shameful I know.)

Going for dual boot if it wasn't obvious.

Tried live cd first, no dice, couldn't get driver loaded to recognize Nvidia. Searched forums for Nvidia specific topics and the cup runneth over! Makes me wish I'd bought ATI instead, but I got a good deal plus Ubuntu is free so its worth trying. Now I've got Kubunto alternate cd and I'm having the very same problem others have had, but no breakthrough. No desktop. No graphics and I've got a notepad full of code suggested by other ubunto veterans passed of to fellow noobs. I wish to shed my noobishness.

Live cd:
Observation of note: Xserver either does not run or does not recognize Nvidia because the driver for Intel seems to be dominant. Everytime I run:
 ```
sudo dpkg-reconfigure xserver-xorg
``` 
The intel driver is there. I get denied acess when I try:
```
/etc/X11/xorg.conf
```
Probably writing it wrong- sudo or not to sudo?
```
gksudo gedit
```
This code of any type produces nada. Even tried:
```
wget http://us.download.nvidia.com/XFree86/1.0-9746/Nvidia-Linux-x86-1.0-9746-pkd1.run
```
This returned a ERROR 404 with other information on a black screen with WHITE letters!Ofcourse I had planned to run the rest of the code found in the post but got stopped dead in my tracks. So I saw suggestions pointing toward using the alternate cd and that is how I ended up with Kubunto which has produced slightly better results, but no finished product, and I really only got as far as I did on ubunto live cd and began learning a different dialect. Kthis and Kthat. Whew!
So this is where I am now: Either uninstall and start all over (not my first choice), or watch the sun come up and get my breakthrough! Hey, how often do we have these meetings anyway? I lost my twelve step card!
(If this is too long I'm sorry.)

Nervous Noob

---

### Post by kerry_s on 2007-02-02
Hi, my name is kerry and yes i am a addict. I can't help my self i install and uninstall just for the hell of it....

Anyways, thats start from the beginning. How far have you got? You say you got the alternate cd , did that install? If so try this->

login
sudo su
apt-get update
apt-get install nvidia-glx

Then 

nano /etc/X11/xorg.conf

change
    Driver         "vesa"
to
    Driver         "nvidia"

press ctrl and x and y and enter to save
type> reboot

---

### Post by Lightsman on 2007-02-02
Hi Kerry! No two installs are alike right? Ok, seeing something different now, but still not quite there. Fast scrolling screen is a good sign right? That was exciting, but I need another fix . . . literally.  
'nano etc/X11/xorg.conf' now produces something. Didn't now about the "nano" all the post I read must have assumed the reader would know. Driver held the 'nvidia' also. Ran it again to check, but it wasn't vesa it was vga if that makes any difference at this point?
'dpkg-reconfigure' still pumpin' the same thing, Intel hell.
Really appreciate the help. Fellow install junkies remember: "Fake it 'till you make it."

---

### Post by Lightsman on 2007-02-03
Breakthrough!! I got it! I got it! I'm free!!! Oh . . . wait, hmm gotta get sound working, can't find hard drive, and whats the equivalent of windows explorer? More reading. OK I can do that. At least it works!! I can feel the cloak of noobiness getting lighter. Time to pick some brains.
Hey how about wallpaper? Can I decorate my new pad? Thanks Kerry! Talk about a one hit wonder! Sharpshooter!

I'll be back hehe.

---

### Post by kerry_s on 2007-02-03
Nah, i had a headache, had to take a break/nap. I was googling your card before i took a nap and it seems theres a lot of problems with that card and linux. I'm glad you made some progress, so are you saying you got a picture? "Explorer" in gnome it's nautilus, in kde it's konqueror, in xfce it's thunar.

---

### Post by r4ik on 2007-02-03
> **Lightsman said:**
> Breakthrough!! I got it! I got it! I'm free!!! Oh . . . wait, hmm gotta get sound working, can't find hard drive, and whats the equivalent of windows explorer? More reading. OK I can do that. At least it works!! I can feel the cloak of noobiness getting lighter. Time to pick some brains.
Hey how about wallpaper? Can I decorate my new pad? Thanks Kerry! Talk about a one hit wonder! Sharpshooter!

I'll be back hehe.

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

---

### Post by riven0 on 2007-02-03
[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+thread")

:mrgreen:


EDIT: Hey, r4ik got to it before me!

---

### Post by Lightsman on 2007-02-03
Yup got in and surfing. I went back into 'nano /etc' and changed both lines that referenced Intel to Nvidia then pulled yet another 'sudo dpkg-reconfigure' and pop there it was up and running.

---


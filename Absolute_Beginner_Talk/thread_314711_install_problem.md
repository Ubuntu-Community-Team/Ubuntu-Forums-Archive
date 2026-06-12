---
title: "install problem"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by EldBowman on 2006-12-08
I have installed Unbuntu on a gateway computer. Full system erase ans instal. The Instalation goes okay (a little slow). During the reboot the system goes through all the checks and at the point the it is to launch Unbuntu the system freezes.  
The computer has a 40gb drive. 

What can a beginner do to solve this issue.

Thanks

Rick

---

### Post by K.Mandla on 2006-12-08
Can you tell us more about your computer? It might be something unique to the guts of your machine. What's the model number?

---

### Post by EldBowman on 2006-12-08
it is a gateway micro atx san pro v800. It had windows xp installed over win '98.  I used both the live cd and the alt cd to install.  Neither worked.

:confused:

---

### Post by houstonbofh on 2006-12-08
> **EldBowman said:**
> it is a gateway micro atx san pro v800. It had windows xp installed over win '98.  I used both the live cd and the alt cd to install.  Neither worked.

Does it have a CPU, memory or a video card? ;)

Now, after install does it reboot?  If so, how far does it get?  Do you see the Logo, and a lot of text?  What is the last OK you get...  In other words, we need a lot more detail.

---

### Post by K.Mandla on 2006-12-08
Let's see ... unless I'm mistaken, that's a 800Mhz Celeron machine with onboard i810 graphics. 

Are you using an additional video card, or are you just using the graphics on the motherboard?

Do you know how much memory is in your computer?

Can you tell us what happens when it freezes? Do you get any error messages? Does it reach the desktop at all?

---

### Post by EldBowman on 2006-12-09
You are correct, 800Mhz using video card not on the board. I was able to install completly. It will boot and load all the way upto where it seems like it will goto desk top and it freezes. The only thing on the screen is - or cursor up in the upper left hand corner of hte screen that will flash and then go steady.  

:-k

---

### Post by houstonbofh on 2006-12-10
> **EldBowman said:**
> You are correct, 800Mhz using video card not on the board. I was able to install completly. It will boot and load all the way upto where it seems like it will goto desk top and it freezes. The only thing on the screen is - or cursor up in the upper left hand corner of hte screen that will flash and then go steady.  

:-k
Is there some reason you do not what to tell us what you have?

#1 What video card.  Exactly.  Brand and model.

#1 How far does it go?  Does it pass GRUB?  Do you ever see the logo splash?  Can it boot into recovery mode?  Can you list your xorg configuration file?

---

### Post by EldBowman on 2006-12-10
I do not know what kind of video card it has it it not my computer. The splash screen does come up. I am new to linux. I think I see the logo splash and it will go through all the check and as I said before it will lock up just before it goes to the desktop.

---

### Post by houstonbofh on 2006-12-10
> **EldBowman said:**
> I do not know what kind of video card it has it it not my computer. The splash screen does come up. I am new to linux. I think I see the logo splash and it will go through all the check and as I said before it will lock up just before it goes to the desktop.
The problem is that Ubuntu doesn't know what kind of video card you have either.  My guess is that Xwindows is hanging on graphics init.  To get past this, you will have to help us.  First, **watch the next boot for the grub menu.  Choose Recovery.**  If you can get to a command line, we can help a lot.  If this is beyond you, we can not help at all.  (If it just doesn't work, there are some ways around it, however)  You will also **need to know what your graphics card is!**  Open the case and look if you have to, but without that, we are again dead in the water.

---

### Post by wpshooter on 2006-12-10
Bowman:

If you are not going to be installing any other O/Ss on this computer I would try this:

Make sure you are checking the integrity of both of your install CDs by running the verification test that is found on the initial Ubunut boot screen menu.

Get the **KILLDISK** program and **WIPE** your hard drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then I would first try to do the install again first using the DESKTOP CD with just the standard install.

If that still gives your problems you may want to install with the DESKTOP CD using the safe video mode parameter.

If that does not help you may then want to KILLDISK the hard drive again and then try installing from the ALTERNATE CD.

Make sure that when you are feeding the install the various parameters that it ask you to answer that you are allowing your CD drive to spin down completely between getting the prompt and answering it.

Also when you get the parameter regarding the language type, make sure that you click on the test box at the bottom of the screen (you don't have to type anything into it - just click on it) and the click back onto the language parameter, before proceeding.

Write back if you need more help.

Good luck.

---

### Post by lyceum on 2006-12-10
Just a quick observation encase you are still havening troubles. 

You may want to try using Xubuntu, as the PC sounds really old. I have found that you can install Xubuntu, then drop Gnome on it if you like it better and it is faster on older PCs. 

Good luck!

---

### Post by wpshooter on 2006-12-10
P.S. - 

Make sure you are checking the integrity of the memory on your computer by running memtest on it.

By the way how much memory does you computer have ?

If it is less than 256mb you may want to consider Xubuntu like lyceum said.

---

### Post by ardvark71 on 2006-12-10
> **houstonbofh said:**
> The problem is that Ubuntu doesn't know what kind of video card you have either.  My guess is that Xwindows is hanging on graphics init.  To get past this, you will have to help us.  First, **watch the next boot for the grub menu.  Choose Recovery.**  If you can get to a command line, we can help a lot.  If this is beyond you, we can not help at all.  (If it just doesn't work, there are some ways around it, however)  You will also **need to know what your graphics card is!**  Open the case and look if you have to, but without that, we are again dead in the water.

I agree with houstonbofh on this 100%. If the video card or onboard chip doesn't give you the exact name, then give us the numbers off the chip, if possible, and we can go from there. 

I've had the same thing happen with other, older distros so I know what a pain it is. :( 

Best Regards...

:KS

---

### Post by EldBowman on 2006-12-20
I WILL TRY WHAT YOU HAVE SUGGESTED.  I HAVE NOT HAD ALOT OF TIME TO DEAL WITH IT BUT i WILL HAVE SOME TIME AFTER CHRISTMAS.  

THANKS

---

### Post by EldBowman on 2007-01-02
The video card that is installed on this computer is a "(2001) ATI Radeon Craphics" Card.

(S/N 160247 001882  RADEON 7000 64MDDR)
(P/N 1028551000 068453)

---

### Post by houstonbofh on 2007-01-05
OK.  You have an ATI RADEON 7000, which is an older rv100 card.  I would start with [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and let us know if you still have problems.

---


---
title: "Screen Res problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by DeuceII on 2007-06-09
Hi again,

Since my last problem was resolved this morning, I now have another.

You may recall that I have a dual boot 'spare' system, well after sorting this mornings little prob, I had to go off do some other stuff.  I have just booted the 'spare' into feisty and my screen res will not go above 640x480.  Been into the res settings and all that I can select is 640x480!

XP boots to my native (tft) 1280x1024, which my feisty insatl did until this boot.  I have reboot a number of times but still no joy.

I reiterate,  I have been into res settings and all I have is 640x480. 

So I have a 2 fold question...

a) what has happened? (I like to understand where poss)
b)How to correct?

This is my graphics as described by Belarc Advisor -   	Intel(R) 82865G Graphics Controller [Display adapter]
I am running a 2.8  'Northwood' clocked at 3.4 with Ram that can handle the increase in FSB without complaning. Setting back to stock makes no difference.

I had no issues with my display prior to the instructions I followed in my earlier thread.

Any help is welcomed...

Peace to All

DeuceII

---

### Post by diatribe on 2007-06-09
I dont know what might have broken it without looking at your prior post, post you can add resolution settings to your /etc/X11/xorg.conf file, and that should fix your problem

---

### Post by DeuceII on 2007-06-09
> **diatribe said:**
> I dont know what might have broken it without looking at your prior post, post you can add resolution settings to your /etc/X11/xorg.conf file, and that should fix your problem

Thank you for your time.

I, as a complete beginer do not know how to do what you have suggested, although I thank you for your input.  Would you please explain how to do what you have suggested?

Peace to you and yours

DeuceII

---

### Post by BatsotO on 2007-06-09
My first tip will be : search the forum for information, this forums have a long line of history so when not all, most of the problem have already been answered.

The second, try this on terminal : sudo dpkg-reconfigure -phigh xserver-xorg and then reboot, or juat press ctrl-alt-backspace.

I hope this help

---

### Post by diatribe on 2007-06-09
ok from a terminal, type sudo gedit /etc/X11/xorg.conf

like halfway down the file you will see default depths and resolutions, add 1280x1024 to all the reolution lines and save the file, then hit ctrl-alt-backspace

---

### Post by DeuceII on 2007-06-09
Hi folks,

thanks for the above, I did read through loads of threads but none seemed to have an answer.

I tried typing in what you said but all I get is command not found!

I can't understand what has happened, how Fiesty has lost settings it had just 12 hours ago, with the PC off..

thanks again, and if you have any more ideas I'm all ears (eyes...lol)

DeuceII

Edit: After entering the commands in Terminal and getting as posted above, I decided to reboot anyway and my Res is back to what it should be.

I would like to know what has happened, so that I can understand, any one like to explain?

DeuceII

---


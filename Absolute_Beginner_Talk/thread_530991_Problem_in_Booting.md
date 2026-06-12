---
title: "Problem in Booting"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by The Omani on 2007-08-21
Hi,

I am a new user to Ubuntu OS, I am trying to install Ubuntu OS along side with my existing Windows XP. My first step was to boot from the CD, while Ubuntu CD is in. After getting the menu and clicking on install Ubuntu, I get the Ubuntu logo with a loading bar that goes left and right. After a minute or two the screen goes black. Leaving it for more than 7 hours did not come with anything. I tried to repeat the whole thing but I keep getting the same result.

Your help is greatly appreciated! 

Thanks a lot :-)

---

### Post by bdsatish on 2007-08-21
Wat's ur comp's config?

If u r running from LiveCD and u've 256 MB RAM (or less), u mite face some probs...

The same happnd wit me.. Comp hangs after clicking "install" icon..

---

### Post by TeaSwigger on 2007-08-21
> **The Omani said:**
> Hi,

I am a new user to Ubuntu OS, I am trying to install Ubuntu OS along side with my existing Windows XP. My first step was to boot from the CD, while Ubuntu CD is in. After getting the menu and clicking on install Ubuntu, I get the Ubuntu logo with a loading bar that goes left and right. After a minute or two the screen goes black. Leaving it for more than 7 hours did not come with anything. I tried to repeat the whole thing but I keep getting the same result.

Your help is greatly appreciated! 

Thanks a lot :-)

Hello,

This may be caused by too little memory (256mb is borderline) or a problem with graphics. You may not be able to use the 'Live CD'. You can still install ubuntu (or Kubuntu or Xubuntu variations) from the 'Alternative CD' because the 'Alternative CD' version uses less memory and has no fancy graphics until it is installed. Once installed it should be able to work with whatever the graphics situation is and run okay on 256mb or more of memory. If you have less than 256mb memory, you may want to find the guides for special installations on low memory systems. It is still easy to install ubuntu from the 'Alternative CD'.

---

### Post by The Omani on 2007-08-21
Thanks for the guys...

Actually my memory is 1gig so I dont think this is the issue!

---

### Post by TeaSwigger on 2007-08-21
Could be something to do with graphics or sound card then, causing it to 'hang'; but I'm not knowledgeable on either front. Sorry I can't help you beyond that.

---

### Post by The Omani on 2007-08-22
My graphics is 256 MB !!!

Guys can someone help

---

### Post by TeaSwigger on 2007-08-22
I'll try... you need to be a lot more specific.

Let's understand this right: You have a computer with a 256mb video card and one hard drive. You already have Windows XP installed. You downloaded Ubuntu 7.04 Live CD and burnt it on a CD. You successfully booted to the Live CD, which ran successfully. You clicked on the install button and you went through the install steps, right? Location, keyboard layout, created an account, blah blah. After this, ubuntu told you to restart, remove the CD. You restarted, removed the CD when prompted. It fails to load when you try to boot, being stuck on the loading screen (that screen is called the usplash). If this is right please reply with the following:

- The rest of the info about your computer. PC or laptop? Processor, memory, size of hard drive, make and model of video and audio cards, accessories.

- The choices you made during installation with regard to the partitioning; did you set it up "dual boot" and do you see the screen offering you a choice of which system to boot when you start or restart the computer?

- If you chose a dual boot, does Windows still boot and run ok?

Please reply and we'll try to fix this.

---

### Post by The Omani on 2007-08-24
Hey,

thanks for ur reply...

My computer is 100gig with 2 partition hard disk, Dell Inspiron...

The graphics card is 256 mb and ram is 1 gig...

I have windows XP now and wish to have Ubuntu on top of it...

The Ubuntu did not even start the live CD, which mean that booting was not successful...

After booting and starting the live CD, before the Desktop apears the screen turns black...

Tryed waiting long, but no use :(

---

### Post by The Omani on 2007-08-25
Help please!

---

### Post by nvteighen on 2007-08-25
Maybe your CD is corrupted (badly burnt). Do the following:
1. Boot with the Live CD
2. Select "Check CD for defects"

This can happen when you burn the CD too fast. Always use the lowest speed available to create a  Live CD.

---

### Post by The Omani on 2007-08-25
cd is fine, i got it from Ubuntu but I checked it as well, its fine!

---

### Post by The Omani on 2007-08-26
By the way I tried the same CD on my friends computer and it worked, I dont know whats wrong with mine?!?!

---

### Post by nvteighen on 2007-08-26
Well, strange. I only have two more reasons:

1. That you didn't download the image matching with your computer. What file did you download (i386, amd64, etc.) and what processor do you have (Centrino Duo, a Mac, AMD Turion 64, etc.)?

2. That your video card is responsible. What is yours? NVidia cards may be conflictive, sometimes.

---

### Post by The Omani on 2007-08-26
both problems do not exsist...

duel prossesor and i got the i386 copy...

and my video card is not nvidia!!!

---

### Post by tistria on 2007-08-26
ATI video cards are notorious for being a pain to set up under Linux.  It could be that if you have an ATI card, the live CD won't load GNOME (it sounds like that's what's happening).  I've never heard of this happening before, but stranger things have happened.  Does your mobo have on-board video?  If so, try taking out your video card and plugging your monitor into the on-board video directly.  Then try booting to the CD again.  If that works, it's your video card.  If not, I'm sure someone else has a solution.

---

### Post by The Omani on 2007-08-27
Actually its a laptop! But I dont think its a graphical problem, my freind has the same graphics and had the OS working

---

### Post by The Omani on 2007-08-28
anybody?!:confused:

---

### Post by Marat Galiev on 2007-08-28
OK,you have boot in "safe graphical mode"?
This is right way for you.
If this doesn't help,press F1...F2 in boot screen,and  boot with different kernel parameters.

---


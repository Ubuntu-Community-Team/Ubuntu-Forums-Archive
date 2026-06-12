---
title: "Do dual operating partitions cause problems???"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by mkadin on 2007-08-16
I have Ubuntu on my hard drive on a partition; the other partition is WinXP.  I am hoping to keep both of them on computer if possible.  I have heard you can have problems with dual systems is this true?  The only problem right now is that Ubuntu is on #1 to be booted up instead of Windows, I would prefer it the other way around as I have two bible programs that I use alot and only for Windows I believe and so I need to keep windows for those.  I am very new to this but what is Macintosh?  I have seen where questions are ask if you have Windows or Macintosh.  Should I see if Ubuntu will take my bible program?  I tried something once and it froze up the program and I had to reboot.  Anyone have any answers for me?  Also if need be how do I uninstall Ubuntu off of my desktop?:confused:

---

### Post by demonicdude on 2007-08-16
Well, for me, the only time i had problems with dual booter was with version 6.06 of Ubuntu, and basically all it did was give me a blue screen saying error hard disk, but i ignored it and nothing happened :P. Righ tnow, i'm with feisty and everything is running ok. Just make sure the dual-boot is perfectly fine and you dont mess around with anything *major[*.

Macintosh, i believe, is Mac? Apple's OS system, like microsoft is windows, and ubuntu is linux.. [http://www.apple.com/dotmac/](http://www.apple.com/dotmac/) more info on that if u like

Now i'm going to be assuming you have Grub loader? When you load your computer, it goes to a menu with options for picking either ubuntu or windows? And your annoyed cause it is set onto ubuntu and you have to move down to windows? IF this is the case, do this:

in the terminal (you can acess this by going to applications -->accessories --> terminal>
type this in:
sudo gedit /boot/grub/menu.lst

When you type sudo in, your basically becoming the "big-adminstrator" of the computer. This is the only way you can edit the file.

This file is the configuration file of Grub's menu, here you can select different stuff like changing the colors, adding a background to the grub loader, and changing the default selection. Now, this step might seem a bit confusing, but it shouldn't be :P.

Scroll down to where it says "## ## End Default Options ##" You should see on the left hand side the word "title" a few times. First, find which one of the "titles" corresponds with your Windows, shouldn't be that hard to find, and it should be the last one i'm guessing. Ok, once you found that, i need you to go back to the start of End Default options, and start counting the word "title". START COUNTING AT 0, the first "title" you should see corresponds (or at least for me) with this "Ubuntu, kernel 2.6.20-16-generic" that "title" is 0 for me, Now i keep on counting the titles, until i finally finish with the windows one. That "title" for me is number 6. Remember your number.

Second, very easy step compared to how i made the last one seem like >.>... at the top, there should be ##default num, If you see that, good,  There will be 6 more lines with the "#" sign in front of them and then the next line says Default    "number". First of all, the # signs in front of the lines just tells linux not to do anything with that, It is basically refrence for other people who want to look at the code of a program or such and bla bla bla.. Ok anyways, Whatever number you counted for your Windows i want you to put it as this:

"Default           *your number*, so basically replace the number there with whatever you counted. 

Dont panic if you miscounted or anything like that, If you didnt touch any other part of the editor, you should be fine if you miscounted lol. All this does is set the default option to be windows, so next time you start your computer, instead of it being on Ubuntu, It'll be on Windows =). 

Also, if you want, you can change the timer on the grub menu loader. So instead of you haveing 10 seconds to pick something, you can make it 2 *remember if you move the arrows it will stop the timer completly and you'll ahve a lot of time lol*. But never make it 0! never!, if you want me to tell you how to do this, just reply :P.


I hope this helps, and if this wasn't your question, then i just wasted 10 minutes of my life =D

---

### Post by ugm6hr on 2007-08-16
> **mkadin said:**
> I have heard you can have problems with dual systems is this true? 

demonicdude has answered the boot default question in a lot of detail, so I'll leave that.

As for problems dual-booting, I think it is recommended that you do not use the hibernate function in either Operating System (OS), since if you hibernate in one, and then boot the other when you next turn on, it can sometimes cause problems when you return to the previously hibernated OS.  Other than that, the 2 OSes do not interact with each other at all.

If you start a fresh thread with details of the 2 bible programs you need - someone might help you try to install them in Ubuntu...  I believe there is a Christian-focused version of Ubuntu with their own forum that might be of interest to you: [http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html)

---

### Post by hyper_ch on 2007-08-16
and it may be quite possible those windows program can be made run with WINE.

---


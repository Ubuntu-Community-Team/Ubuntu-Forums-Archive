---
title: "Graphics dont let me Boot and im so newbie"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by gavos on 2007-11-01
Hello.. I have an Nvidia mx420 and it doesnt let me boot the Feisties.. Everyone is telling me to find and install some drivers but i cannot do either, because they speak like i know things in command line.. Mention that i can only access ubuntu from recovery mode and that i wont have an internet connection.. What can i do please help!!!   :confused:

---

### Post by Pumalite on 2007-11-01
Try Alternate CD.

---

### Post by pacsum on 2007-11-01
Try with Gutsy.

---

### Post by gavos on 2007-11-01
> **pacsum said:**
> Try with Gutsy.

Do you think this will fix these things? How can i write gutsy over feisty!!!

---

### Post by gavos on 2007-11-01
> **Pumalite said:**
> Try Alternate CD.

Is there a possibility that the CD has a problem even if the installation process completed succesfully?? And even if in another computer the same CD worked fine?? Note i ordered the CD from the official site of ubuntu..

---

### Post by Pumalite on 2007-11-01
I think the Gutsy suggestion is better.

---

### Post by meanburrito920 on 2007-11-01
Can you specifically tell us what the error is, if any, or what actually happens when it doesnt worK. did the install process work? will the CD not even boot for installation? please be more specific.

---

### Post by gavos on 2007-11-01
The whole installation process is ok.. When comes the time for the feisties to boot for the first time the progress bar with the ubuntu logo stacks at the end (at the last box), after a minute or two the progress bar fills and i see a cursor like in command prompt (in a black screen) blinkering for 15 secs and then the screen makes 4 jumps between black and sleep and after 15 secs i see the pointer of mouse that is like a black X and not a pointer.. After 30 secs it becomes a real mouse pointer, the brown backround of ubuntu comes in and if i wait about 15 minutes i will be promted for the password.. But you can feel the system slowness from the mouse pointer that has 1 frame per second refresh rate.. Its ugly!!!
No errors..
Any ideas please!!

---

### Post by Pumalite on 2007-11-01
Memory?

---

### Post by gavos on 2007-11-01
Ok.. 768mb..

---

### Post by gavos on 2007-11-02
Any ideas???????????

---

### Post by Pumalite on 2007-11-02
How far did you get in the installation with the Alternate CD?

---

### Post by gavos on 2007-11-02
What is Alternate CD?

---

### Post by gavos on 2007-11-06
Really theres nobody to help me out there?????
Or my problem is too heavy!!!
Help me i cant stand windows anymore!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Pumalite on 2007-11-06
If you have integrated graphics, they are eating up your RAM and maybe the system is too heavy for you. Or your graphics demand that you install with the Alternate CD. We need your graphics?

---

### Post by OldTimeTech on 2007-11-06
Let's back up a minute.....

Are you running a laptop or a desktop....because the Nvidia mx420 is a graphics card not a type of machine.

So then we need to know the type of cpu, speed and with 768mbs of memory...you should (should being the keyword) be able to run feisty and/or gutsy....but you have something that is really eating away at your RAM/memory.

By the way, an Alternate CD is the installation CD that is run on text for loading instead of a GUI.

---

### Post by gavos on 2007-11-06
I have an Intel pentium 4 1.5 ghz.. Its a desktop.. Is that enough?

I tried to search in the forums and what i found has to do with programs that do the job automatically like envy.. I dont know maybe i didnt understand.. The problem with me is that i have no internet connection confiured (ethernet card) cause i have to boot succesfully in order to configure my connection.. I tried sudo dpkg-reconfigure xserver-xorg and then sudo startx and everything loaded succesfully, but i had no rights on the machine nd it wouldnt let me configure an internet connection.. Then tried to reboot normally but it was the same disaster that i explained at the first posts..

---

### Post by Pumalite on 2007-11-06
If you are running Windows; isn't there a way to see all the hardware in you computer?

---

### Post by gavos on 2007-11-06
> **Pumalite said:**
> If you are running Windows; isn't there a way to see all the hardware in you computer?

Of course.. Tell me what you need to know and i will tell you..

---

### Post by gavos on 2007-11-07
Anyone?

---

### Post by mike555 on 2007-11-07
The way I understand it , you ran the "live" CD and it worked , then you installed Ubuntu and it wont work?   it seems to me that it should have, but like others have said , I would recommend downloading the newest alt. CD , burning it as slow as you can and installing again from it ........ if that doesn't work it's probably your graphics card , I had to use "Envy" to get my 5200 to work , you will probably need to install it from the command line ..........  your internet should be configured during the install if your using Ethernet ( you should have been asked during the install) ........if you have any more questions , you should list your computers components ...

---

### Post by Pumalite on 2007-11-07
> **gavos said:**
> Of course.. Tell me what you need to know and i will tell you..

Graphics, please?

---

### Post by gavos on 2007-11-07
> **Pumalite said:**
> Graphics, please?

Soryy i thought that i mentined my graphic card.. Its an Nvidia mx420..

---

### Post by Pumalite on 2007-11-07
Use the Alternate CD. Download new iso, do md5sum on it, burn at 4x, burn as Image.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by jimod4 on 2007-11-07
why don't you boot with the live cd.  Then copy the file /etc/X11/xorg.conf to a floppy.  then boot into the installation that does not work.  select recovery mode from the grub menu.  copy the xorg.cong file back to the hard drive.  then type startx.  enjoy free software.

---

### Post by gavos on 2007-11-07
> **jimod4 said:**
> why don't you boot with the live cd.  Then copy the file /etc/X11/xorg.conf to a floppy.  then boot into the installation that does not work.  select recovery mode from the grub menu.  copy the xorg.cong file back to the hard drive.  then type startx.  enjoy free software.

This will fix my problem permanently?
Cause i tried configuring that file from recovery mode and then startx (ubuntu started normally but i had no rights to do anything at all) but when it comes the time to boot normally again ubuntu doesnt boot like i described before..

---

### Post by gavos on 2007-11-07
> **jimod4 said:**
> why don't you boot with the live cd.  Then copy the file /etc/X11/xorg.conf to a floppy.  then boot into the installation that does not work.  select recovery mode from the grub menu.  copy the xorg.cong file back to the hard drive.  then type startx.  enjoy free software.

In order to try this one, can anyone tell me what is the exact cp command to copy this file from the floppy, or an external usb stick?

---

### Post by Therion on 2007-11-07
See if this will get you up and running.  

Boot with your LiveCD and at the boot menu, use F6.
Find the following line:
```
kernel          /boot/vmlinuz-2.6.22-14-genericroot=UUID=43a49820- ... dcb2c ro splash quiet
```
Edit that line by changing the word **splash** to **nosplash**.
Continue with the LiveCD.  I shortened the line of code because it's insanely long, but  You'll know it when you see it.  
What's important is that **ro splash quiet** part, and changing splash to read nosplash.

If you decide to install, you'll need to boot into Recovery Mode again from your hard drive and then re-edit that line, since you're no longer booting from the LiveCD.  You won't get a splash-screen when you first boot up, but you'll be prompted to install the restricted drivers once you do boot off your hard drive, and from there you should be good to go.

---

### Post by gavos on 2007-11-07
> **Therion said:**
> See if this will get you up and running.  

Boot with your LiveCD and at the boot menu, use F6.
Find the following line:
```
kernel          /boot/vmlinuz-2.6.22-14-genericroot=UUID=43a49820- ... dcb2c ro splash quiet
```
Edit that line by changing the word **splash** to **nosplash**.
Continue with the LiveCD.  I shortened the line of code because it's insanely long, but  You'll know it when you see it.  
What's important is that **ro splash quiet** part, and changing splash to read nosplash.

If you decide to install, you'll need to boot into Recovery Mode again from your hard drive and then re-edit that line, since you're no longer booting from the LiveCD.  You won't get a splash-screen when you first boot up, but you'll be prompted to install the restricted drivers once you do boot off your hard drive, and from there you should be good to go.

Im not sure that i understood what youre telling me in the second paragraph.. I allready installed ubuntu..

---

### Post by Therion on 2007-11-07
> **gavos said:**
> Im not sure that i understood what youre telling me in the second paragraph.. I allready installed ubuntu..
Ahh... Okay.  I thought you were still booting from the LiveCD.  That's good though, at least you have an install to work from.  To fix your black screen, try the following steps:

Boot your PC.
From the GRUB menu hit "Escape".
Select "**Recovery Mode**" (you'll wind up at a system prompt).
From the system prompt:
```
 nano /boot/grub/menu.lst
```
Scroll down to the bottom of the page using the arrow key, past all the # signs until you come to the first line that starts with Kernel.  This will be a long line of code that runs off the end of your display.  Use the arrow keys to scroll to the end of that line where you'll find where it says **-ro -splash -quiet**
Remove the word splash.
Ctrl+X to save, confirm the overwrite and reboot.

---

### Post by gavos on 2007-11-08
> **Therion said:**
> Ahh... Okay.  I thought you were still booting from the LiveCD.  That's good though, at least you have an install to work from.  To fix your black screen, try the following steps:

Boot your PC.
From the GRUB menu hit "Escape".
Select "**Recovery Mode**" (you'll wind up at a system prompt).
From the system prompt:
```
 nano /boot/grub/menu.lst
```
Scroll down to the bottom of the page using the arrow key, past all the # signs until you come to the first line that starts with Kernel.  This will be a long line of code that runs off the end of your display.  Use the arrow keys to scroll to the end of that line where you'll find where it says **-ro -splash -quiet**
Remove the word splash.
Ctrl+X to save, confirm the overwrite and reboot.

I done this but nothing happened
I have no problem with black screen or somethnig..
My problem is that from the time that the cursor of the mowse show up after booting, the pc is exxxxtremely slow and after you hit the password it never goes to desktop.. Its a cursor alone forever.. 

Its realy a so big problem?

---

### Post by gavos on 2007-11-08
Guys can anyone help me with this please!!!

---


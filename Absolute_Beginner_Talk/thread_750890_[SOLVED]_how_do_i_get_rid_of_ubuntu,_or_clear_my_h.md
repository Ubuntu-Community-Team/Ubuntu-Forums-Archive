---
title: "[SOLVED] how do i get rid of ubuntu, or clear my hard drive"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by rolledthatho on 2008-04-09
hey guys, i know so many of yall love linux, but since ive installed it over windows my comp has been HORRIBLE. speed, crashing etc.. 

anyway since i installed it, its messed up my ps2 port, (ive read a LOT about this bug) anyway i plug in the keyboard all the lights BLINK and then nothing, all i want to do is put windows back on my pc, but i cant "press any key" to boot the disk when it gives me the prompt. im using a usb keyboard now, and it dosent power on until the screen after the one i need.

what are my options aside from a loaded gun 

thanks for any help in advance

---

### Post by rolledthatho on 2008-04-10
ok guys, long story short, when i installed ubuntu it messed up my ps2 port (like it has so many others) seems like bug that has yet to be fixed. anyway i want windows back bad, but there is no way to boot it up without a keyboard.

can i just wipe out my hard drive put the windows disk in and let it recognize and automatically boot up windows, or at least take me to the option screen

---

### Post by rolledthatho on 2008-04-10
please anyone?

---

### Post by tamoneya on 2008-04-10
well if your keyboard isnt being detected until after the bios prompt i am inclined to say that this is a BIOS problem and unrelated to ubuntu.  Therefore I would attempt a BIOS flash to try and reenable the usb keyboard during boot.

Also in the ubuntu forums you should try not to bump your thread for at least 24 hours.

---

### Post by heartburnkid on 2008-04-10
If this issue is preventing bootup, then it's not an Ubuntu issue.  Your BIOS controls the keyboard before the OS even comes up; if you can't get into your BIOS Setup (the "Press <this key> to enter setup" bit you see when you first boot up), or your BIOS is throwing "Keyboard Not Found" errors at you, it means you have a physical problem, either with the keyboard or with the motherboard.

In short, get a new keyboard.

---

### Post by ELF_O8 on 2008-04-10
yeah, the easiest way to do this is to just put in the windows
disc and repartition all of the stuff from there. 
After re-installation everything should work fine, sorry you couldn't stick with Linux.

best of luck

---

### Post by PmDematagoda on 2008-04-10
@rolledthatho:- Please understand that creating duplicate threads is disallowed, just one thread on one topic in the appropriate section will do. Also as tamoneya said; please do not bump a thread more than once within 24 hours.

---

### Post by rolledthatho on 2008-04-10
ok tamoneya, sorry about bumping, guess i was jsut getting desperate, and im trying to have this fixed tonight so i can do some work on this thing tomm.

to everyone who spoke of BIOS, im pretty computer illiterate, so i dont know what that means, i did a lot of searching and found a lot about some bug, many people had problems with their ps2 ports once installing ubuntu. anyway if i can do this with my usb, then that would be fantastic, what do i need to do about the BIOS to fix that? and how do i do it?

heartburn kid, no new keyboards are needed i have 4 ps2 keyboards and 2 usb keyboards, none of them work on here, but all work fine on other computers. so whats this with the bios? 

ELF- the windows disk is in, how do i just "partition the stuff from there" if i cant get to the boot screen, it says "press any button to boot from cd" buttons dont work until the screen after that... then it mentions some stuff about GRUB something, but continues to boot up in linux

dematogoda, sorry it came across that way, my new thread in the begginer forum mentioned me wanting to get rid of it, but my main question (how to erase a hard drive) was completely different... even though i wanted it for the same reasons ;) 

sorry again

adidas where will sudo rm -rf take me, i see that it erases everything, but everyone says not to do it? this is my only computer so i need to figure out whats going on before i do anything or im lost with no internet for help. do i just type that in a terminal and restart and magically its gone? where do i go from there after running that terminal?

and still any help is appreciated

---

### Post by tamoneya on 2008-04-10
you should not be typing rm -rf it is a bad idea in general and he does not want to just remove ubuntu he wants to install windows.  Installing windows will replace any files or partitions belonging to ubuntu.  Suggesting anywhere about rm -rf is not a good idea in these forums since it can do so much irreversible damage.  

[http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

---

### Post by tamoneya on 2008-04-10
okay lets just start from the beginning and work our way to a solution.  What happens when you place your windows install disk into the cd rom drive and reboot the computer.  If everything is working right you should get prompted to "boot from cd" This is what you want to do.  If you get this that means that windows will start installing itself and in the process wipe out ubuntu.  If that doesnt work let the computer boot ubuntu and come back here and we will debug it.

---

### Post by rolledthatho on 2008-04-10
haha nah im not QUITE that comp illiterate, but i appreciate your help greatly and im willing to do whatever that will work 

to asnwer your question, ive done this a million times. i reboot, my keyboard lights power off. then screen pops up says, "press any button to boot from cd" i press a million DARK buttons (because it seems as if the keyboard dosent have power yet) and i get nothing aka it continues to boot up regularly

ps if you would like to help me on aim beachbum32785, might make it easier, thanks again

---

### Post by heartburnkid on 2008-04-10
It's a hardware problem, not a software problem.  Try a different keyboard.

Trust me on this.

---

### Post by tamoneya on 2008-04-10
okay well i believe that this is a BIOS problem.  i dont think you had keyboard support previously since you dont need to hit anything to boot the ubuntu cd.  we should flash the bios to attemp to resolve this.  do you know what motherboard you have?  it should say on the board itself if you dont know.


about bios flashes:
[http://www.devhardware.com/c/a/Hardware-Guides/Why-and-How-to-Flash-Your-BIOS/](http://www.devhardware.com/c/a/Hardware-Guides/Why-and-How-to-Flash-Your-BIOS/)

---

### Post by ELF_O8 on 2008-04-10
after reading other reviews, i think that your problem is a BIOS problem.
the BIOS of a computer is like the core, what the computer runs on when it isnt using an OS.
I think your BIOS is rejecting your ps2 keyboard for some reason.
I haven't a clue on how to fix that.

---

### Post by heartburnkid on 2008-04-10
You guys are both making a mighty big assumption here.  It's far more likely that his keyboard failed than that his BIOS failed, especially since this failure seems to have occurred suddenly (well, suddenly enough for him to attribute it to a change in software).  This is also the far easier thing to diagnose and repair, especially for a computer novice.  There's no reason for him to go mucking about with his bios unless and until we prove that the keyboard is not the problem.

EDIT:  OK, never mind, then it's not a keyboard issue.  Didn't notice that he'd already tried that.  Sorry.

Then it is time to root around in the BIOS (but not to flash it, not yet).  When you boot up, you should see "Press <Some key> to enter Setup".  Press that key.  Go under Integrated Peripherals or whatever sounds similar to that (it's going to vary from BIOS to BIOS), and make sure all your ports are enabled.  While you are in there, enable USB Keyboard Support.

---

### Post by tamoneya on 2008-04-10
we are currently debugging over IM.  I will post some updates if we get stuck but i think we are making progress.  Motherboard is [http://www.biostar-usa.com/mbdownloads.asp?model=M7VIZ%20V8.X](http://www.biostar-usa.com/mbdownloads.asp?model=M7VIZ%20V8.X)

Does anyone have any experience with this motherboard at all?

---

### Post by tamoneya on 2008-04-10
we just performed a bios reset with no success so now we are going to move onto a full bios flash.

---

### Post by rolledthatho on 2008-04-10
this guy (im assuming) is the man thanks for your help man we got it fixed

---

### Post by heartburnkid on 2008-04-10
Would you mind sharing the solution with us, for posterity?

---

### Post by rolledthatho on 2008-04-10
haha my fault, basically i took some connector pin of JMOS1 (it was on the bottom two) i put them on the top two. (there were 3) reset the BIOS and everything worked.

---


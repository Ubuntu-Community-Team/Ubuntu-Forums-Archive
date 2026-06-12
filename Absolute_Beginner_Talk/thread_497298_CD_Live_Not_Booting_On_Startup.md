---
title: "CD Live Not Booting On Startup"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Jeremywilms on 2007-07-10
ookay I know I burnd it 100% correctly, because it autoruns when I put in the disc everything works perfectly exept, when I put the CD Live CD in(I Burned it ISO) it auto runs and all of that. Though I restart my computer with the CD in it and it does'nt even give me an option on what I want to boot it. It just boots my default Vista.

---

### Post by Chilli Bob on 2007-07-10
Have you definately checked in your BIOS that the CD is set to boot before the hard drive? If you don't know how to check this let me know and I'll talk you through it.

---

### Post by Jeremywilms on 2007-07-10
=P I have no Idea how to check, explain please.

P.S I don't know what you mean by BIOS either XD!

---

### Post by RomeReactor on 2007-07-10
Hi. I agree with **Chilli Bob**, sounds like an issue with BIOS; make sure the CD is enabled to boot, and I would disable all other options (floppy, other HDs, just to be sure). And make sure to save the settings as you exit BIOS.

---

### Post by Jeremywilms on 2007-07-10
One problem, I don't know what a BIOS is, and I don't know how to check or enable my CD To boot before my harddrive, and If I do do this, and I don't have a cd in. Will it request a CD, or just skip ahead to the C Drive?

---

### Post by RomeReactor on 2007-07-10
Try pressing **DEL** after powering on your PC; most systems use that shortcut to enter BIOS, though it could be one of the function buttons (maybe F2; I'm not sure).

---

### Post by RomeReactor on 2007-07-10
[BIOS]("http://en.wikipedia.org/wiki/BIOS") means Basic Input/Output System; what it does is communicate with the pieces of hardware you have installed, to enable or disable them, or change certain settings.

---

### Post by Chilli Bob on 2007-07-10
OK, when you start you computer it will flash a little text on the screen. (it helps if you start with a warm monitor, if it's cold it might disappear before the screen is visible - not a problem with LCD)

Anyway, it will say something like "For setup press F2". The button in question is usually enter, delete or one of the function keys, it varies from PC to PC.

Press this button (you gotta be quick) and it will take you to the BIOS setup menu.  It's best not to change anything in here if you don't know what you're doing, but feel free to look around.  Usually the mouse won't work, so follow the on-screen instructions.

You will need to look for something like "Boot Order" or "Start-up options". Again it varies from PC to PC, but it should be obvious.

This will give you the chance to decide what order the PC looks for devices to boot from. Options will include the hard drive, the floppy, the CD, and depending on the age of your PC, maybe USB devices and the network.  You will have to change the order of these, using the on-screen instructions, so that the CD-Rom is the first on the list.  Then either the floppy or hard drive.  (Usually the hard drive unless you feel you may need to boot from floppy for some reason).

Follow the on-screen instructions to save and exit.  Boot up will continue as usual, except that the PC will now try to boot from the CD if it can.  If there is no bootable CD in the drive, it will just boot from the hard drive as usual.

Try that and let me know how it goes.

EDIT: I should have said that the changes to the BIOS will still be there next time you start the PC.  That's not a problem. Just make sure you take out the Live CD when you have finished with it so your PC will boot normally.

---

### Post by Jeremywilms on 2007-07-10
Hmm well....I got it to run and the Graphical setup came on. I don't want to install it though I just want to run it. So would I select the first option?

*Edit*
The first option being "Start Or Install uBentu"

---

### Post by Chilli Bob on 2007-07-10
I assume you are at the menu?? Yep, just select the first option and it will run off the cd.  If you want to start the install proper, there is a shortcut on the desktop when Ubuntu starts.  Be patient with the live CD. It runs much slower than a proper install.

Is this your first time in Ubuntu??  Welcome aboard!!

---

### Post by RomeReactor on 2007-07-10
Yes, **Start or Install Ubuntu** will run Ubuntu from the CD, it won't install anything untill you double-click the **Install** icon on the desktop.

A warm welcome from me too! :popcorn:

---

### Post by Jeremywilms on 2007-07-10
> **Chilli Bob said:**
> I assume you are at the menu?? Yep, just select the first option and it will run off the cd.  If you want to start the install proper, there is a shortcut on the desktop when Ubuntu starts.  Be patient with the live CD. It runs much slower than a proper install.

Is this your first time in Ubuntu??  Welcome aboard!!

Thanks, It vary impressive much better then the vista welcome screen. It actually runs alot faster then vista even on Live. I wanted to have this installed but installed on the same harddrive as my current operating system. And have accsess to the same files(I know there not all compatible). So basicly I was looking through the install are there any tutorials that teach you how to install two operating systyems?

P.S I think my resolutions is messed up a bit. How would I fix that?

---

### Post by Chilli Bob on 2007-07-10
I've never done a dual boot, so I don't feel safe advising you on this. There are tutorials out there if you search the forums. Also at the top of this page is a link to Support>documentation and Support>community. Look through these for advice.

Ubuntu seems to always start at your card's highest resolution. To change it go to System > Preferences and look for Dispaly settings or screen resolution or something. I'm at work on XP and can't remember the exact term.  You'll know when you see it.

---


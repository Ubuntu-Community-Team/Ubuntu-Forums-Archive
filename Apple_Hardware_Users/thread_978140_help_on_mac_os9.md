---
title: "help on mac os9"
date: 2008-11-10
forum: Apple Hardware Users
---

### Post by alphadelta14 on 2008-11-10
i finally have a good copy of hardy disk that is readable on my mac (g3 powerpc). i however have had no experience with booting into anything with my mac. i know enough to hold "c" when it starts, but the regular os just boots. i also have no idea how commands work.

~thanks ahead to whoever can solve my problem

---

### Post by justin92089 on 2008-11-10
What type of PowerMac G3 are you using?  I know if it is an older one (ie beige) model then you will have to use a special boot-loader.  Yellow Dog used to include one ages ago, and I think you may still be able to use that one with Ubuntu.

-What the bootloader does is it's an extension for mac os 9 (down to mac os 7 i believe) that is named so that a bullet prefixes the extension name (in the classic mac os's, extensions loaded alphabetically, the bullet forces it to load first).  When it hits that extension, the bootloader tells os 9 to stop booting, and starts the linux system.  This was because older apple computers (all powerbooks prior to the g3 lombard, and powermacs prior to the blue and white g3)(none of the ibooks or imacs were affected by this issue) had their rom soldiered into place and were unable to be altered.  That rom would only boot a Mac OS, nothing else.  Hence the need to first start into a Mac OS, then kick over to linux.  This is why the mac won't start from your ubuntu cd (it knows its not a mac os install cd).

So whatever you do, don't delete your mac os 9 install!!! unless you have the mac os CD to reinstall it.

I know this isn't quite the solution, just an explanation of why holding down the C key doesn't work.  Hopefully someone can pick up where I left off and provide the actual files necessary

---

### Post by alphadelta14 on 2008-11-10
it's a blue g3

---

### Post by justin92089 on 2008-11-10
hmm, then it should be able to boot directly from the ubuntu cd.  Dumb question, but are you sure you have the PPC version of the cd and not the i386, etc?  if you are sure it is the right version, then I have an idea.  pop the ubuntu disc into the mac, then shut down all the way.  After waiting a few seconds, press the power button and then immediately after that (but not at the same time) hold down the option key on your keyboard.  A blue screen should pop up, along with your mouse pointer, a button with a picture of your hard drive, and next to it (if it is the correct cd for the powerpc hardware) a gray button with a picture of a cd in it.  there will also be two buttons below those (a refresh button, and a continue button).  If the cd button appears, then just single-click on it.  After a few seconds the screen should go black then begin booting the cd.  Let me know how that goes.

---

### Post by alphadelta14 on 2008-11-10
it is definitely the ppc cd. i tried it and it only recognized the hard drive.

---

### Post by justin92089 on 2008-11-10
shoot, umm... does the cd come up on the desktop if you let the computer boot to mac os 9?  If it doesn't, then the cd drive may be bad.  If it does work, then is the cd drive an aftermarket/replacement model?  There is a very small number of aftermarket drives that don't boot macs for whatever reason (but that number is REALLY small).  Also, if it is aftermarket and you have the zip disk drive installed, are the jumpers set to the right settings (primary and slave and what not)?  Or if it is the only drive on that bus, also check to see if it is set correctly (i think you would want it as the primary if it is by itself).

If all else fail, I would try and see if you could borrow someones mac os 9 or any version of 10.x install cd (up to 10.4), and just see if it will boot the computer.  I will check to see if there was a firmware update for your computer.

---

### Post by alphadelta14 on 2008-11-10
the cd shows up which is a good thing. the drive is the very original one that came with the mac. and around here everyone has a windows xp, i am the only person with a sort of mac variation.

---

### Post by justin92089 on 2008-11-10
That's rough, being the only one with a mac.  Luckily now all my friends also have macbooks, so I'm not alone anymore.  I did some searching and found a firmware update for your mac.  I will post the link in the message.  Try updating the firmware and see if that doesn't make any difference of getting the cd to appear on the "blue boot screen."

P.S. i'd recommend printing the instructions on apple's page out, just to make sure you don't skip a step (at least, i printed them out several years ago when I update my powermac G4).

[http://docs.info.apple.com/article.html?artnum=58374](http://docs.info.apple.com/article.html?artnum=58374)

---

### Post by justin92089 on 2008-11-10
Also, how much ram do you have installed?  While booted in Mac OS 9 it can be found by clicking on the apple menu, and then the first thing in the list (should say "About this computer").  just make sure you are in the finder first (it will have the blue smile icon in the top right corner if you are... and it may say Finder along side the smile).

---

### Post by alphadelta14 on 2008-11-10
640 mb
i am trying to do the firmware update now, it took a little while to find the programmers button, but i got it.

---

### Post by justin92089 on 2008-11-10
okay, then you have more than enough ram for Ubuntu.  Sweet, let me know how the firmware update goes.

---

### Post by justin92089 on 2008-11-10
okay, may have hit a problem.  Do you have the powermac g3 blue and white, or an iMac G3 that is blue?  if it is the latter, what is the cpu speed?  That firmware update was for the power mac g3, and won't run on an iMac.

P.S. my mistake, i assumed you had a PowerMac, not an iMac.

---

### Post by alphadelta14 on 2008-11-10
i guess i have a regular g3, the one that has the monitor built into the computer. it didn't work

edit: sorry for telling you what you just figured out.

---

### Post by justin92089 on 2008-11-10
lol ya, that was my bad.  Alright, there are several different variations of the imac g3, each with a different firmware update.  We gotta figure out which one applies to yours.  You said you have 640 mb of ram.  Is your cd drive a tray?  or is it just a slot-loading drive?  (like a car-stereo type)

Also, how fast is your imac?  I'm guessing 500mhz?

---

### Post by alphadelta14 on 2008-11-10
i don't know how fast but i think its 400. and it has the slot loading drive.

---

### Post by justin92089 on 2008-11-10
okay, I believe this is the update you need.

[http://docs.info.apple.com/article.html?artnum=75130](http://docs.info.apple.com/article.html?artnum=75130)

Just make sure you have os 9.1, 9.2, 9.2.1, or 9.2.2 installed first.  If you aren't sure, let me know.

---

### Post by alphadelta14 on 2008-11-10
of course i have 9.0, figures

---

### Post by justin92089 on 2008-11-10
alright, no biggie.  if you have 9.0, you can update to 9.1 for free (actually, you can go all the way up to 9.2.2 for free, but 9.1 is high enough for the firmware update, and also the others require that you do them in order).  the updates are on apples website.  here is the link:

[http://docs.info.apple.com/article.html?artnum=75103](http://docs.info.apple.com/article.html?artnum=75103)

This will update you to 9.1

---

### Post by alphadelta14 on 2008-11-10
bleck! how many more of these do i need to do?
those updates are much harder than those security updates that windows has

---

### Post by alphadelta14 on 2008-11-11
well, i updated to 9.1 and then did the firmware update following. i can't get anything to happen with the "c" or opt key.

---

### Post by tiresia on 2008-11-11
It was ok to update the firmware, but I believe that you can't boot from the CD, because it is not the right one, or it was not correctly burned. Where did you download it and how did you burn it?
Download it here:
[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)
and burn it very slowly with the Apple Disk Utility

---

### Post by alphadelta14 on 2008-11-11
i burned it using the link that you showed me, the first one. i did it on my xp with active@ iso burner. i believe the result was in CDFS format.

---

### Post by tiresia on 2008-11-11
You should use better the Apple Disk Utility of your Mac OS 9

---

### Post by alphadelta14 on 2008-11-11
i have a CD-Rom drive on my mac. i can't burn anything there, in addition to the fact that the internet download would take a full day

---

### Post by alphadelta14 on 2008-11-17
i think that i should get an old download that was actually built for the Mac OS 9. put that on and upgrade, a lot. Can someone give me a link to an older version of ubuntu?

---


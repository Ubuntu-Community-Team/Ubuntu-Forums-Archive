---
title: "Blank screen on Live CD (for MAC)"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Radiolad on 2006-11-10
Hi, Well I'm VERY new to Ubuntu and recieved my Live CDs a few days ago. The good news is the CD for X86 PCs works great and I have played with all the goodies in that box  :D   The BAD news :mad:  I tried the CD for my iMAC and after the initial loading of all the software I had a short 3 second music intro followed by ....Blank screen  :-k   Juding by the number of postings this is very common and is all to do with video-card compatability :???:
My knowledge of PC/Macs is limited, (although I have rebuilt both hardware and software)  So can anyone either give me an **IDIOTS** **GUIDE **for tweeking software for the iMAC and/or POWER PC, both of which currenly run OS9.2,  **_OR _**When will the next release of UBUNTU include the mod??
Many thanks in antisipation,  Radiolad.

---

### Post by elcasey on 2006-11-10
If your Mac (please don't capitalize "Mac," it's not an acronym ;p) is too old to run OS X, it may be too old to run Ubuntu (though this is unlikely; probably just unsupported hardware). Have you ever tried upgrading your iMac to OS X? 

Worst case, try a LiveCD from another distribution. Not all distros will work on all machines, which is why this LiveCD thing is so great - no repartioning and reformatting until you're actually sure that the distro will work!

Someone more experienced with Ubuntu and Linux than me will probably have better suggestions, but try a Fedora LiveCD or do a search and find out which distros explicitly support the old iMacs (I'm assuming you have one of the eMac-style, "colored" iMacs with a CRT not and LCD?).

---

### Post by Radiolad on 2006-11-10
Hi, thanks for the info. Yes my imac is crt.
Cheers and thanks for your time :) :D 
Radiolad

---

### Post by linear on 2006-11-10
The LiveCD does not set up xorg.conf correctly for the iMac G3. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
 4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

---

### Post by Radiolad on 2006-11-10
Hiya, Thanks for the fix. Will this effect the iMac when the live CD is removed. In other words, if I mess this up will I have a permanent blank screen ?? :( 
Many thanks in anticipation, Regards Radiolad.

---

### Post by elcasey on 2006-11-11
No, you're editing a file that will be in memory (RAM) because it's running from the LiveCD, not the hard drive. OS9 isn't based on UNIX, so no worries there. Your Mac will still boot up fine when you remove the CD and reboot.

---

### Post by Radiolad on 2006-11-11
Hi, Many thanks...SUCCESS ! I followed your instructions to the letter and up came Ubuntu  :) :) 

If I may, two other quetions.
1. I have the iMac and a PowerPC G4. I want to delete OS9.2 from both of them and install Ubuntu. Will the LiveCD do this by clicking 'Load Ubuntu' icon. Or is there more to it?

2. As with my X86 PC, once Ubuntu is running the Macs, will I have 'right-click' and scroll facilities on the mouse ? (not available on OS9.2)

Again many thanks for you assistance  :KS  it is very much appreciated,
 Kind regards  Radiolad.

---

### Post by linear on 2006-11-12
> **Radiolad said:**
> 1. I have the iMac and a PowerPC G4. I want to delete OS9.2 from both of them and install Ubuntu. Will the LiveCD do this by clicking 'Load Ubuntu' icon. Or is there more to it?

During the install, you will be able to erase the hard disk (if you want to). See these installation instructions: [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC) (they were written for 5.10, but should apply - mostly).

> 2. As with my X86 PC, once Ubuntu is running the Macs, will I have 'right-click' and scroll facilities on the mouse ? (not available on OS9.2)What kind of mouse? If you have a one-button mouse, right-click is the F12 key; not sure about scroll.

One more thing - some people have had trouble installing to G4 Macs using the LiveCD. You may need the alternate install disk, or have to install 5.10 and then upgrade. The [Apple PPC Users]("http://www.ubuntuforums.org/forumdisplay.php?f=133") forum is a good information source.

---

### Post by Radiolad on 2006-11-13
Many thanks once again. The mouse is a USB L/R plus scroll mouse so I'm hoping this will be OK. Thanks for the Mac possible pitfalls. Cheers and kind regards,  Radiolad  :)

---

### Post by mo79 on 2006-11-13
> **linear said:**
> During the install, you will be able to erase the hard disk (if you want to). See these installation instructions: [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC) (they were written for 5.10, but should apply - mostly).

What kind of mouse? If you have a one-button mouse, right-click is the F12 key; not sure about scroll.

One more thing - some people have had trouble installing to G4 Macs using the LiveCD. You may need the alternate install disk, or have to install 5.10 and then upgrade. The [Apple PPC Users]("http://www.ubuntuforums.org/forumdisplay.php?f=133") forum is a good information source.

Glad to see another happy iMac user.
Just want to know (I'm a PC user), and someone I know may want to spruce up their ageing rev. B iMac G3 233, tray loader.
What would be the best bet, Ubuntu or Xubuntu and what are the system requirements and recommended hardware upgrade options?

---

### Post by migheleto on 2006-11-13
> **linear said:**
> The LiveCD does not set up xorg.conf correctly for the iMac G3. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
 4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

Worked absolutely fine :cool:  Thank you very much.

---

### Post by mgpowell2000 on 2006-11-13
i'm still stuck on my iBook G3 installing ubuntu.  

after i hit ctrl-opt-F1 i typed in "sudo nano /etc/X11/xorg.conf"
and then...
nothing much happened.  the cd kept making its spinning noise.

what did happen was the "ubuntu@ubunt:~$" prompt came up again and then a second time, followed by "sudo nano /etc/X11/xorg.conf"

shouldn't some sort of menu pop up?  what should i type next?

what i did was type "section "monitor"" because i read that somewhere else.  uh.

as you might tell, i have no experience doing any programming or linux.  so thank you much for understanding.

---

### Post by slorimer on 2006-11-17
> **linear said:**
> The LiveCD does not set up xorg.conf correctly for the iMac G3. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
 4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

All went fine until step 6 (BTW - those on euro keyboards the # is Shift-option-3). First, it wouldn't accept ----P as an argument or something. All hell has broken loose afterwards. There is a blue screen screaming error after the start-up sequence. So restarting Gnome after just wasn't working. Have snow imac G3 600 MHz with CD-ROM, i think the last in the series.

---

### Post by linear on 2006-11-18
> **slorimer said:**
> All went fine until step 6 (BTW - those on euro keyboards the # is Shift-option-3). First, it wouldn't accept ----P as an argument or something. All hell has broken loose afterwards. There is a blue screen screaming error after the start-up sequence. So restarting Gnome after just wasn't working. Have snow imac G3 600 MHz with CD-ROM, i think the last in the series.

A typo in xorg.conf, perhaps? If you want to start fresh, use:

[B]sudo dpkg-reconfigure xserver-xorg
[/B]
to regenerate xorg.conf.

---

### Post by dodginess on 2006-12-19
Just a quick message to say thanks for the advice as well :) In case anyone is trying to get Ubuntu working on an eMac you will also probably need to change the Default Depth to "16" from the normal value of "24" - when I originally updated the Horiz and Vert values Gnome restarted but gave a configuration error, setting the 16-bit mode fixed it and no problems to date. This information was included in another post but without the Horiz and Vert details mentioned.

Keep up the good work guys - another convert for you :D

dodginess

---

### Post by ultravisiontech on 2007-02-06
> **linear said:**
> The LiveCD does not set up xorg.conf correctly for the iMac G3. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
 4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

- I tried these instructions but after nano launches xorg.conf appears to be blank.  I did a ^W and searched for "HorizSync" and "VertRefresh" and they were no where to be found.  I also did next page and nothing was there.

---

### Post by MahRain on 2007-02-23
I can confirm this procedure also works for Xubuntu 6.10 (maybe a better choice for a G3)

---


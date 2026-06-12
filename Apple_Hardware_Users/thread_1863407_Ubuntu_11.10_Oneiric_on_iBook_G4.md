---
title: "Ubuntu 11.10 Oneiric on iBook G4"
date: 2011-10-17
forum: Apple Hardware Users
---

### Post by jumil on 2011-10-17
I have this old iBook G4...

[http://www.everymac.com/systems/apple/ibook/stats/ibook_g4_1.2_12.html]("http://http//www.everymac.com/systems/apple/ibook/stats/ibook_g4_1.2_12.html")

...and have been trying various versions of Ubuntu on it over the last  few weeks. Now that 11.10 was released, I decided to give it a go and it  turns out Unity 2D with LightDM runs really well on the thing. 
So well in fact that it would be a shame not to get the rest of the system working.

I did a cli install from the 11.04 mini iso (as the 11.10 mini iso's  installer would not recognize the iBooks harddrive) and upgraded that to  11.10 before installing Ubuntu via tasksel.

With configuring the system I stand on the shoulders of giants. Mainly rsavage's awesome  			 			[How to install power pc Lubuntu 11.04 with Firefox 5]("http://ubuntuforums.org/showthread.php?t=1798792") thread.

I have been exclusively using Ubuntu on my desktop machine for just 6  months  now and thus am no master in these things. Any help would be  greatly  appreciated.



Here is the current situation.
[SIZE=2]
**What doesn't work:**[/SIZE]


[LIST]
[*]**[COLOR=Orange]wifi[/COLOR]** Installing the firmware for the airport extreme card got this working
[/LIST]
 [FONT=Courier New]sudo apt-get install firmware-b43-installer[/FONT]

, however the wifi indicator does not show the signal  strength. After  connecting it appears to be stuck somewhere in the  connection animation  and does not change at all.


[LIST]
[*][COLOR=Red]**brightness fn buttons**[/COLOR]
[/LIST]
These simply does not work.
The buttons were working out of the box on 10.10 and 11.04 Ubuntu and Xubuntu though.


[LIST]
[*][COLOR=Red]**Sleep/Suspend**[/COLOR]
[/LIST]
It just  doesn't. It does a logout though but then does not turn of the screen  and backlight and does not go to sleep. I sort of miss the little snore  lamp.
I asume this might be linked to backlight problem above.[SIZE=2][/SIZE]

---

### Post by jumil on 2011-10-24
I actually got the backlight dimming to work. And as a bonus it suspends and wakes on both command and lid too.\\:D/

For the wifi indicator I still have no clue though. I'll continue to work on this but might be willing to drop it, since it is no absolute show stopper. I mainly wanted the dimming  for better battery time.

I'll post the backlight solution to a new thread with a more descriptive title, so google can find it.

---

### Post by rsavage on 2011-10-25
jumil, just wondering if you've tried the live cds to find out if they have the wifi signal strength indicator problem?  There seems to be a few quirks caused by installing from the mini cd.

> as the 11.10 mini iso's  installer would not recognize the iBooks harddrive
Can you expand on what the problem was please?  Did it not have the correct device driver or was it the sda/hda problem?  I want to update the lubuntu thread with oneiric info so it would be useful for me to know (thanks for calling the thread awesome btw!!!).

Was the command you used to upgrade "sudo do-release-upgrade"?

---

### Post by jumil on 2011-10-25
I have not tried to install from the full 11.10 live CD yet, but was able to boot it. There is another problem with installing form it right? I only followed those discussions marginally throughout the last week and it seemed I was the only person actually running 11.10 on an iBook.
It is my understanding that I have to install in order to be able to install the wifi firmware to test this. Or is there a way around that?

Since I got my kernel from my other thread now I might try to install from live over the weekend.

The mini iso was missing the correct device driver.

Yes "sudo do-release-upgrade" is what I used.

---

### Post by rsavage on 2011-10-25
Pretty sure you can use the normal command to download the firmware and wifi will work with the live cd.  The status of the live cd seems to keep changing.  It may work now!

Thanks for the feedback.

---

### Post by jumil on 2011-10-26
I was able to install the downloaded firmware-b43-installer package from a USB stick while running from the current live CD.
The problem with the wireless indicator persist.

---

### Post by b_schear on 2011-11-13
Hey everyone,

So I got 11.10 on my IBook G4 no problem.  Just need to get the wireless working.  I should try the firmware-43 thing.  Where can you download that?  Thanks in advance.

---


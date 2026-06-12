---
title: "New install boots to black screen; mem test stalled"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by randypr on 2008-03-07
The Machine: 
Compaq Presario 5000US
Pentium III Coppermine @933 MHz
512 MB RAM
Maxtor 20 GB HDD
Generic CD-ROM
ATI 32MB Graphics card

I downloaded Alternate Install 7.10, burned an iso cd and went through install process. It formatted entire disc (wiped XP), and I selected the default (regular) packages, as best as I can recall. I selected 1024x768 as highest rez. Rebooted, got the fancy orange bar, and then the Black Screen. All stop.

I tried a Live CD (I have both a Live and an Alt CD). It got to the orange bar, then went black. Several times.

Rebooted into recover mode, watched the words fly by, it failed the ieee80211 (err= -17), but everything else said OK. [insert edit] I also tried booting into safe video mode. Same-o. [end.edit] Tried startx, no go, now in mem test. 

It got to Test 17 and is still sitting there. I can't send a screenshot, but it says a bunch of nonsense (mvm nesos admptm, Cist:itlile, etc.) and the bottom task (?) bar says: 

(S) eot ccniuain S) collc  (Rsrl_nok

The cursur is sitting at the upper left of the screen, blinking and blinking, and won't move; i.e, it's not accepting keyboard input. 

Now what?

And yes, md5checksum is correct, tried cd check: is OK; I hunted high and low in the forums, tried Google, and now I'm back.

This machine was running perfectly with XP Pro Serv Pak 3 12 hours ago, and had a solid internet wireless connection. Now, nada. 

:confused:Help.

---

### Post by uberlube on 2008-03-07
does your pc have wireless. That error says 80211 wchich looks to me like 802.11

---

### Post by Fixman on 2008-03-07
Can you access ttys by pressing ctrl+alt+F1? (or ctrl+alt+f{any number till 6})

---

### Post by uberlube on 2008-03-07
also try to specify your vga into the boot process by pressing e to edit while the ubuntu login is highlighted during grub. delete 'quiet splash' and add 'vga=791' in the kernal line.

---

### Post by randypr on 2008-03-07
This is uncool.

Rebooted and now I don't even get the Compaq bios splash screen.

I'm going to remove the ATI card.

Hang on.

---

### Post by randypr on 2008-03-07
OK, I removed the ATI card and it booted properly.:)

Now I can't remember my freaking user name or password.

Aarrgh.

Where are the proper drivers for this ancient ATI card, or should I just forget about that?

And thank you, BTW.

(What was up with that mem test??)

---

### Post by uberlube on 2008-03-07
Envy will install the proper drivers. But if you have an integrated nvidia based card, id stick with that. ATI isnt supported very well in linux.

---

### Post by randypr on 2008-03-07
Super.

But where did I hide the user name/password?

I know, I know; I'm an idiot.

---

### Post by uberlube on 2008-03-07
:lolflag:

---

### Post by randypr on 2008-03-07
Whew.

[s]Found[/s] Reset the password and now we're good to go.

Thanks again, everybody.

---


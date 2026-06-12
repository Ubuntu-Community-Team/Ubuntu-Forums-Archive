---
title: "sound"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by sunrex on 2005-08-18
how do i disable my onboard sound and get my sound card to run?

---

### Post by EnderTheThird on 2005-08-18
You'll need to give more information about your system (motherboard and sound card at least) before anyone here will be able to help you.  I just installed Linux yesterday, so I can't help you myself, but other people will need that information before they can do anything for you.

---

### Post by sunrex on 2005-08-18
my sound card i have is sound blaster live 24 bit, however, i have no clue what the motherboard soundcard is =/

---

### Post by sunrex on 2005-08-18
i got it to work somhow on suse 9.3 pro

i installed alsa and configured it..then somthing else

but i forgot everything i did back then

so whats the alsa driver i need, can i just sudo-apt get it, if so can u tell me the command

and then do i type in sudo alsaconf or what...

im sorry for bugging you so much, but if im going to 100% switch over, i want everything running...right now im on duel boot

---

### Post by poofyhairguy on 2005-08-18
[QUOTE=sunrex]how do i disable my onboard sound and get my sound card to run?[/QUOTE]

Look in your bios menu (aka the menu where you tell the computer to boot from a CD).

---

### Post by sunrex on 2005-08-18
im not booting from a cd....oh u mean the thing when it starts up with COMPAQ and press F1?

---

### Post by EnderTheThird on 2005-08-18
That sounds about right.  Usually it will tell you to press one of the F# keys, Enter, or Delete in order to access Setup and/or BIOS.

---

### Post by the_purulent on 2005-08-18
That's the one! 
In that menu there will be an option to disable onboard sound (or at least there is on most every system). 

As for setting up your other card... my soundblaster was autodetected.  So yours should be as well.  I would guess that once the onboard is disabled the other one should then be the default...

---

### Post by sunrex on 2005-08-18
i think i did it but sound still doesnt work

i was runnin suse 9.2 pro then went to 9.3 pro but i had to configure it with alsa and i have never gotten it to work on ubuntu

so im running kubuntu so how do i get sound working, i know i need alsa..but can i use sudo apt-get install for it or how do i get the right one

btw this is Sound Blaster 24 bit live

if i cant get sound at all im going to go nuts, couse my on board sound SUCKS lol

---

### Post by sunrex on 2005-08-18
well the red thing on the speaker at the bottom of taskbar is gone still no sound so i guess i need to install alsa still..but no one has told me the command

---

### Post by sunrex on 2005-08-18
will this help?

SOUND server informational message:

error while initializing the sound driver:

device: defult cant be opend for playback (no such file or directory)

the sound server will continue using the null output device..

so..


anyone tell me how to fix my sound?

---


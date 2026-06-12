---
title: "Sounds Issues"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Qwerty_ on 2007-07-29
I have two sound cards in my Ubuntu box. One is a basic onboard sound card, the other is a Soundblaster 5.1 card.

My problem is Ubuntu swaps and changes through which sound card it likes to use, it is different each time I boot so I have to swap the cables.

I am sick of swapping them and have not been able to do anything in the System>Preferences>sound menu.

I want to disable the onboard sound card so I can simply use my Sound Blaster card.

Secondly when recording in Audacity everything sounds weird and I think that the first problem could be causing it.

---

### Post by Jeek Elemental on 2007-07-29
if you dont want to use onboard sound at all, the simplest solution may be to disable it in bios; look under "integrated peripherals" or similar.

if you want to have both available try this:

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)

---

### Post by Qwerty_ on 2007-07-29
I will go have a look in the Bios now, cheers.

---

### Post by Qwerty_ on 2007-07-29
Alright cheers Jeek Elemental that worked.

Is some where that  I can tell the line-in to act as a mic I think that might be what the problem is, what are some commands I can use to mess with alsa.

Edit: alsamixer is the command but I have kind of stuffed things up... how can I reset it to defaults?

---

### Post by Qwerty_ on 2007-07-29
I hate to do this but  I need to bump this topic. Because I would like to get my sound back workind properly.

Is there no command to reset alsa to defaults?

---

### Post by Jeek Elemental on 2007-07-29
you can try:

sudo dpkg-reconfigure alsa-base
sudo dpkg-reconfigure alsa-utils

and then :guitar:

---

### Post by Qwerty_ on 2007-07-29
Thanks for your help, however, it did not fix the sound issues most things sound like rubbish now not sure how I did it though.

---

### Post by billstei on 2007-08-04
I also have this same problem: one sound card built in to the motherboard, and one PCI512 soundblaster card.  Which card gets used as the primary channel by ALSA is completely random from one boot-up to the next.  Jack setup is similarly unpredictable with HW0 sometimes being the built-in sound and sometimes the PCI card.  Turning off the built-in is not the solution I am looking for.  I want to use both cards simultaneously, and I do, but I never know which one will be the primary one.

Bill

---

### Post by billstei on 2007-08-05
Here is the solution I am using after having researched it a bit.

List the names of the sound cards in a terminal with:

cat /proc/asound/modules

You will get something like:

0 snd-thisandthatsoundcard
1 snd-someothersoundcard
2 snd-yetanothersoundcard

Then go to /etc/modprobe.d and edit the options file (make a backup copy of it first) using the editor of your choice (use sudo so you have permission to save) and add the names in the order that you want them like this:

options snd-yetanothersoundcard index=0
options snd-thisandthatsoundcard index=1
options snd-someothersoundcard index=2

Then you can try to restart the sound system, or just do the sensible Microsoft thing and restart the whole machine.  Then cat /proc/asound/modules should show them in the order specified and it will (hopefully) be that way after every boot-up.  I had one card that refused to be moved from index 1 so maybe this isn't 100%, but I think I at least have consistent enumeration now.

Bill

---

### Post by Jeek Elemental on 2007-08-06
to set default alsa card do:

asoundconf list

pick your favorite card and then do:

asoundconf set-default-card <your favorite card>

---


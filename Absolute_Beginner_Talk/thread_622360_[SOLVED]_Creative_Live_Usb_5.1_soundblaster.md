---
title: "[SOLVED] Creative Live Usb 5.1 soundblaster"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2007-11-24
Hi, has neone managed to get a Creative live card working in Ubuntu?  I looked around a bit, and well I'm completely out of my league.  I looked on the Alsa Wiki, but I don't even know how to find out what kind of chipset is in my card.  So far, Gutsy has recognized my card it even shows up in the Sound menu, but I only get sound on my front 2 speakers (5.1 surround set up)  

This is the link to the alsa webpage, I thought to give it a try myself, but even the install guide there is a little to vague for me. And I'm not sure which one I should follow.  There are two I'm not sure about.  The first is 

Sound Blaster Live 5.1     chipset :  emu10k2

the second.  

Sound Blaster Live 24bit  chipset : SB0410

On my soundcard box, I got Soundblaster Surround 5.1 but it also has something about 24bit home cinema surround.  

Neway what I would like is maybe a link to some guide or maybe some hints so I can start figuring out how to go about this.

Many thanx

---

### Post by gn2 on 2007-11-24
There's useful info here: [http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb](http://gentoo-wiki.com/HOWTO_Install_Creative_Sound_Blaster_Live_24-bit_external_(usb))

and here: [https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I have a USB sound card which I use with Linux for a while, if I remember rightly the package to make it work was in Synaptic, snd-usb-audio

---

### Post by rexxxlo on 2007-11-24
i have a very similar card and it works for me but i don't have 5.1 speakers 

the emu10k chip is of good quality and alsa has some info on it 

click system>preferences>device manager and you should find out if it is supported and what model it is exactly 

there is a command to get info on just that but im still a newbie so i cant remember hopefully someone will chime in 

good luck and i will watch this thread for more info also

---

### Post by bobpur on 2007-11-24
I have a Soundblaster 5.1 XGamer in an old Compaq that worked "out  of the box" with whatever distro I fed to it. I'm using it now listenng to Streamtuner and surfing the forums :)
OOPS! I just noticed the part about your desire to use 5.1 speakers. I'm using 2.1 Altic-Lansing speakers. I don't have the room for 5.1 speakers amongst my other projects. Sorry:(

                          Good Luck

---

### Post by rexxxlo on 2007-11-24
do you have all of the sliders in the volume control for each channel?

i know there are sliders the will control the sound output for each speaker or pair ?

my problem is how do i get just a sub control....then have it crossover with a low pass flter at around 80 hz?

---

### Post by jbguev on 2007-11-25
Holy Smokes!!!!!!
I just got in the forums to check to see if anyone had gotten their 5.1 speaker system working, and I stumbled across this thread.  I decided to start messing with the alsa volume control and discovered a whole bunch of settings I could play with.  I enabled the "Surround" checkbox, which produced a slider, and increased the volume and, voila! both my rear speakers came on.

I hope this helps.

Jerry

---

### Post by rexxxlo on 2007-11-25
well im glad that you can here the monsters behind you  but do you have a subwoofer?

---

### Post by whitethorn on 2008-01-01
Hi so I've been working at it, and I finally got it surround sound working.  I don't know if it's true surround, but at least I got my bass and all my speakers working.  I used the script from whashnez on this webpage

[http://ubuntuforums.org/archive/index.php/t-104704.html](http://ubuntuforums.org/archive/index.php/t-104704.html)

the sebastfr skript didn't work for me.

---

### Post by Shazaam on 2008-01-01
I don't have the usb version as mine is pci but it works great. It isn't "true" surround in the sense of a dedicated home audio amp but it's close. To find more stuff to tweak open a terminal and type in "alsamixer" (without the quotes). Lots of goodies there; if you find a setting with "MM" this means the setting is muted. Highlight the setting and hit the "m" button on your keyboard to unmute it. Make sure you use the right and left arrow keys on your keyboard to move around in alsamixer.

---

### Post by Shazaam on 2008-01-06
Per your pm it looks like Creative usb sound card support for linux is pretty slim. You could go to the Soundblaster forums and make a pest out of yourself.  :)
 Maybe somebody will get a clue and look into the situation.

[http://forums.creative.com/creativelabs/board?board.id=soundblaster](http://forums.creative.com/creativelabs/board?board.id=soundblaster)

---


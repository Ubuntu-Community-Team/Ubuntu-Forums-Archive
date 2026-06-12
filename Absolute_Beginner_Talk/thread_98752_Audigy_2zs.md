---
title: "Audigy 2zs"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-04
Hey guys!

Hope everyone is well everywhere and someone is able to help me! I was checking out the compatible hardward list and I noticed the the Creative Labs **Audigy 2zs ** soundcard was not listed. Currently I have Ubuntu 5.10 installed on my **laptop** and love it muchly, but the wife is buying me a **second HD** (250gb seagate SATA 7200rpm) for x-mas for my tower in which i have the 2zs sound card, now my question is if I install breezy will the sound even work?

---

### Post by Gray. on 2005-12-04
I can confirm that the Audigy 2 ZS works in Ubuntu 5.10 as that is what I have in my PC right now!

*EDIT* When you install Ubuntu, one of the first things you should do is run this command in the terminal
```
sudo alsamixer
```
and then put the PCM controls up higher (well any of them but this is the main one I put up)
Press Esc to exit alsamixer
This helps to get the sound to be louder as (I personally think that) the default levels are too low.

---

### Post by adduds on 2005-12-04
**OH WONDERFUL!** that's great to here, now my second question is:

1. is it **hard** to configure 

2. how does it sound

Because I know the sound on my laptop was quite comprimised after installed breezy compared to XP, now does it sound just as good on breezy? sorry just curious music is a **HUGE** part of my computer experience

---

### Post by Gray. on 2005-12-04
Ubuntu does all the configuring for you.
But I just like to set the PCM level up higher in alsamixer so that it is louder (I use headphones plugged directly into the sound card so it's not that loud by default.
Also when you first install Ubuntu go to System > Preferences > Multimedia Systems Selector and make sure that the correct options are set. No need to worry, just select each option and click "Test" and if it works then make sure you select that one!
It may sound like alot of work but it really isn't. :D
Also I'd strongly suggest that you install and run [EasyBreezy]("http://dev.realistanew.com/easybreezy/easybreezy0.33-alpha.tar.gz"), which helps you set-up all the little fiddly bits that make Ubuntu so much better to use.
I don't really notice any difference between Breezy and XP, because all I really do is listen to music with Rhythmbox while I'm surfing/configuring/tinkering etc.

---

### Post by adduds on 2005-12-06
ya that's all I use it for aswell, that and movies...but I got totem pimped out, I watched Underworld on my lappy and it looked phat. thanks for the automatix tip....i also have 5.1 surround sound (Logitech Z5300)...it should still go ok tho eh?

---

### Post by Gray. on 2005-12-06
Yeah. In totem you can change the sound output in
Edit > Preferences > "Audio" tab
Also in alsamixer there are options for surround sound (may have to press m to enable them), but I don't have a 5.1 setup so I can't test it out. I'm sure someone else on the forums has 5.1 and Audigy2 and would gladly help.
Oh and welcome to Ubuntu :D

On and Automatix is no longer being provided but EasyBreezy is set to take its place. Get it [here]("http://dev.realistanew.com/easybreezy/easybreezy0.33-alpha.tar.gz").

---

### Post by adduds on 2005-12-07
Hey grey, i d/led the amd64 live ubuntu 5.10 popped it into my desktop, and had the surround working w/in seconds :), excellent

---

### Post by Gray. on 2005-12-07
Isn't it great when things just work? Glad to hear it all worked out well. :D:D:D

---

### Post by GangBoy on 2005-12-08
How did you make audigy 2 zs to work. When I plug mine to pcmcia slot system just freeze and also when i am booting system with plugged audigy.
When booting system it freezes on:
.
.
.
via 82 cxxx: already loaded
[45.499254] via 82xxx: Assuming DXS channels with 48k fixed sample rate
[45.499295] Please try dxs-support=5 option
[45.499328] and report if it works on your machine.
[45.499368] For more details, read ALSA-Configuration.txt
[45.499527] ACPI:PCI Interrupt 0000:00:11.5[C]->GSI 22(level,low)->IRQ22
[45.499590] PCI:via IRQ fixup for 0000:00:11.5 from 11 to 6
[46.086124] PCI:Enabling device 0000:06:00.0(0000->0001)
[46.086170] ACPI:PCI Interrupt 0000:06:00.0[A]->GSI 18(level,low)->IRQ 18

and there it freeze. Have you got any idea how to solve this problem?? I am runnig now on kubuntu breeze amd64, but i tried before ubuntu breeze amd64 and also both 32bit version and the problem was the same. Please help me. When i get it work i can finally throw out of my notebook :).

---

### Post by adduds on 2005-12-08
I just used the Ubuntu 5.10 Live AMD 64 CD, and everything worked....one thing i did was go into alsamixer(the gui one) and edit-->Preferences and enabled alot of stuff in their...turned PCM up, and tinkered w/ the surround a bit. other than that i just when to Systems-->Preferences-->Multimedia Systems Selector and chose ALSA as my output

---

### Post by joflow on 2005-12-09
How did you get 5.1 working with the Audigy 2zs?  I can't get multi-channel audio from a xvid file in linux with vlc or mplayer.  There is no option for it however I have the option in Windows.

---

### Post by adduds on 2005-12-09
i never tested it with video, but as far as i know it should work...I went to alsamixer (gui or term eithe or) and then to System-->Preferences-->Multimedia Systems Selector and chose alsa-mixer, and went to test and the test came through all 5 channels....

if that doesn't work could you describe what is happening?

---


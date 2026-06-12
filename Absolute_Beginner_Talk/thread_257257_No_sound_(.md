---
title: "No sound :("
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by TooRight on 2006-09-14
Hiya,

I installed Ubuntu the other day as a part of a dual-boot system for now and i am lovingggggg it!! I plan to get rid of windows totally as soon as I relearn some skills linux-style :)

The one thing that is bugging me is not being able to get my sound to work. I have a Dell, and my searches led me to the following webpage/patch (?) [http://librarian.launchpad.net/1728369/vaio-stac7661-test3.diff](http://librarian.launchpad.net/1728369/vaio-stac7661-test3.diff) , but i haven't got the foggiest idea what to do with the file... can anyone out there point me in the right direction?

Thanks in advance!!

---

### Post by xpod on 2006-09-14
WOW....THATS some first steps to be taking eh!!!!

I had to mess about with sound to begin but i dont recall having to comprehend ought like THAT:confused:

EDIT:...if alsa dont work try oss ...it`s in synaptic...that was what got my sound going one time.strangely i got alsa working this time round.

---

### Post by TooRight on 2006-09-14
Yeahh, I saw that page I was intimidated to say the least, lol.... dayummmm!! :o

I am determinedddddd to get this all figured out though!!

I check for oss and found a bunch of stuff listed in Synaptic. i installed alsa-oss and audiooss, with no change :(  ... any other suggestions? :D

*** Waittt.... was messing around with things, and i have soundddddddddd!! OMGG, I could kiss you right now Xpod!! lol

Thank you thank you thank you!!! :D

---

### Post by benfindlay on 2006-09-14
This may seem like a really stupid question, but are all your volumes turned up in the audio controls?

The reason I ask is bacause when I first installed ubuntu on an old compaq (internal speaker jobby) there was no sound. To get the sound I had to go into preferences for the volume settings, tick the box to show mono master and internal speaker volume controls. Both these controls were muted, and since it was a mono speaker, the master stereo did nothing for the volume.

Again, stupid question, but it took me a couple of days to realise that was what was up with mine! ](*,) 

HTH

---

### Post by TooRight on 2006-09-14
Yeah, I actually had checked that and all looked fine... i was at a total loss, lol.

When I double click on volume control from the taskbar now, and click on file/change device, I'm given two choices now: HDA Intel (Alsa Mixer) and SigmaTel STAC9221 A1 (OSS Mixer). I selected the first one (alsa mixer) and made sure all the tracks were set to be visible and that all were turned up properly.

I don't know what happened, but it all works now, thanks to install advice from Xpod :D

---

### Post by Rumor on 2006-09-14
Probably a silly question, but when you look under System | Preferences | Sounds, is your sound card selected as the default sound card at the bottom of the window? 
I ran into a problem like this with a computer that had integrated sound on the motherboard and a soundblaster card installed. Ubuntu defaulted to the one card and the speakers were plugged into the other. Switching the card in the sound preferences window turned everything on :D

---

### Post by xpod on 2006-09-14
Well...theres a first....ME giving advice...that leads to a eureka moment.

You should have a "multimedia system selector" in your prefarences tab(if not you can enable it in the alacarte menu editor)

Thats the first thing i recall playing about with to switch between alsa and oss or even esd...I have it set on "autodetect" and i aint had no probs with sound vanishing on certain app`s since my last crash and re-install.

Also...in "user`s and groups" if you double click on your user name a box pops up and if you chose "user privalages" you can check what functions your permitted to use including audio.....THAT should obviosly be defaulted for you but things do get muddled up at times so it`s handy to know about.

Glad you can hear the noise

EDIT:..AND theres THAT

---

### Post by TooRight on 2006-09-14
Cool, just enabled the multimedia system selector... thanks!!! :D

---

### Post by Nostromo on 2006-09-14
I'm an absolute beginner, so treat me like an idiot, but only if you have answers, please.
:wink: 

I've got Ubuntu 6.06. I don't get any audio out. I've checked the multimedia system selector & users and groups, and done some changes: 

using command "cat /proc/asound/modules" I found that my sound card is called ens1371 (Ensoniq). Following an advise ([https://launchpad.net/distros/ubuntu/+bug/56482](https://launchpad.net/distros/ubuntu/+bug/56482)) I wrote: "sudo nano
/etc/modprobe.d/alsa-base" and added at the bottom "install sound-slot-0 ens1371". I tried also "install sound-slot-0 snd_ens1371" since I thought I might have misunderstood the advise.

I added "snd-ens1371" to the "/etc/modules", as advised ([http://www.ubuntuforums.org/showthread.php?t=174872)](http://www.ubuntuforums.org/showthread.php?t=174872)), but didn't know how to "modprobe snd-ens1371" to load the driver manually.

In System/Preferences/Sound the default sound card is Ensoniq AudioPCI, but I don't know if it so even in the first place.

A friend told me to go via terminal to alsamixer, where I changed all MM-values into 00's and put the levels up.

I'd be very happy if someone could give me a hand here - and explain the process thoroughly.

---

### Post by jester805 on 2006-09-14
Kind of along the same problem (with sound anyway).

I have a Dell Dimension 9150 with a Creative X-Fi sound card.  I've been trying to figure out why I don't have any sound coming out of it.  A friend of mine found this quote from Creative:

"The X-Fi series of products are not supported under Linux. Closed-source drivers will be available for the X-Fi series of sound cards in the second quarter of 2007. These drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects)"

So that might help some people out anyway.

---

### Post by xpod on 2006-09-14
Theres an "alsamixer" command you could type in the terminal and check all your relevant controls are correct.

I only know the basics im afraid....only switched a pc on a few months ago and ubunto 3 weeks ago so im still stumbling across the answers to it all myself....WITH the help of these guy`s on here(and gals of course).

You can also right click your speaker icon up there in the corner and mess about in there to see whats what?

Sorry i dont know more

EDIT:..sorry ,i just realised it`s driver issues you have#-o

---

### Post by djtrancient on 2007-05-20
@TooRight:

Thanks, I was having problem getting sound, and then I made sure to switch to ALSA, and then activate all the panels, and make sure they were all unmuted.  From another noob, thanks for the help!

---


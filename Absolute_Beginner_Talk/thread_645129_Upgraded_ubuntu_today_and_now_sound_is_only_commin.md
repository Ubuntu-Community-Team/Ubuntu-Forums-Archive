---
title: "Upgraded ubuntu today and now sound is only comming in through left channel"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by petrolheadjman on 2007-12-19
as the title would lead you to believe, i am only getting sound out of my left speaker (and subwoofer.) after an update of the kernal and kernal headers

there is a very faint sound comming out of the right one and it is mostly static.

I have checked that everything is centered and that its not the speakers.

can you please help me i know a little about linux and any help would be appreciated thanks.

---

### Post by mmb1 on 2007-12-19
Go into a terminal and type "sudo alsamixer".  Please post the output.

---

### Post by petrolheadjman on 2007-12-19
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA VIA VT82xx                                                         &#9474;
&#9474; Chip: VIA VIA VT1708                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master Front [dB gain=-3.50, -3.50]                                    &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OM&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;   68<>68   93<>93   100<>100  44<>44   74<>74    65<>65   94<>94    0<>0     &#9474;
&#9474; <Master F>Headphon    PCM     Front   Front Mi    Line      CD      Mic      &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

that is more or less the output i get

---

### Post by mmb1 on 2007-12-20
Alright, this means that Ubuntu recognizes that your sound card is there, search synaptic for any packages related to your sound card model and manufacturer: HDA

---

### Post by petrolheadjman on 2007-12-20
yeah my card is an onboard via chipset sound card. HDA means high definition audio doesnt it??

---

### Post by petrolheadjman on 2007-12-24
yeah there isnt anything in synaptic, any other ideas?

---

### Post by HackCoders on 2008-01-03
This happened to me today, (my second day with ubuntu), I got wine installed and some good stuff along with it, I'm learning all the terminal stuff too ^_^

Anyway, what I did, I was playing around with the settings..I went to the sound icon at the top near the time, then I went to open volume control, then File > Switch device > pick the other one.. and the slider was down for some reason, so I moved it to the top and audio came from both sides...

Maybe that happened to you too..

---

### Post by dogerelly on 2008-01-03
I too am a complete newbie and had the same problem when I first installed Gutsy. I also corrected the problem by switching the mixer device from alsa (HDA Intel) to the OSS mixer. (System>Preference>Sounds then click on Device under Default Mixer button). This sorted out the problem immediately, but I am not sure whether using this device has any other negative impacts. Interestingly, for some other reasons I needed to reinstall Ubuntu, and this time everything worked fine straight off using the alsamixer......

---

### Post by jeffemmert on 2008-04-13
I also have the ESS Allegro-1 sound card in an old Gateway 600ygr laptop with two hard drives. C=XP Pro, F=Ubuntu 7.10. When I boot with XP the sound is great; when I boot with Ubunto, I only get sound from the left channel. I've tried each of the suggestions in the previous posts (update drivers, sudo alsamixer, switch devices and adjust volume, reboot) and it's still a lefty:(

Short of the version 8 upgrade next week, what else have you got?

---


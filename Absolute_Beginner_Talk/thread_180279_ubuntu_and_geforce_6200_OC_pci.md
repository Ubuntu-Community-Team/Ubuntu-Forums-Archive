---
title: "ubuntu and geforce 6200 OC pci"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-21
just grabbed this video card for cheap so i could hopefully run XGL.. since my old video card was an intel integrated.. but starting ubuntu stops on "loading hardware drivers" when i am on the card bios wise, i can boot up if i switch the video card off and to my integrated one, so i booted that way, installed the nvidia drivers, and it added nvidia into my xorg.conf, so i rebooted and it still wont boot.. also the installed didnt seem to pick up the card from the beginning.. am i doing something wrong? or am i lucky enough to have an unsuported card

oh yeah im using dapper.. but i thought this was an absolute beginner problem (never did this before)

---

### Post by joshrobinson on 2006-05-21
does anyone at least know how to figure out the card's bus identifier?

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]does anyone at least know how to figure out the card's bus identifier?[/QUOTE]


Should be able to find out with 

```
lspci
```

you'll probably have to have the card in to see its BusID, but I could be mistaken.

---

### Post by Belathor on 2006-05-22
I have an XFX Geforce 6500 which is basically and 6200 TC with a higher clock speed and it was recognized out of the box (as a 6200) so I can't imagine it isn't supported. I have no idea about its bus identifier though. good luck

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]Should be able to find out with 

```
lspci
```

you'll probably have to have the card in to see its BusID, but I could be mistaken. It's a nvidia card right? What model?[/QUOTE]

BFG nvidia GeForce 6200 OC, i think i found out the bus of it as 0:5:0.. but it still wouldnt load it.. with the nvidia driver
but the gpu on it is geforce 6200.. not sure what to do

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]BFG nvidia GeForce 6200 OC, i think i found out the bus of it as 0:5:0.. but it still wouldnt load it.. with the nvidia driver
but the gpu on it is geforce 6200.. not sure what to do[/QUOTE]

And you put that BusID into your xorg.conf file right?

---

### Post by joshrobinson on 2006-05-22
yeah i did sudo dpkg-reconfigure xserver-xorg and ran through the setup, put in nvidia geforce 6200 as the name, then pci:0:5:0 in and picked the nvidia driver

still hangs up on loading hardware drivers

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]yeah i did sudo dpkg-reconfigure xserver-xorg and ran through the setup, put in nvidia geforce 6200 as the name, then pci:0:5:0 in and picked the nvidia driver

still hangs up on loading hardware drivers[/QUOTE]

If you push ctrl+c to get past it, does anything positive happen?

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]If you push ctrl+c to get past it, does anything positive happen?[/QUOTE]

not really, it always finds my onboard intel video.. even when its not activated in the bios, or putting out video from the vga port

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]not really, it always finds my onboard intel video.. even when its not activated in the bios, or putting out video from the vga port[/QUOTE]

I replaced my onboard ATI video with a Nvidia card and all I had to do was get the BusID with lspci and there weren't any other problems, so this seems a bit strange.

The author of this thread, [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074), might be able to help you. He seems to be the master of Nvidia cards.

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]I replaced my onboard ATI video with a Nvidia card and all I had to do was get the BusID with lspci and there weren't any other problems, so this seems a bit strange.

The author of this thread, [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074), might be able to help you. He seems to be the master of Nvidia cards.[/QUOTE]

alright well, i check to make sure i got the busID right, and try again.. if not i will send that guy a pm and see if he can maybe shed some light on it.. bfg video cards use straight out nvidia drivers, so it should think that its an nvidia 6200.. im downloading a suse 10.1 iso right now and is almost done, hopefully that will recognize it so then i at least know if i have to make another trip to bestbuy and try another card

i might be a good while, but i will update how things go, but thank you for the lspci command :-D

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]alright well, i check to make sure i got the busID right, and try again.. if not i will send that guy a pm and see if he can maybe shed some light on it.. bfg video cards use straight out nvidia drivers, so it should think that its an nvidia 6200.. im downloading a suse 10.1 iso right now and is almost done, hopefully that will recognize it so then i at least know if i have to make another trip to bestbuy and try another card

i might be a good while, but i will update how things go, but thank you for the lspci command :-D[/QUOTE]

I hope you can get it working!

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]I hope you can get it working![/QUOTE]

yeah me too :-/ at least i have a laptop, so the computer not runing doesnt kill me

but lspci comes back as 0000:05:00.0 vga compatible controller: nVidia corporation geforce 6200

when i do dpkg reconfigure the pci bus of my other card isnt as long, should i just put it in the format the other one is? 0:05:00 ?

---

### Post by joshrobinson on 2006-05-22
oh, and ill be following your xgl howto if i ever get this thing to work.. ive had it bookmarked for awhile

shame it wont work for my laptop's ati.. but im pretty sure its an unsupported card.. and i run amd64

---

### Post by bluevoodoo1 on 2006-05-22
My lspci show...
 
0000:02:09.0

and in my xorg.conf it looks like...

PCI:2:9:0

EDIT: I'm actually using the guide I link at the top of my page now (it's [here]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29")), it has fewer steps and is a bit easier--- with the same outcome.

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]My lspci show...
 
0000:02:09.0

and in my xorg.conf it looks like...

PCI:2:9:0[/QUOTE]

hmm so mine would be 0:5:0 then right?

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]hmm so mine would be 0:5:0 then right?[/QUOTE]

Hopefully it is... Try it!

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]Hopefully it is... Try it![/QUOTE]

alright well a couple of my friends are bugging me to get on xbox live and play some call of duty, so im gona take a break from it.. thanks so much for your help, hopefully ill get it up and running.. ill update in a few hours on whats going on.. bookmark this if you could and check back tomarrow for me :-D

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]alright well a couple of my friends are bugging me to get on xbox live and play some call of duty, so im gona take a break from it.. thanks so much for your help, hopefully ill get it up and running.. ill update in a few hours on whats going on.. bookmark this if you could and check back tomarrow for me :-D[/QUOTE]

Sure thing. I hope you can get it working. 

Out of curiosity I was just looking here..
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

and I didn't see your 6200 OC as a supported card....

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]Sure thing. I hope you can get it working. 

Out of curiosity I was just looking here..
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

and I didn't see your 6200 OC as a supported card....[/QUOTE]

its a geforce 6200.. bfg just overclocked it a bit, thats what the OC stands for.. but ubuntu recognises it as a 6200 in lspci and device manager.. its just a matter of getting it to use it

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]its a geforce 6200.. bfg just overclocked it a bit, thats what the OC stands for.. but ubuntu recognises it as a 6200 in lspci and device manager.. its just a matter of getting it to use it[/QUOTE]

Oh ok! I thought OC was actually part of the model name.

---

### Post by joshrobinson on 2006-05-22
[QUOTE=bluevoodoo1]Oh ok! I thought OC was actually part of the model name.[/QUOTE]

ok well, with suse, and ubuntu, it sends kernel panic's at my system like crazy, a bunch of codes come back that i dont understand or doesnt say anything usefull, and then time's out and just stays there

bestbuy i go again tomarrow.. and try to get a different card.. ill try for ati this time.. they dont have any TRUE nvidia cards there.. so hopefully an ati radeon will work :-(

---

### Post by joshrobinson on 2006-05-22
update: my motherboard is a piece of crap, same thing with an ati card, switching computers and ram with another in my house..crap motherboards...

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=joshrobinson]update: my motherboard is a piece of crap, same thing with an ati card, switching computers and ram with another in my house..crap motherboards...[/QUOTE]

Yikes! oh no!

---

### Post by joshrobinson on 2006-05-23
[QUOTE=bluevoodoo1]I replaced my onboard ATI video with a Nvidia card and all I had to do was get the BusID with lspci and there weren't any other problems, so this seems a bit strange.

The author of this thread, [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074), might be able to help you. He seems to be the master of Nvidia cards.[/QUOTE]

ok so the video card works.. had trouble getting xgl to work in ubuntu, tried suse.. couldnt even get the drivers to compile the kernel module because ati screwed up the installer or something.. not sure.. but i dont have a file i need thats supposed to be in the ati directory.. so im going to build a package for ubuntu and try again.. i want xgl so bad :-(

---

### Post by bluevoodoo1 on 2006-05-23
I'm glad you got something working.

---

### Post by joshrobinson on 2006-05-23
[QUOTE=bluevoodoo1]I'm glad you got something working.[/QUOTE]

just trying to get ati to overwrite mesa for opengl now

---

### Post by joshrobinson on 2006-05-23
well i finally have xgl... but the rain plugin wont start.. i want it to rain on my desktop :-(

---


---
title: "supported hardware?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by yasahiro on 2007-06-14
i would really like to switch to ubuntu, but theres a few things keeping me from doing so...

1st... my graphics card...its a geforce 6600gt agp 8x...  i read somewhere... where there was a simple one word to type in, and it downloaded a program, which seemed like it automatically detected the exact type of graphics card you had, and installed it, but i cant find that program again...

2nd... my sound card, i also read somewhere that someone got the turtle beach montego ddl optical output working... i cant figure it out :(

3rd... it seems as though feisty fawn doesnt support my belkin F5D6001 wireless card... but the edgy one supported it... im thinking maybe i can set my wireless router to pick up the wireless signal from a different wireless router across the house, and hardwire my computer to the router. ive seen that before. i think i might try that with my xp installation so i can get that problem out of the way.

im sorry if that seems like alot... but im very very very much of a beginner when it comes to ubuntu... any help would be greatly appreciated :)

---

### Post by renzokuken on 2007-06-14
the first problem is easy, just use [Envy](www.albertomilone.com) to install the nvidia driver (or the Restricted Drivers Manager in Feisty.

2nd problme not really sure but remember....google is your friend

3rd problem - ndiswrapper may be needed but it shouldnt be hard, again just search these forums or google for your wireless card make

---

### Post by Tux Aubrey on 2007-06-14
I have the same graphics card and, while I had a few problems initially, it can be done.  As above, Envy should work (download it fom TSeliot's site [_**here**_]("http://albertomilone.com/nvidia_scripts1.html")) - but so should the in-built restricted driver manger (on feisty's System>Administration menu) - I did have to reinstall the restricted-modules after a kernel update but otherwise its no big deal.

No idea about the sound card.

I have two "unsupported" wireless cards (D-Link and netgear) and both work OK with ndiswrapper.

---

### Post by gabkdlly on 2007-06-14
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

This is a good resource.

---

### Post by yasahiro on 2007-06-14
yeah, envy, i remember now... thank you ^_^

and thanks also for the tips on the wireless card :D

now all i need is suggestions for my turtle beach montego DDL optical output...

im so close i can almost feel it... :D

because i know somebody got that sound card to work before under ubuntu...

and i believe it found the chipset c-media something, if im not mistaken, thats the chipset for my sound card

---

### Post by yasahiro on 2007-06-14
okay, i did some reasearching, its the c-media 8768 chipset, i looked on the alsa website, under turtle beach, the montego ddl isnt listed, but under c-media, there is CMI8768... it appears that would be it... buti dont want to dive in and find out it doesnt work :( anybody know if it is?

anyhow, [--Here--]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci") is the page with the instructions.... it seems like i can follow it, just type the commands into the terminal? of course, ill have to download an ubuntu live cd and see if i can get it the things working that can work without actually installing it, before i actually switch over.

anyways, just one more thing i would like to get out of the way...

 is there ntfs support? cuz i have a 150gb ntfs hard drive, about 7/10 filled with movies, music videos, songs, etc. that i dont have another drive to transfer them to. 

again.. any help would be greatly appreciated. :)

---

### Post by borris.morris on 2007-06-14
Yes, NTFS is supported. You can use Automatix2, or I believe that the package is ntfs-3g or something like that.

---

### Post by yasahiro on 2007-06-15
well... here goes

i feel ive researched and went through enough that i can install ubuntu successfully and get it all working, and ive downloaded the 7.04 live cd already... 

so anyways, im going to install it tomorrow night, that way i have 2 days to go exploring and trying to work out anything that dont seem to be working, or stuff i cant figure out.

ill write down the links and information you all gave me, that way i just go in and install it all

thanks again for all your help.. hopefully, thanks to ur help, ill be watching my first movie on ubuntu next week :popcorn:

---


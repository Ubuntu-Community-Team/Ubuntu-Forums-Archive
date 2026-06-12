---
title: "some help to solve my wine problem once and for all......"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-06-24
ok i dont seem to able to get an answer for this problem, which ive had for a couple of months, and ive posted various times and still no answer.
the problem is that wine simply wont run on my system, i can install it fine, but when it comes to running it all i get is a complete system lock, and the only way to get out of it is to press the restart button, this is the only thing that works because the system is rendered totally useless by running anything to do with wine.
ive searched various forums and such like and cant seem to find a solution.
im running fiesty (not the 64bit build) i have an nvidia agp card, an amd athalon 64 bit cpu, and ecs nforce 3 motherboard, a via sound card, im using 2 80gig sata drives, one with ubuntu on and the other as storage (i also have a usb storage drive)
i have found articles that say it maybe the sound card and/or the graphics card that are causing the problem, in which case i wont be able to use wine as i need the graphics card and the sound card, i have also seen that changing to the vessa drivers or something for the graphics may solve the problem, although im not sure how to do this, so some help with that would be appreciated.
the main board does have built in sound, so maybe i should try using that and removing the sound card, but if anyone else has had this problem i would appreciate your input, i only want to try running games with wine as this is all i use windows for (well not now as ive got rid of it altogether, so this is why getting wine to run is important) i know i can use cedega for games, but i have problems with that aswell (ive posted about that in a different thread, "some questions about cedega" or something like)
so any help would be appreciated.
just for the record, i have tried installing wine every way possible and all to the same end, basically the system hard locks when trying to run it, i will try using the onboard sound to see if that helps.
if anyone can help with changing to vessa ill appreciate it, i think it involves re-configuring xorg ? not sure though.
cheers

ok, some im now eating a very large slice of humble pie, i removed my sound card and went into the bios and enabled the onboard sound, and re-booted, the sound worked straight away (this would have been a different story with windows) and i went straight to terminal and typed in winecfg and you'll never guess what happened ? it *#~@/>g worked ! so now all i need is a good how to that tells you how to use it.
cheers from a happy ubuntu user, and fingers crossed this mean no more windows ! which is what ive been working towards.

---

### Post by shifty_powers on 2007-06-24
Well hello mr techno-mole. Good to see you outside of the egosoft forums ;)

Firstly, what version of wine do you have?

```
wine --version
```

secondly, have you considered compiling wine from source, specific to your system? It's actually not that hard. Dependencies can be a bit of a pain sometimes, but still, a good way to learn. Just do:

```
sudo apt-get install build-essential checkinstall
```

and then you can use:

```
./configure
make
sudo checkinstall
```

Once you have downloaded the source. Checkinstall will build a deb file that can be used by your package manager, synaptic, so that it is easier to update and remove in future.

Also, do you have automatix 2? It gives you a trial version of crossover office, by codeweavers to ry out. Might be worth a though ;)

Good to see you here buddy ;)

---

### Post by techno-mole on 2007-06-24
hello there mr shifty_powers, good to see you to.
ive edited my original post because ive got it to work with out hard locking the system, i took out my via sound card and it just worked, ive now got to figure out how to actually use it, was so shocked that taking the sound card out worked i never bothered to find a using wine type how to :D
i have - wine-0.9.39
i did try before to compile from source, but again all it did was to lock the system, until that is i took out the sound card (maybe something wrong with it ) 
i have used automatix in the past, but found it to cause me problems, so i tend to do alot through terminal or synaptic or building from source.
cheers for the help, and its nice to see a familiar face on here :D

---

### Post by Kosimo on 2007-06-24
> **techno-mole said:**
> hello there mr shifty_powers, good to see you to.
ive edited my original post because ive got it to work with out hard locking the system, i took out my via sound card and it just worked, ive now got to figure out how to actually use it, was so shocked that taking the sound card out worked i never bothered to find a using wine type how to :D
i have - wine-0.9.39
i did try before to compile from source, but again all it did was to lock the system, until that is i took out the sound card (maybe something wrong with it ) 
i have used automatix in the past, but found it to cause me problems, so i tend to do alot through terminal or synaptic or building from source.
cheers for the help, and its nice to see a familiar face on here :D


Hello mate, I'm pretty sure we can find out what's going wrong on there.

What is your Mainboard and Chipset ?

---

### Post by techno-mole on 2007-06-24
my main board is an ecs nforce 3 board, the chipset is an nvidia nforce 3 chipset.
i have solved the problem, that is to say i have run winecfg with no problems, i have sound on the system through the on board sound, i took out the pci sound card i was using and wine ran ok.
i need to figure out how to install stuff with it, im trying at the moment to install need for speed undergound 2 but i think i may have to use cedega for games though, because of the difference with direct x and open gl.
from what ive read wine doesnt support direct x ?
cheers for the help though, im ok using the on board sound for now, and to be honest the system does seem to run a little better with out it, so maybe its on its way out ?
cheers

---

### Post by Kosimo on 2007-06-24
> **techno-mole said:**
> my main board is an ecs nforce 3 board, the chipset is an nvidia nforce 3 chipset.
i have solved the problem, that is to say i have run winecfg with no problems, i have sound on the system through the on board sound, i took out the pci sound card i was using and wine ran ok.
i need to figure out how to install stuff with it, im trying at the moment to install need for speed undergound 2 but i think i may have to use cedega for games though, because of the difference with direct x and open gl.
from what ive read wine doesnt support direct x ?
cheers for the help though, im ok using the on board sound for now, and to be honest the system does seem to run a little better with out it, so maybe its on its way out ?
cheers

Well.. As far as I know CEDEGA works much better for me than Wine for games. I'm using it to play starcrat and warcraft III. No problems at all, much faster than wine (but a bit slower than win of course) anyway, perfectly playable. About if wine support directx i guess yes if I'm not mistaken.

---

### Post by shifty_powers on 2007-06-24
[cedega](http://en.wikipedia.org/wiki/Cedega) is actually a proprietary fork of wine, as it goes. And wine most certainly does support emulation of direct x.

As to which is better for games, well you will get many, many opinions of that around here ;)

For me, it depends on the game, tbh. Some things run better in wine, some things run better in cedega. Heard good things about cross over office as well...

---

### Post by Kosimo on 2007-06-24
> **shifty_powers said:**
> [cedega](http://en.wikipedia.org/wiki/Cedega) is actually a proprietary fork of wine, as it goes. And wine most certainly does support emulation of direct x.

As to which is better for games, well you will get many, many opinions of that around here ;)

For me, it depends on the game, tbh. Some things run better in wine, some things run better in cedega. Heard good things about cross over office as well...

If you read my post you'll see I said... Works much better (FOR ME) than wine ;)

For the games I use.

---

### Post by techno-mole on 2007-06-24
ok, ill have to play about with wine for a while, ive just tried to install need for speed underground 2, i got as far as it asking for the second disc, but it wouldnt let me eject the first disc.
a quick question about cedega, does it have any dependencies ? i have a copy floating about, i installed it fine (least i though i had) abnd i tried to install need for speed underground 2, and that went ok, but when i tried to run the game nothing happened, so  i ran it terminal to see what output i got i got the following - 

 /usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
import gddb_parser
F1 2007-06-24 09:38:17,985 WARNING The Cedega version (6.0.2) you are defaulting to is missing the following file : /home/user/.cedega/.winex_ver/winex-6.0.2/.transgaming/config
now im taking it this means it didnt install properly, or did i miss something out ? 
seeing as this is the first time ive been able to mess about with such programs i thought id ask.
since using ubuntu ive found it does what i need it to, with the exception of games, so wine was a way of installing the windows games i had with out the need for a dual boot etc, i dont think theres any programs i would need wine for ? other than games.
so maybe cedega is a better option for me, but only if i can get it to work.
cheers

---


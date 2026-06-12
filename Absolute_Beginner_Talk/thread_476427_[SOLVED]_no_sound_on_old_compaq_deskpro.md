---
title: "[SOLVED] no sound on old compaq deskpro"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by slipperhead on 2007-06-17
i was given an old compaq deskpro en series sff 550mhz 128 mb that was headed for a skip.
i had to install ubuntu by putting its hard drive in my other pc as it has no cd drive so i had a few problems with network and display.
now i can not get the sound card detected despite even compiling alsa (no alsaconf in ubuntu?)
its an onboard sound chip and i cant really even determine what it is.
i have searched the net and there does not seem to be a solution to this.
the sound card is possibly  Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)
(from output of lspci)

does anyone know if a linux driver even exists for this?

---

### Post by weel on 2007-06-17
If lspci thinks it's a DVD decoder, than either it is a DVD decoder, and not a sound card -- or lspci got it wrong, and the information is not particularly useful. Anyhow, with any old soundcard you may want to test your luck and see what happens if you just pretend it's a SoundBlaster. I know I'm not being very helpful ;-)

---

### Post by chemtut on 2007-06-17
I had a similar problem with a compaq armada-------I solved it with a cheap usb speaker!!!!!!

---

### Post by tgalati4 on 2007-06-17
Try:

sudo modprobe snd-sb8

or

sudo modprobe snd-sb16

and see what it says.  Most sound cards in that era supported SB codes.

---

### Post by slipperhead on 2007-06-17
ok, will give that a try, thanks

---

### Post by slipperhead on 2007-06-17
both of those give 

'FATAL: Error inserting snd_sb16 (/lib/modules/2.6.15-28-386/kernel/sound/isa/sb/snd-sb16.ko): No such device
'
was worh a try anyway!

---

### Post by tgalati4 on 2007-06-17
Compaq Deskpros were business machines and the thinking was that they would not be used for multimedia.  Does the motherboard have speaker/Line-in/Line-out jacks?

Do a google search on your model number and see if you can find a Windows driver for sound and that may give you a clue as to the chipset.  Sometimes the documention for the machine will have a features or specifications page that will tout what great sound it has from the UltraHypeMegaSound chip.   Once you find the chipset, then search the forums and you will find some more modprobe hints to try for that particular sound chip.

I assume that you are using Dapper with the 15-28 kernel.  The sound chips on these old machines are part of the ISA bus and sometimes you need to go into the BIOS and turn off Plug-N-Play OS (Linux doesn't understand plug-N-play).  Also turn off (temporarily) the serial ports and parallel ports) to free up interrupts and ports.  This will help with the hardware detection.

---

### Post by slipperhead on 2007-06-17
have just taken the thing apart to see if there are any clues to the sound card.there is a card- creative model ct7230  and there s an ati chip which most of the writing has worn off.

will google and hopefully ome up with something
and will turn of the pnp serial ports and see what happens. thanks for the info

---

### Post by slipperhead on 2007-12-05
just a little update for anyone who might have the same problem-

i put a bigger hard drive and more ram (now 256mb)  in this pc and decided to install fiesty on it just to see how it would do. (and not too bad actually)

it has no cd so i used unetbootin(really impressed with that!)

dapper   had never detected any soundcard so i nearly fell off my chair when i heard the log in drum sound! (considering i had no speakers plugged in!)

sound out of the box!  (built in speaker)

hardware info gives me that the sound card is ESS audio drive ES1869

so i hope this might be of use to anyone searching :)

---


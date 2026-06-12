---
title: "Sound Card"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-28
I Know this isnt exactly about ubuntu, but i accidentally unpluged my sound card from the motherboard (red, white, and black wires) and i dont know where to plug it into. Can someone help

---

### Post by Hobo Joe on 2007-08-28
Take a picture.

All motherboards and soundcards are different, and so we can't really help without a picture.

---

### Post by redfox1160 on 2007-08-28
here are pictures:

[http://www.hibit.it/shopping/foto/big/ga-7vtxe.jpg]("http://www.hibit.it/shopping/foto/big/ga-7vtxe.jpg")
[http://www.terralab.ru/pubimages/27157.jpg]("http://www.terralab.ru/pubimages/27157.jpg")
[http://www.asahi-net.or.jp/~eg5t-stu/mother/ga-7vtxe.jpg]("http://www.asahi-net.or.jp/~eg5t-stu/mother/ga-7vtxe.jpg")

Also, what is the spot it plugs into called (cause i have the manual for the motherboard...)

---

### Post by Hobo Joe on 2007-08-28
I can't tell from those pictures, they're a little small.

The best advice I can give you is either just plug it into a bunch of slots until it works, or take a picture of the thing yourself.

This has happned to me to0, but rather than 3 cables, I had 8, and they all had to be in there exact spots or none of it would work. That's 64 combinations. It took a long time, because I had to figure it out myself. :)

---

### Post by dwhitney67 on 2007-08-28
Look for the J pins in the manual.  'J' stands for jumper.  There are probably some pins on the motherboard that are not connected to anything and that is where the plastic connector you removed connects to.  Should be just two (maybe three) pins.

Btw, the pics you posted were not of much help because they did not contain enough resolution.  Try posting hi-res pics again or just let us know what is contained in the documentation; or just tell us what motherboard you have (perhaps the doc is on the web).

Anyhow, I think you will figure it out.  It is not that difficult (compared to what you went thru earlier!)

---

### Post by redfox1160 on 2007-08-28
MANUAL: [http://www.giga-byte.dk/Support/Motherboard/Manual_Model.aspx?ProductID=1310]("http://www.giga-byte.dk/Support/Motherboard/Manual_Model.aspx?ProductID=1310")
It is a Gigabyte GA-7VTXE motherboard.

EDIT: [http://www.giga-byte.dk/Products/ViewImage.aspx?ProductID=1310]("http://www.giga-byte.dk/Products/ViewImage.aspx?ProductID=1310") (better pic)

---

### Post by dwhitney67 on 2007-08-28
I just realized something... the audio cable from the sound card gets connected to the CD-ROM drive... not the motherboard.  The sound card is already connected to a PCI slot on the motherboard.  ;)

---

### Post by Hobo Joe on 2007-08-28
> **dwhitney67 said:**
> I just realized something... the audio cable from the sound card gets connected to the CD-ROM drive... not the motherboard.  The sound card is already connected to a PCI slot on the motherboard.  ;)

O.o
You must have some crazy hardware if it's hooked up like that!

---

### Post by redfox1160 on 2007-08-28
i think this was hooked up to the motherboard tho...

---

### Post by dwhitney67 on 2007-08-28
> **Hobo Joe said:**
> O.o
You must have some crazy hardware if it's hooked up like that!

It's been awhile since I have owned a desktop (too bulky for my tastes), but that is how the one I used to own was setup.  The sound card receives HDD-stored audio data from the motherboard bus... not some cable.  When playing an audio CD in the CD-ROM drive, then the audio goes directly to the sound card.

Maybe things have changed during the last few years, but that is how I recall my system being set up.  I had an ASUS motherboard.

---

### Post by Hobo Joe on 2007-08-28
I have an Asus, and the soundcard is hooked up to the motherboard. And from the motherboard there is a ribbon cable to the CD drive.
It's a newer motherboard too, I just got it a couple months ago.

---

### Post by redfox1160 on 2007-08-28
so if i plug that into the cd-rom, ill be able to hear the sounds that ubuntu makes when it starts up?

---

### Post by dwhitney67 on 2007-08-28
> **redfox1160 said:**
> i think this was hooked up to the motherboard tho...

Well, if that is the case, then reference pages 10 and 19 of the manual.  I can only think that the audio is going into the motherboard.  Still the need for that baffles me.

---

### Post by dwhitney67 on 2007-08-28
> **redfox1160 said:**
> so if i plug that into the cd-rom, ill be able to hear the sounds that ubuntu makes when it starts up?

I presume you have external speakers (or at minimum headphones) hooked up to the external jack on the sound card.  If so, then you should be able to hear sound.

Of course, this all depends upon Ubuntu's ability to detect and initialize your sound card with the appropriate device driver.  Sometimes this is a walk in the park, other times it can be a nightmare to get a sound card to work (under Linux).

Also, plugging the sound card into the CD-ROM is optional.  It is only if you want to play back an audio CD.  Most folks just rip a CD to MP3s nowadays.  Some folks don't even have music on CDs anymore... I'm one of them.

---

### Post by redfox1160 on 2007-08-28
it worked before, but now it doesnt. (the speakers are built into the computer)

---

### Post by dwhitney67 on 2007-08-28
> **redfox1160 said:**
> it worked before, but now it doesnt. (the speakers are built into the computer)

Ah, hence the reason for the cable.  What kind of cable is it?  Can you locate the PC speaker?  Do the connectors match up?

---

### Post by redfox1160 on 2007-08-28
im not exactly sure, would there be a wire that ran from the card to the motherboard?

---

### Post by dwhitney67 on 2007-08-28
I really do know if I can help you further.  Do you have access to external speakers or earphones (for example from an Ipod)?

Try plugging those into the output jack of your sound card.

As a last resort, do you have the documentation for the sound card?

P.S.  I presume you do indeed have a sound card.  The motherboard you have has a built-in audio chip set.  Many times a chip set similar to yours doesn't meet one's expectations, thus an extra investment is made for a PCI sound card (for instance the SoundBlaster Live!).

---


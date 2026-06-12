---
title: "Sound Juicer"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-21
I still haven't brought my music over to Ubuntu from Windows. I tried Sound Juicer to rip a CD, and it worked fine, only the size of the whole ripped CD was 428MB. I have a lot more CDs, and they can't all be that size.

In WMP, you can choose the bitrate of the copied converted audio files, and I had a nice balance of size and quality. I don't want the music to take up that much room, but I also want somewhat better quality than an .ogg file. Is there another application or file type out there, or maybe a way to increase the bitrate on an .ogg?

EDIT: Or I guess a simpler solution would be to get Rhythmbox to play .wma files.

---

### Post by szf on 2007-02-21
You haven't mentioned which Profile you used when you ripped the CD in Sound Juicer. If it's FLAC, then the file size ~90% of the filesize if the files were simply wave-table (.wav).

I tried (with varying success) to maintain both FLAC and ogg and/or mp3's on my /media mount for versatility. The default .ogg Profile is: *audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.65 ! oggmux*. You can do a [FONT="Courier New"]$ man oggenc[/FONT] in the terminal to learn more options there.

---

### Post by Kateikyoushi on 2007-02-21
Did you rip it to wav ? It is very big for mp3, you could also try goobox to rip cds.

---

### Post by 42Wired on 2007-02-21
I'm sorry, I forgot to mention that I ripped it as flac.

---

### Post by Kateikyoushi on 2007-02-21
In that case it's not so surprising.

---

### Post by 42Wired on 2007-02-21
So do I rip it as wav to maintain quality and small-to-medium size, or is there another way?

---

### Post by szf on 2007-02-21
> **42Wired said:**
> So do I rip it as wav to maintain quality and small-to-medium size, or is there another way?

It depends on your usage. If you plan on playing ripped music from your linux box, then FLAC is a fine choice. By learning which compression ratio in FLAC hits a sweet spot - you'll have to experiment. The upside with FLAC is that it's always *lossless*, with lower file compressions being trivial to transcode back to wave-table. If you plan on transferring to other compys/mp3 players or backing up whole catalogs to CD/DVD, then a lossy format (mp3,ogg,?) may fit the bill.

---

### Post by 42Wired on 2007-02-26
Can I mess with the compression ratio in Sound Juicer? I didn't see anything that would let me.

If not, what's a good ripping program that would allow me to do that?

---

### Post by The Seeker on 2007-02-26
> **42Wired said:**
> If not, what's a good ripping program that would allow me to do that?
I'd recommend abcde. Once you've installed it, take a look at the abcde.conf file (usually found in /etc) and customise to your heart's content.

---


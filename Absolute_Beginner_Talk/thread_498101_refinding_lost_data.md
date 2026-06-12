---
title: "refinding lost data"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by i_pod25 on 2007-07-10
i recently lost all my photos from a mini sd disc  for my phone when i attached it to my computer... they were realli special photos :(... and now there all gone

can anyone please help me find a way to find them if possible :(?


thank you

---

### Post by kidders on 2007-07-13
Hi there,

Linux has a wealth of forensic data recover apps to choose from. Photos in particular should be quite easy to recover, with the following caveats:
[LIST]
[*]Hopefully your camera isn't a really high-spec one that uses raw image formats. I know very little about photography, to be honest, but my instinct is to assume that the word "raw" has the potential to make life difficult for an app that's trying to figure out where one file ends, and the next one begins.
[*]With luck, you stopped using the corrupted SD card immediately. If you reformatted it & started using it again, or made any attempt to write to it, you could be in trouble.[/LIST]
Although there are lots of techniques you can try, I would recommend exploiting the fact that most cameras store images in JPEG format ... assuming that applies to *yours*. You see, the data in these files is very specifically organised, allowing certain recovery apps to identify them quite reliably, even where your filesystem's own organisational infrastructure has been completely destroyed.

**Suggestion: **Don't mess about too much with your SD card. Repeatedly performing sequences of recovery operations on it has the potential to burn it out, or cause further accidental damage. I suggest using **dd** to dump the entire contents of the disk onto your hard drive, and performing any recovery procedures on the disk dump instead. As well as being faster, it'd be safer!

---

### Post by Hendrixski on 2007-07-13
I've used photorec.  just get it from the Ubuntu repositories and point it at the drive you want to recover the pictures from.  Don't forget to specify what file format you want to recover or you'll be over-run with stuff that it recovers,  it's very powerful.

:-)

---


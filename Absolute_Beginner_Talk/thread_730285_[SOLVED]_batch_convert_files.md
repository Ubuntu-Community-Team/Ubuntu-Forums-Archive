---
title: "[SOLVED] batch convert files???"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Nikhil Gohil on 2008-03-20
hi, i didnt know where to post this....so here. anyways, i use mp4tools to convert audio from mp3 to eaac+.```
 aacplusenc inputfile outputfile bitrate
``` . is there any way to batch convert mp3s to aac's using mp4tools? i prefer using mp4tools.

---

### Post by ohzopants on 2008-03-21
You should look into writing a nautilus script for this.  They're pretty easy to write (bash scripts) and you can then do it directly from nautilus.

---

### Post by Nikhil Gohil on 2008-03-21
i dont exactly know how to write a bash script...never touched that part. if anyone could help me here.............

---

### Post by Nikhil Gohil on 2008-03-21
i read somewhere that running a script on a folder convertes all files in that foldes. anyone..........

---

### Post by nick_h on 2008-03-21
I think you need something like:
```
#!/bin/bash
BITRATE=12345
for f in *.mp3; do
	INF=$f
	OUTF=`echo $f | sed "s/.mp3/.aac/"`
	/usr/bin/aacplusenc $INF $OUTF $BITRATE
done

```

---

### Post by Nikhil Gohil on 2008-03-21
thanks for the reply dude.........i copied the code, pasted it in a file and ran it after putting it in the folder i wanted. but it dosent do the conversion. i edited only the bitrate to 56. this is what it gives me........```

*************************************************************
* Enhanced aacPlus Encoder
* Build Feb  9 2008, 15:19:55
* Matteo Croce <rootkit85@yahoo.it>
*************************************************************


Usage:   /usr/bin/aacplusenc <source.wav> <destination.aac> <bitrate>

Use - as filename for stdin and/or stdout.

Example: /usr/bin/aacplusenc song.wav song.aac 32

```

over and over again for as many mp3's are their in the folder. am i doing something wrong?

---

### Post by Nikhil Gohil on 2008-03-22
bump

---

### Post by nick_h on 2008-03-22
It looks like aacplusenc only accepts wav files as input.  You could look for another utility or use lame to convert the mp3 to wav format.
```
#!/bin/bash
BITRATE=56
for f in *.mp3; do
	INF=$f
	OUTF=`echo $f | sed "s/.mp3/.aac/"`
	/usr/bin/lame --decode $INF - | /usr/bin/aacplusenc - $OUTF $BITRATE
done
```

---


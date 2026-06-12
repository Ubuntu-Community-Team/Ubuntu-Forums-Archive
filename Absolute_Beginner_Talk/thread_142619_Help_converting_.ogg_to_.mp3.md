---
title: "Help converting .ogg to .mp3"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by gyga on 2006-03-10
I recently tried to copy a cd to my mp3 player. The extracter (sound juicer) is only able to save as ogg. The problem is my player only does mp3 and wma. Any help on doing this would be appreciated.

I know that I have the codes as I can play mp3s.

---

### Post by dresnu on 2006-03-10
there you go:[http://www.ubuntuforums.org/showthread.php?t=13858&highlight=ogg2mp3](http://www.ubuntuforums.org/showthread.php?t=13858&highlight=ogg2mp3)

---

### Post by gyga on 2006-03-10
Thanks, I had actually just returned to edit my post (I just found it). But thanks any way.

---

### Post by jr.gotti on 2006-03-11
I didn't really look at the date, so I don't know how old this thread is that I'm reviving, but if you want to rip a CD directly to MP3, use abcde.

```
sudo apt-get install abcde lame
``` 
Once that installs, pop in the CD, enter

```
abcde -o mp3
``` 
The program will query freedb, and then proceed to rip your CD to mp3 format.

Edit: Good. As it turns out, this thread is only a day old :D

---

### Post by celloandy on 2006-03-11
Alternatively, if you prefer a gui app that can rip straight to mp3, try goobox.  While the methods described above will convert from ogg to mp3, I strongly recommend against this strategy.  Converting from one lossy audio format to another results in a substantial loss in quality, and your resulting mp3s will sound much worse than if you had ripped them as mp3s directly from the CD/

Andrew

---

### Post by BoyOfDestiny on 2006-03-12
[QUOTE=celloandy]Alternatively, if you prefer a gui app that can rip straight to mp3, try goobox.  While the methods described above will convert from ogg to mp3, I strongly recommend against this strategy.  Converting from one lossy audio format to another results in a substantial loss in quality, and your resulting mp3s will sound much worse than if you had ripped them as mp3s directly from the CD/

Andrew[/QUOTE]

100% true... I shudder to think of those iTunes to cd to mp3s... Seriously... Sometimes it's just nice to boycott...

---

### Post by gdoyel on 2006-03-19
Thank you.

I have been searching forever for some help on this. iPods don't really like .ogg, and I'm in college so I don't exactly have the money to buy a new player that does :-)

---

### Post by ncappel1 on 2006-03-19
In general, you don't want to convert files from one lossy format (ogg) to another (mp3) the process that goes on is that in the conversion, the ogg file will be expanded to a wav file, then recompressed as an mp3. Mp3 and ogg files being lossy (ie, they are compressed) cut out different parts of the wavelengths that are unneeded, resulting in a file that will not sound as good, but problably the change is uncoticable. The change does become noticeable though when it gets uncompressed, then recompressed. 

If you can, you'd be better off reripping your cds into mp3. I know it's not good! if you don't want to do this, you will simply have to live with the awful question "what would my music sound like if it were better quality!?" and it will pester you for ever. ; )

if you do want to go ahead, have you tried using cowbell? or the "audio-convert" nautilus script?

---


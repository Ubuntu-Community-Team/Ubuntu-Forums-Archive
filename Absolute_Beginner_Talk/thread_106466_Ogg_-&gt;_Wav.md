---
title: "Ogg -&gt; Wav?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-12-20
Greetings, my entire collection resides on my external HD (some 7k+ tracks), and they are all in the OGG format.  Now, the cd-players I have around the homestead are all old-school and thus, cannot play ogg.  I have a couple of questions...

1) if a player cannot play OGG must it be converted to something that can? (like mp3 or wav?)

2) short of purchasing a new player that supports OGG is my only option conversion? 

thank!

---

### Post by monchichi on 2005-12-20
I don't understand, are you trying to burn the files into an Audio CD?

Whatever the case, don't convert from ogg to mp3! Converting from one lossy codec to another lossy codec will decrease the quality of your music considerably.

---

### Post by infoburner on 2005-12-20
what kind of cd players are we talking about? can they play mp3 cds?

if they only play standard audio cds, then I think you will have to burn your tracks to a standard audio cd. (we are talking 80 minutes of music per cd max)
to do that, get k3b via 

```
sudo apt-get install k3b
```

and then Applications -> Sound and Video -> K3b
click "New Audio CD Project" and then drag the tracks you want on the cd to the bottom window.

if the cd players will play mp3 CDs, which would allow you to fit many more songs on to each CD, you will have to convert each song to mp3 first because as far as I know there aren't any CD players that will play ogg. first get an encoder.
I use ffmpeg because its easy to use :
```
sudo apt-get install ffmpeg
```

then a short shell script will convert all the tracks in the current working directory into mp3:
```

for item in `ls`
do
ffmpeg -i $item $item.mp3
done

```
then you can use k3b to burn the songs to the CD as a "Data CD Project" instead of audio cd.

Hope this helps!

---

### Post by bionnaki on 2005-12-21
transcoding from lossy to lossy is not recommended, but if you insist on doing it, I recommend soundconverter

sudo apt-get install soundconverter

make sure you have all your codecs, etc installed

---

### Post by garnertr on 2005-12-21
Thanks everyone, I didn't think about burning as MP3... I was thinking old old school.. har har... yes, my players can play mp3... so that will work fine...

thanks for the software sugestions, will attempt later this morning...

thanks for the script, exactly what I'm looking for!!! :)

---


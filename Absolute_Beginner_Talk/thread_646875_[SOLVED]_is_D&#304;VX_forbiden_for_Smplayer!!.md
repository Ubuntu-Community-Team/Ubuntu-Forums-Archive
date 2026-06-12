---
title: "[SOLVED] is D&#304;VX forbiden for Smplayer?!?!??"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by vlaklak on 2007-12-21
[SIZE=3][FONT=Times New Roman][B]Hello Ubuntu People,

I use VLC to watch movies or DVD's, but VLC is not good in subtitle showing.  VLC can'nt show subtitles proberly.

So I am using SMplayer.  But I change my computer to 64-amd.  And I am using 7.10 like before, but Mplayer-Smplayer can't play Divx movies.  

I download some codecs, but it did not help.

What must I do?
[/B][/FONT][/SIZE]

---

### Post by Saahib on 2007-12-21
No help from mplayer.. really ?
May be something missing.. I am able to play divx in it..

---

### Post by mellowd on 2007-12-21
Open a terminal and type this:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by vlaklak on 2007-12-22
[B][SIZE=3]Thanks very much, but it did not help unfortunatly.

Is it about amd-64 or I write ubuntu wrongly.  But I write Ubuntu 3 or 4 times to CDs correctly.  Should I use Fluxbuntu or Easyubuntu.   Because in VLC and Movie Player the divx movies are working but their subtitles don't, but mplayer and Smplayer don't work totally.[/SIZE][/B]

---

### Post by mellowd on 2007-12-23
No, ubuntu should be fine (though if you wanted to install another one, I'd reccomend Mint, it's based on ubuntu)

Once the codecs are installed you should have no problem watching divx's so I'm not sure what's wrong

---

### Post by vlaklak on 2007-12-23
[B][SIZE=3]I can not manage to work mplayer and smplayer, but I manage to put subtitles in Movie Player while playing Divx.

If I take the divx movie in a folder with it's subtitle, Movie Player shows subtitle correctly. But I don't know what if the subtitles need to be delay 1-2 seconds.  

Like the Americans say : "In God We Trust."  :)
[/SIZE][/B]

---

### Post by mellowd on 2007-12-23
Does the application not give you the option of fixing the sync of subtitles?

---

### Post by vlaklak on 2007-12-23
[SIZE=3]No, is it a problem?[/SIZE]

---

### Post by mellowd on 2007-12-23
I don't know, I assumed it was a problem for you?

---

### Post by pissedoffdude on 2007-12-23
Have you installed the proper codecs? Try adding the medibuntu repo ```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```
Then```
sudo apt-get update
sudo apt-get install w64codecs
```

---

### Post by vlaklak on 2007-12-23
[B][SIZE=3]
I download the "w64codecs" using Medibuntu repositories, but things are not change unfortunatly.

Still I can not play "mplayer" and "smplayer".  I think Ubuntu telling me to use original DVD's. :)
But I don't have such a problem while I was using x86 version.  Is it make diffrence between x86 and amd-64.  My computer is AMD X2 3500.
[/SIZE][/B]

---

### Post by rvm4000 on 2007-12-24
That message tells it can't use the video output driver, nothing to do with codecs.

Why don't you run mplayer (not gmplayer) in a console to see the whole mplayer output? 

```
mplayer video_to_play.avi
```

---

### Post by pissedoffdude on 2007-12-24
> **vlaklak said:**
> [B][SIZE=3]
I download the "w64codecs" using Medibuntu repositories, but things are not change unfortunatly.

Still I can not play "mplayer" and "smplayer".  I think Ubuntu telling me to use original DVD's. :)
But I don't have such a problem while I was using x86 version.  Is it make diffrence between x86 and amd-64.  My computer is AMD X2 3500.
[/SIZE][/B]

Hmm, there seems to be a problem with selected video output.  Try opening mplayer>right click>preferences> and under the video options select the second driver xv.  If that doesn't work, try experimenting with the other video outputs.

---

### Post by vlaklak on 2007-12-25
> **pissedoffdude said:**
> Hmm, there seems to be a problem with selected video output.  Try opening mplayer>right click>preferences> and under the video options select the second driver xv.  If that doesn't work, try experimenting with the other video outputs.

[B][SIZE=3]Thanks very much!  Finally I can use Mplayer.  
Thank YOU again and again!!!!!:lolflag::guitar::lolflag:
[/SIZE][/B]

---

### Post by mellowd on 2007-12-26
Excellent, mark the thread as solved :)

---


---
title: "I enabled my multimedia......... Or did I??"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by thunderkyss on 2007-05-20
I followed all the steps from the Sticky up top. Everything looked good. 

After Kubuntu says it unpacked the libraries, it says

Terminal Output:
> Setting up libdvdcss2 (1.2.9-2medibuntu2+build1) ...

Setting up w32codecs (20061022-0medibuntu1+build1) ...



Then puts me back at the command prompt..........

So, did it work??

Well, I put in a CD, with some MP3s on it(ChyrstalMeth, Soulstice, TheiveryCorp, etc...) well, there were some WMAs on it, and they played fine. The Mp3s did not. 

I put a DVD in, it played as an audio CD.

I must have skipped something right??

---

### Post by overdrank on 2007-05-20
> **thunderkyss said:**
> I followed all the steps from the Sticky up top. Everything looked good. 

After Kubuntu says it unpacked the libraries, it says

Terminal Output:



Then puts me back at the command prompt..........

So, did it work??

Well, I put in a CD, with some MP3s on it(ChyrstalMeth, Soulstice, TheiveryCorp, etc...) well, there were some WMAs on it, and they played fine. The Mp3s did not. 

I put a DVD in, it played as an audio CD.

I must have skipped something right??

Hi this link maybe of some help.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Good luck and hope this helps!:p

---

### Post by esoterica on 2007-05-20
I followed those instructions as well and mine seemed to not work also, after some digging I found out that there is an issue when you activate "Desktop Effects" that then causes problems when you go to play DVD's and such. I couldn't figure out how to undo what enabling the Desktop Effects had done so I clicked it again, unchecked both the boxes in it and everything was fixed after that. I've suggested doing the same to other people and it's worked for them as well. Wish there was a note about this in that locked post above with the multimedia steps in out, because outside of the Desktop Effects issue those instructions work perfectly and the errors you receive would never lead you to suspect that as the problem.

If you haven't enabled desktop effects yet then don't or your likely to complicate fixing your specific problem even more, if you have try going into it again, unchecking both the boxes and seeing if that solves your problem.

---

### Post by Iceni on 2007-05-20
For dvd playback:

```
sudo apt-get install libdvdread3
-and-
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by thunderkyss on 2007-05-20
> **Iceni said:**
> For dvd playback:

```
sudo apt-get install libdvdread3
-and-
sudo /usr/share/doc/libdvdread3/install-css.sh
```


output:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.


That second command degraded my version of lpdvdcss2(??) to an earlier version

---

### Post by esoterica on 2007-05-20
People have been pasting in outdated answers when others have asked your same question, the steps degrade your software and don't fix the problem, no harm done though.

Follow these steps, it will replace the downgraded software with the current and it should work assuming you have not enabled the desktop effects...

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just go right through the steps one at a time

---

### Post by thunderkyss on 2007-05-20
[Code:]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29")
> sudo apt-get install libdvdread3 libxine1-ffmpeg

I was missing that last package. Libxine1 -ffmpeg

You've got to run it on a fresh install, and never played a DVD on the system before. 


Thanks for your help guys. 

Now, I need to conquer my mp3 problem. 

It plays .wma files, ogg files, but no mp3s. 

I wonder if my truck will play .ogg files.........

---

### Post by esoterica on 2007-05-21
Keep following those directions and you'll get it working, I just installed absolutely every one of those codecs they referenced and I could find from following those steps. I doubt your car system will play .ogg files, most just recognize .wma and .mp3's from stuff you create off your computer. There is built in software for just making an actual audio CD like you'd buy in the store, but I've never used it before, I just convert everything to .mp3 so it plays on no matter what I want to run it on.

---


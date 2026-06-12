---
title: "XMMS equalizer presets"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-22
Hi, does anyone knows how to get the presets for xmms equalizer if I don't have winamp installed? I also had problems trying to download it from the winamp page. What do I need to do?

---

### Post by goatflyer on 2007-01-22
Winamp and xmms are two different programs.  xmms is a linux workalike to winamp, you don't install winamp, and you don't try to get xmms stuff from the winamp page.

To save presets in xmms, just make sure the equalizer window is open (press EQ button if you can read it), and on the equalizer window press the PS button, and a menu will appear.  Click 'Save' and you will be prompted to save your current equalizer settings.  You can create several presets, and call them what you like: Jazz, Rock, Classical, or Bungawunga.

To select a preset, just choose 'Load' from the equalizer's PS menu.

Hope this helps.

---

### Post by Jorge32 on 2007-01-22
Yes I already know that, it's jsut i wanted to know if I could get those presets because I am not too good for equalizing it myself. so, is there a way of getting or seeing the presets of winamp or quintessential?

---

### Post by ramonev on 2007-01-23
I think you are looking for this:

[http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz)

To install, just unpack the presets and put them on the main folder of your chosen player (so far, xmms, audacious, and the old bmp will work).

ps: got the tip straight from the xmms faq. :)

---

### Post by xmastree on 2007-01-23
> **goatflyer said:**
>  and you don't try to get xmms stuff from the winamp page.Apart from skins. You can get skins from the winamp site which work with xmms.

:guitar:

---

### Post by RebelwithoutaClue on 2008-03-10
I'm obviously being thick, but when I go to [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz) all that's there is text - no files, nothing to unpack.

Sorry for the extreme newbism, but what do I do to get those 'files'?

---

### Post by steveneddy on 2008-03-10
> **RebelwithoutaClue said:**
> I'm obviously being thick, but when I go to [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz) all that's there is text - no files, nothing to unpack.

Sorry for the extreme newbism, but what do I do to get those 'files'?

That's it. Just select save as and browse for the folder.

---

### Post by RebelwithoutaClue on 2008-03-10
Now it's starting to hurt.  I downloaded the file to the desktop and moved it into the audacious folder.  Nice.

I can't get audacious to reference the presets.

OK - so maybe I need to unpack the file.

I can't do it with the browser (access denied) and I can't get to the folder from the desktop terminal - I can't even get out of home.

I also can't find the command line unzip either so even if I got there I'd still be stuck.

This must be like childsplay to you guys, but something so simple is a real pain to do.  It's really frustrating when I'd know exactly what to do in the wintel world.

I can't even find the unpack or extract command  Gnn.

- As a footnote to my toy throwing, I managed to get to the dir but....Doh!

gary@gary-laptop:/usr/share/audacious$ tar -xvf winamp_presets.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

---

### Post by lloyd_b on 2008-03-10
"gunzip winamp_presets.gz"

Lloyd B.

---

### Post by disturbedite on 2008-03-10
> **RebelwithoutaClue said:**
> Now it's starting to hurt.  I downloaded the file to the desktop and moved it into the audacious folder.  Nice.

I can't get audacious to reference the presets.
this was a problem for a long time.  i believe it was recently fixed with audacious 1.4.5 or 1.4.6.  if you're not on hardy then you have a very outdated version of audacious.  gutsy has 1.3.2 & hardy has 1.4.6.

you could request a backport, but it prolly wouldn't happen since hardy's feature freeze is in effect & i would think (i could be wrong tho) backports would be extremely low priority since the new release is so near.

---

### Post by RebelwithoutaClue on 2008-03-10
Confirm 1.3.2 - blimey Help/About is a lot harder to find on Linux!

OK, so continuing on the painful theme...

I downloaded the presets back to the desktop and extracted the presets there.

I then moved it into the audacious dir, fired up audacious again and repeatedly tried to get the app to see the presets to no avail.

The version thing is interesting though becuase I added it through Add/Remove and have repeatedly done the update out of date thing.

Something else to look at I s'pose....

Thanks again tho'

---

### Post by disturbedite on 2008-03-11
just cuz a new version of a program is released does not mean that new version will make into ubuntu.

---

### Post by PinkFloyd102489 on 2008-03-11
> **goatflyer said:**
> Winamp and xmms are two different programs.  xmms is a linux workalike to winamp, you don't install winamp, and you don't try to get xmms stuff from the winamp page.

To save presets in xmms, just make sure the equalizer window is open (press EQ button if you can read it), and on the equalizer window press the PS button, and a menu will appear.  Click 'Save' and you will be prompted to save your current equalizer settings.  You can create several presets, and call them what you like: Jazz, Rock, Classical, or Bungawunga.

To select a preset, just choose 'Load' from the equalizer's PS menu.

Hope this helps.

I beg to differ. Im using my Winamp theme and EQ Preset that I brought over from my XP. Full Bass and Treble. :-)

---

### Post by gigaferz on 2008-03-11
hello

I hope this helps

 How to use winamp presets in xmms

Go tto the faq website @ xmms

right click the link and save as, (if you click you get to a web page with text)

 once in your Desktop (or any other folder)  right click it and select "extract here"

Open the file with a text editor

 Now go to your Home folder, press ctrl+h to view hidden files and folders

go to your .xmms folder and open config

select and copy the presets form the file downloaded 

then go to your config file  lookl for this line "eqpreset_extension=preset" and below it paste all the presets form the other file.

save it and launch xmms and look at the eq, you should see them in there.

edit
:P well thats how i did it the first time, I guess you can just copy the presets from the web site and paste them into your config file

---

### Post by k33bz on 2008-03-11
> **xmastree said:**
> Apart from skins. You can get skins from the winamp site which work with xmms.

:guitar:

not all winamp skins will work

---

### Post by disturbedite on 2008-03-11
> **k33bz said:**
> not all winamp skins will work
true.  modern skins will not work with xmms or audacious.  classic skins are 100% supported though.

---

### Post by jonnylentilbean on 2008-07-19
it's very simple.

run the two following commands:

wget [http://www.xmms.org/misc/winamp_presets.gz](http://www.xmms.org/misc/winamp_presets.gz)
gunzip -c winamp_presets.gz > ~/.config/audacious/eq.preset

They should be there in the presets dialog. There are so many vague "methods" people provide, but this is IT.

---

### Post by legendnz on 2008-07-20
Thanks Jonny, that's the answer we were looking for. There were some long winded ones there. 
 It also possibly needs a restart of the player.
Thanks again.

---


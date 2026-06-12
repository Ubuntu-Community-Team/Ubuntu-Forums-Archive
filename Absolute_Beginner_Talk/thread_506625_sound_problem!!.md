---
title: "sound problem!!"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by wak_maximus on 2007-07-21
i cant hear anything on my laptop...
even the volume is max..

please help me..:(

---

### Post by benx009 on 2007-07-21
when you double click the volume control icon [IMG]http://ubuntu.sabza.org/wp-content/gnome-volume.gif[/IMG], is PCM set on mute???  for some reason, pcm is the actual volume control thingy on my system, not master

---

### Post by wak_maximus on 2007-07-21
no..it not set on mute..
i try using a earphone..
i can hear sound..but the quality is too bad..
maybe because of that i can hear anything on my laptop speaker..

---

### Post by wak_maximus on 2007-07-22
please..can anyone help me??:cry:

---

### Post by envykris on 2007-07-22
u r hardware based volume increase button...can you try revving it up..
also..can you upload a snapshot of your Sound Mixer settings..u can get to that by double-clicking on the speaker icon

---

### Post by LuisAugusto on 2007-07-22
I am not at home, and my laptop charger broke xD so I can't be sure exactly where it is, but:

-Double Click the volume manager.
-Go to settings, there most be one option that aloud you to add options.
-Add the "external amplifier" option
-In the mixer, silence it (the external amplifier).

It should work now.

Hope it helps

---

### Post by wak_maximus on 2007-07-22
> **LuisAugusto said:**
> I am not at home, and my laptop charger broke xD so I can't be sure exactly where it is, but:

-Double Click the volume manager.
-Go to settings, there most be one option that aloud you to add options.
-Add the "external amplifier" option
-In the mixer, silence it (the external amplifier).

It should work now.

Hope it helps

in the volume manager, i cant find where to do the setting..
it only have 3 tabs..File, Edit , Help..
on that tabs, there is nowhere i can find place to do options..

---

### Post by wak_maximus on 2007-07-22
> **envykris said:**
> u r hardware based volume increase button...can you try revving it up..
also..can you upload a snapshot of your Sound Mixer settings..u can get to that by double-clicking on the speaker icon

i will get you a snapshot...
thanks for helping..:)

---

### Post by kvonb on 2007-07-22
This guide should have all the answers you need:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by wak_maximus on 2007-07-22
> This guide should have all the answers you need:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
__________________
My screens..[http://wamrfixit.homeip.net/webshare/feisty/screenshots](http://wamrfixit.homeip.net/webshare/feisty/screenshots)
My system...P4 3.2, nVidia 6600gt, 1gig RAM, 80gig HDD, Leadtek 2000xp TV card (mostly 2nd hand salvaged/repaired parts ).
Reply With Quote

i try that link..
its useful..but my problem doesn't solve yet..
this is my sound driver:
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
i cant find any match on this website like been told on that website..

and i don't have any further steps..because they doesn't find any solutions..

---

### Post by wak_maximus on 2007-07-22
> **envykris said:**
> u r hardware based volume increase button...can you try revving it up..
also..can you upload a snapshot of your Sound Mixer settings..u can get to that by double-clicking on the speaker icon
[IMG]http://img81.imageshack.us/img81/2629/screenshotvolumecontrolbp1.png[/IMG]
This is my snapshot of volume manager..

---

### Post by wak_maximus on 2007-07-22
> **envykris said:**
> u r hardware based volume increase button...can you try revving it up..
also..can you upload a snapshot of your Sound Mixer settings..u can get to that by double-clicking on the speaker icon

[IMG]http://img81.imageshack.us/img81/2629/screenshotvolumecontrolbp1.png[/IMG]
this is my snapshot of sound mixer...

---

### Post by anewguy on 2007-07-22
I'm relatively new at this, too, so if these instructions don't work I'm sorry.  They did work for me and my laptop, though it's not the same as yours.

- with the screen you showed on your last post, click on the "file" tab and then "change device" and select "alsa mixer".  

- click on the "edit" tab and then on "preferences"

- scroll through the list that shows and find "external amplifier"

- click on the box in front of it so that it is checked

- click "close"

- there now will be a "switches" tab - click on it

- in the list that show uncheck "external amplifier"  (I know this seems counter intuitive - adding it in "preferences" only to uncheck it in "switches", but it really did work for me)

- turn all of your sound volumes up all the way

Now try sound.

This worked for me.  I didn't originate it - somebody else has already figured this out and posted it where I found it - I just don't remember the post.:)

---

### Post by wak_maximus on 2007-07-22
[IMG]http://img187.imageshack.us/img187/7444/screenshotvolumecontrolcu0.png[/IMG]
this is the snapshot when i click edit>preferences
no external amplifier..

-sorry for my english-

---

### Post by kvonb on 2007-07-22
On your keyboard, look for a button "FN", usually written in blue.  Also look for a picture of volume up and volume down.

Press "FN" and "volume up", see if it works.

> **wak_maximus said:**
> now i can hear sound..
but it is to slow..
i mean almost not hear anything..
why??

-sorry for my english-

---

### Post by wak_maximus on 2007-07-22
Thanks guys!!
i manage to hear sound now..
i turn the PCM-2 and max the volume..
it works..:)

---


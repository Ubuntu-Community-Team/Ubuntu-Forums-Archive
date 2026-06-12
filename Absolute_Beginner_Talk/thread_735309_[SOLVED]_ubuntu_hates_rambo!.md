---
title: "[SOLVED] ubuntu hates rambo?!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-03-25
ok so first I had problems with first blood part 2 but I figured it out, now first blood I play with VLC and it immediatly goes full screen and I can't get out pus its just black with sound?! I have tried both dvd and dvd simple mode, help?! 



by the way I do not have another dvd on hand so I don't know if this is a dvd specific problem.

---

### Post by Hospadar on 2008-03-25
Have you tried playing this in totem?  do you have all the restricted codecs installed?  How about libdvdcss2?  If you don't have a clue what I'm talking about, let me know and we can make sure you have everything you need installed.

have you ever been able to play other dvds?

---

### Post by chris200x9 on 2008-03-25
yes to both questions....but totem still says codec not found? I'm trying another dvd right now will report back soon.

the codecs were gotten from add/remove programs....should I have done something in synaptic instead?

edit: it's all DVDs.

---

### Post by LowSky on 2008-03-25
no you need the medibuntu repos... copy and paste each command into terminal one at a time and run... instructions are for 32bit Ubuntu if you need 64bit let me know


```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

```
sudo apt-get install libdvdcss2

```

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

```

```
sudo apt-get install w32codecs

```

---

### Post by chris200x9 on 2008-03-25
still VLC goes black with just sound and totem says codec not found.

---

### Post by LowSky on 2008-03-25
did you do all the steps I posted then do a reboot?

---

### Post by chris200x9 on 2008-03-25
I needed to reboot? doh!

---

### Post by chris200x9 on 2008-03-25
so, it worked but I have a new problem as soon as I play it I see the picture for a split second and then it looks like VLC tries to go full screen and my computer restarts? :confused:

---

### Post by LowSky on 2008-03-25
do you have Compiz running it might be messing with your video watching

---

### Post by chris200x9 on 2008-03-25
yes, any suggestions what I should do?

---

### Post by LowSky on 2008-03-25
turn it off, or see if you have an add on called video-something or other turned on... sorry using XP at the moment

---

### Post by chris200x9 on 2008-03-25
weeeeeeeee, I have DVD playback yay :) thank you so much!

---

### Post by forrestcupp on 2008-03-25
If you happen to be using an ATI video card, you can try [this workaround](http://ubuntuforums.org/showpost.php?p=4532372&postcount=10) to get your video working in vlc with Compiz turned on.

I know that's probably not your problem, but just in case.

---

### Post by lila on 2008-03-25
Hello,
I've been following this thread because I've got the same problem - I did all the commands in the terminal and restarted and can now... watch the trailer.  VERY frustrating!  It will only show the film company's little trailer (you know, the lion roaring or Pegasus galloping) I tried several DVDs but they're all the same.  I tried clicking on all sorts of things in the menu (like individual chapters) but no...
And I don't even know what compiz is, so unless it's a default thing I don't think I've got it running.

Any ideas?
Lila:(

---


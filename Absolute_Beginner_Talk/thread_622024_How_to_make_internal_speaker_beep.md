---
title: "How to make internal speaker beep?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-11-24
My little test machine doesn't have a working sound system, but it *is* able to beep its internal speaker when needed.

I use this just when I'm working on my big machine, and I'd like to have my bare-bones xfce4 install be able to beep that speaker when new mail comes in.  The xfce "Mail Watcher" plugin, on the top panel, allows me to give it a command to use whenever new mail shows up, so I'm hoping there is some command which I can plug in there to beep the speaker.

Anybody know of one?  

If I had a sound system, I'd put "aplay something.wav" but I haven't found anything to simply beep that internal speaker.

TIA,
Bob

---

### Post by espressopigeon on 2007-11-24
Try:

echo -e "\a"

---

### Post by PhrankDaChickenGeek on 2007-11-24
or try 'beep' - you can set duration and pitch

sudo apt-get install beep

---

### Post by RTrev on 2007-11-24
> **espressopigeon said:**
> Try:

echo -e "\a"

Ahah.  That should work right at the command line also, correct?  I don't get anything, although "man echo" shows that it should work.  Thanks.. I'm at least on the right path now.  The beep works when I'm in an editor like mousepad and try to do something like backing up past the beginning of the line, but the echo command as written above gives me silence.  If I remove the quotes then I see an "a" appear as I would expect.  Hmm.

---

### Post by RTrev on 2007-11-24
> **PhrankDaChickenGeek said:**
> or try 'beep' - you can set duration and pitch

sudo apt-get install beep

Bingo!  Thanks much!!

Bob

---


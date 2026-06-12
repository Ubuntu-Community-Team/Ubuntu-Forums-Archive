---
title: "No System sounds after startup"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Mikeoak on 2007-10-20
All my other sounds work fine, but after the drum roll for login and the startup sound, I get no more system sounds and no shutdown sound.  I have tried all possible combinations under sound preferences, but have been stumped.  

Since everything else works fine, I suspect it is an easy fix, but not so obvious.  The main thing I miss is the sounds fo Pidgin.  The sound is there when you push the test button, but does not work during message exchange.

Any ideas?

My computer is a Dell Dimensions 2400 with integrated sound.

Thanks

---

### Post by mistergq on 2007-10-20
sounds like something is muted.

go to terminal
type alsamixer
check to see if anything is muted.

oh, and have a cd or mp3 playing while you clicking to see if it turns on! ;)

---

### Post by Steve_Barker on 2007-10-20
Thank You Mistergq

Lost all sound after upgrading, and looked to the forums, after much irritation and failed attempts, for a way to get sound back. Your reply did the trick.

Many Thanks

Steve B

---

### Post by Mikeoak on 2007-10-20
Hmmm, not sure what I am seeing, but  line has MM at the base of the column, also line jack and the second headphone. .  I imagine that MM=muted?  I am able to play a CD and also, I found out that I can get the sounds to play in Pidgin so I am almost there.

---

### Post by mistergq on 2007-10-20
mm is mute.  If you press m, it will turn that option back on.  up and down arrow key controls volume sound.

---

### Post by Mikeoak on 2007-10-20
Thanks, I unmuted the line and that doesn't seem to make much diff.  Unmuting headphone and line jack turns off my mp3 player, LOL.

Anyway, I was happy to find that I could get sounds in Pidgin by enabling sounds to play Always rather than the default when you only get sounds if you are shown as available.:)

---

### Post by magli on 2007-11-04
I am having the exact same problem: everything works accept the system sounds, despite the fact that they can be previewed without a problem.

I also found this thread concerning the same problem:
[http://ubuntuforums.org/showthread.php?t=583452](http://ubuntuforums.org/showthread.php?t=583452)
I will post over there, and continue to watch that thread.

---

### Post by magli on 2007-11-08
This issue was solved in this thread:

[http://ubuntuforums.org/showthread.php?t=583452](http://ubuntuforums.org/showthread.php?t=583452)

I simply had to install "esound", and now all my system sounds are working.

---


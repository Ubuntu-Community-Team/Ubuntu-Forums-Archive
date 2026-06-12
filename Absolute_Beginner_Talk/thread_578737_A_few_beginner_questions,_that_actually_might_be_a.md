---
title: "A few beginner questions, that actually might be a challenge..."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by ChristDude on 2007-10-17
Well, I plan on getting finally getting Ubuntu when the new update is released tomorrow, so here are some questions just to wrap up my decision.

1. Will the Creative Zen V Plus 2GB work with the media player on Ubuntu without having to run any funny terminal codes :D?

2. I've heard that the Broadcom wireless cards normally don't work with Ubunt (along with a lot of other distros), so will the new update possibly change this? I can use a Ethernet connection, but wireless would be preferred.

3. Will Ubuntu be able to play DVDs like any other OS?

4. Is Ubuntu smart from someone who needs to get out of Windows due to lots and lots of errors?

Thanks, and have some popcorn while you're answering.:popcorn::lolflag:

---

### Post by KCPokes on 2007-10-17
I'm only going to speak to number 2, regarding Broadcom cards.  From what I've seen, and experienced, the Broadcom cards do work "out of the box", normally.  That said, the driver is rather flaky and the speeds are limited to "B" speeds.  I ran into the same issue with the Realtek drivers.  My suggestion, for most people, is to go the ndiswrapper route; it just works.  There are cons to going that route but after struggling for months now with the Realtek drivers I finally switched to ndiswrapper and have been wondering why I didn't do it LONG ago.  

Good luck.

---

### Post by hardyn on 2007-10-17
1) try it
2) broadcom arn't the best... but there are work arounds, and if worst comes to worst there is NDISwapper.  again try it
3) with appropriate codecs
4) well its not without its problems... and does require a higher level user, or at least somebody that is willing to learn.  you WILL have to use some command line, not everything will 'just work' you cannot buy the cheap hardware and expect it will work... it is not like windows, it is a different OS.  If you want to learn a little more about computing, are up for a new challenge; yeah its a smart move.

---

### Post by ChristDude on 2007-10-17
> **KCPokes said:**
> I'm only going to speak to number 2, regarding Broadcom cards.  From what I've seen, and experienced, the Broadcom cards do work "out of the box", normally.  That said, the driver is rather flaky and the speeds are limited to "B" speeds.  I ran into the same issue with the Realtek drivers.  My suggestion, for most people, is to go the ndiswrapper route; it just works.  There are cons to going that route but after struggling for months now with the Realtek drivers I finally switched to ndiswrapper and have been wondering why I didn't do it LONG ago.  

Good luck.

Forgive me, yet I didn't really understand any of that. Mind restating that in a way that someone who isn't familiar with Ubuntu would understand? Thanks :-D.

---

### Post by mikeyphi on 2007-10-17
Q3 DVD's - install the appropriate codecs etc and then no probs!
Q4 That's why I switched to Ubuntu!!

---

### Post by Hospadar on 2007-10-17
1) My zen vision M runs great with gnomad or amarok.  you might have to install a library or two (libnjb and libmtp to be specific) but that's real easy to do.  I would assume you'd have no problem.  You can always try it on the livecd first.  The default media player for ubuntu (rythmbox) won't do anything with this however (at least not to my knowledge) amarok is the default kde player and works great, as well as being easy to install with the usual package manager.

2) The issue is that the broadcom chipset is not well specified and broadcom hasn't released any linux drivers.  So while I think some are *possible* to get working, it probably won't be easy.  You could always look into getting an inexpensive usb or pci reciever with a more supported chipset.  That would be my suggestion on the issue as they arn't all that costly.

3) Yes, but you'll need to install some extra stuff because dvd formats and ecryption arn't supported by default for legal reasons.  There are some really helpful guides in the community documentation for getting this working.  Generally you will need to use the [Medibuntu]("http://medibuntu.sos-sts.com/") packages

4) Sometimes a few things can take a little research to get set up, but I've always found ubuntu to be easier and less error prone in the big picture.

---

### Post by LowSky on 2007-10-17
your broadcom card should work but may not be as fast as it could be under windows. there are fixes for it like trying to install the windows drivers using a program called NDISwapper.

hope this helps

---

### Post by oilchangeguy on 2007-10-17
> **ChristDude said:**
> Well, I plan on getting finally getting Ubuntu when the new update is released tomorrow, so here are some questions just to wrap up my decision.

1. Will the Creative Zen V Plus 2GB work with the media player on Ubuntu without having to run any funny terminal codes :D?

2. I've heard that the Broadcom wireless cards normally don't work with Ubunt (along with a lot of other distros), so will the new update possibly change this? I can use a Ethernet connection, but wireless would be preferred.

3. Will Ubuntu be able to play DVDs like any other OS?

4. Is Ubuntu smart from someone who needs to get out of Windows due to lots and lots of errors?

Thanks, and have some popcorn while you're answering.:popcorn::lolflag:

1. run the live cd and see what happens.
2. see above answer.
3. ubuntu will play dvd's now, with the proper codecs installed.
4. not sure what you mean. and most problems with any os are caused by the operator. not the operating system. this forum is full of threads by people who've been tinkering, when they shouldn't. and end up screwing up their computer.

---

### Post by arashiko28 on 2007-10-17
1. Try Amarok or Rythmbox these work with my ipod perfecly fine.
2. go to this post, read and follow directions as told, you won't have any other problems with the broadcom wireless, it worked for me :) [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
3. Install VLC and you'll have no problems, I don't
4. Since root has a restricted access even if you wonder around the files, you cannot modify them or delete them without the permissions. Follow this rule: IF YOU DON'T KNOW WHAT THAT IS, DON'T TOUCH IT! and you'll have no problems:)

Welcome to Ubuntu, sit and enjoy:popcorn:

---

### Post by ChristDude on 2007-10-17
OK, thanks everyone. I'll get the Live CD sometime soon when the update is released. I will be back here every now and then, and I might be able to help out some when I get the hang of it.

---


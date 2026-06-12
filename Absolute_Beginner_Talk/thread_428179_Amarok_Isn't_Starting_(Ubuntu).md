---
title: "Amarok Isn't Starting (Ubuntu)"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by InuyashaDuelist on 2007-04-30
I recently decided that since using Kubuntu wasn't quite using the full experience (and besides, it doesn't work as well on my old machine), that I'd switch on over to Ubuntu. Instead of installing ubuntu-desktop, I pretty much did a full reinstall just for good measure.

So I got in and everything worked fine. The moment I got my backups back into place, and things felt just like before, I was happy. Then the shrugs began.

I couldn't get Yakuake working, because of compatibility problems, so I'm stuck with the default Terminal. This isn't that bad, I guess, since I can just click on it on the panel up top, but this was just one of my two main problems with switching to Ubuntu.

My second biggest problem thus far is that, frankly, I use Linux mainly for Amarok. If Amarok doesn't work, there's no humongous reason for me to use Linux. I got Amarok installed (even though it had to put in the darned KDE libs), and got it to open. I fixed my preferences to what I enjoyed, and imported my freshly backed-up media library. I attempt to play a song, and the following happens, in this order:

Some sort of message, possibly the no-mp3-support message attempted to pop-up, but failed, and froze Amarok. I closed it and tried opening it again. It opened fine. I tried to play the same song, and it got to the point where it was adding the song to the playlist when it got stuck at 100% and froze. I closed it. I tried re-opening it once more, but it wouldn't open this time. I tried reinstalling, and it wouldn't open. I tried purging and reinstalling, and it wouldn't open. I tried running it from the terminal, and it didn't do anything at all (literally. I typed in "amarok" and pressed enter, and it just sat there, not doing anything).

I tried Exaile, since it was supposedly the Amarok clone for GNOME, but the fact that it lacks an informative sidebar, global hotkeys, a good OSD, and a lot of preferences made me just not go for it.

I'd really hate to have to switch back to Kubuntu so soon. Is there anything I could do to get Amarok working?

Thanks in advance.

---

### Post by pommattski on 2007-04-30
> **InuyashaDuelist said:**
> ... and it got to the point where it was adding the song to the playlist when it got stuck at 100% and froze. I closed it. I tried re-opening it once more...

I had exactly the same problem.
It turned out to be a missing xine player library or something.

Edit: Just checked: The one to look for specifically is libxine-extracodecs and you should find that amarok-xine is already installed.

---

### Post by InuyashaDuelist on 2007-04-30
Just got those installed, but it still won't open.

---

### Post by Narcoleptic_Insomniac on 2007-04-30
> **pommattski said:**
> I had exactly the same problem.
It turned out to be a missing xine player library or something.

Edit: Just checked: The one to look for specifically is libxine-extracodecs and you should find that amarok-xine is already installed.

I also have this problem and I tried your idea but it didn't work. For me it's freezing just as the Amarok window opens but the splash window doesn't go away, and then I can't do anything except force quit. Both that library and amarok-xine are installed.

---

### Post by InuyashaDuelist on 2007-04-30
It seems that a little restart temporarily fixed the problem. I expect the problem to occur again, though.

---

### Post by pommattski on 2007-04-30
(just remembered...) Make sure that you have libxine1-ffmpeg installed also.  
I did find that a restart was required as well - but it hasn't crashed or hung since then.

Hope it works for you!

---

### Post by InuyashaDuelist on 2007-04-30
Thanks, very much.

And I also found a decent GNOME clone for Yakuake, Tilda. Looks like my problems are pretty much fixed thus far. :D

---


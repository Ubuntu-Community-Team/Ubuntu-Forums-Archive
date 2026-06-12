---
title: "Running WinAmp"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-04
I read a post that a user got WinAmp to work using wine.  Can you give me some pointers about making this work?  I've never used wine.  WinAmp is about the only thing left in w2k that I'd like to have.

Thanks,
bobland

---

### Post by jbonll05 on 2007-05-04
It's not Winamp, but have you tried the xmms player,  it plays Shoutcast, Live 365, etc. I use the Beep Media Player with it. Other players also work. Xmms is in the repo's where you can read a brief on it.
JB, Ubuntu user

---

### Post by Boztech on 2007-05-04
Just use xmms, it is nearly identical to Winamp 2.x for Windows, even the menu layout.

---

### Post by Iokua on 2007-05-04
Personally, I can't stand xmms. 

I do however absolutely love Amarok. I actually prefer Amarok over Winamp because Winamp constantly bugs me to update it and has a number of other annoyances.

---

### Post by BobLand on 2007-05-04
Where are these players located?  Where are the repos?

---

### Post by Burnspot on 2007-05-04
> **BobLand said:**
> Where are these players located?  Where are the repos?

I do believe you can get most of them through the Add/Remove function under "Applications"...just set your filter to show all available.

---

### Post by powder on 2007-05-04
XMMS and Beep Media Player have been obsoleted by Audacious.

sudo apt-get install audacious audacious-plugins-extra

---

### Post by Iokua on 2007-05-04
> **BobLand said:**
> Where are these players located?  Where are the repos?

I installed Amarok from the medibuntu repository: 

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

### Post by powder on 2007-05-04
> **Iokua said:**
> I installed Amarok from the medibuntu repository: 

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Amarok is not in medibuntu.  He would also need to import the GPG key for those repos to work in the first place.

---

### Post by K.Mandla on 2007-05-04
> **powder said:**
> XMMS and Beep Media Player have been obsoleted by Audacious.

sudo apt-get install audacious audacious-plugins-extra
+1! I started using Winamp at something like v1.2 or something, so Audacious is perfect for me. I don't care for multimedia management suites. Just play the music. :D (Of course, I mostly use cplay nowadays, but it's not really anything like Winamp.)

---

### Post by moore.bryan on 2007-05-04
> **powder said:**
> XMMS and Beep Media Player have been obsoleted by Audacious.

sudo apt-get install audacious audacious-plugins-extra

*what makes audacious better than xmms?*

---

### Post by jfinkels on 2007-05-04
If you want information on installing software, look here! [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

XMMS is almost identical to winamp, as said by a previous poster. To install it, type the following in the terminal:
```
sudo aptitude install xmms
```

However, you should also try out other music players as suggested by other esteemed members of the community here. Linux is freedom of choice.

---

### Post by K.Mandla on 2007-05-04
> **moore.bryan said:**
> *what makes audacious better than xmms?*
It doesn't use GTK1.2 for one thing, so it looks a lot prettier in the submenus and selection dialogs. But I also think it has better support for some sound types; I seem to remember reading that somewhere, but it might not be 100 percent true. And it has a way cool pop-up tooltip that shows the album cover!! 

:shock: :mrgreen: :lolflag:

---

### Post by moore.bryan on 2007-05-04
> **K.Mandla said:**
> It doesn't use GTK1.2 for one thing, so it looks a lot prettier in the submenus and selection dialogs. But I also think it has better support for some sound types; I seem to remember reading that somewhere, but it might not be 100 percent true. And it has a way cool pop-up tooltip that shows the album cover!! 

:shock: :mrgreen: :lolflag:

*gotcha... none of those things are particularly important to me, so i'll stick with xmms; thanks!*

---

### Post by powder on 2007-05-04
> **moore.bryan said:**
> *what makes audacious better than xmms?*

Nothing, if you're still living in 1999.

---

### Post by Malibu Illusion on 2007-05-04
Chalk up a vote for amaroK.  Great player, great functionality.  I'm another one who'd favor it over WinAmp itself. ^^

Take care.

---

### Post by moore.bryan on 2007-05-04
> **powder said:**
> Nothing, if you're still living in 1999.
[I]as if there's something wrong with '99?  prince thought it was the party year...
;-)
[/I]

---

### Post by BobLand on 2007-05-04
I mostly look at the videos in Winamp.  The players recommended here appear to be music players.  How would I reach ShoutCast?  Are there lists like in Winamp?

Thanks,
bobland

---

### Post by Iokua on 2007-05-04
> **BobLand said:**
> I mostly look at the videos in Winamp.  The players recommended here appear to be music players.  How would I reach ShoutCast?  Are there lists like in Winamp?

Thanks,
bobland

Ahh, video. For video I just use VLC or MPlayer. As for shoutcast, Amarok has a list of shoutcast channels just like Winamp does.

---


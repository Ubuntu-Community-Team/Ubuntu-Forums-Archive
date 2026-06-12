---
title: "Firefox beta crashes X?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by bardic on 2008-04-10
I'm not sure if this is exactly what is happening but I think so. Sometimes when I minimize Firefox (3 beta 5) it seems X is crashing. It goes to terminal and after a second or two, I goes back to the login screen. 

How can I find out if it's FF causing this and report this as a bug?

---

### Post by joshrobinson on 2008-04-10
> **bardic said:**
> I'm not sure if this is exactly what is happening but I think so. Sometimes when I minimize Firefox (3 beta 5) it seems X is crashing. It goes to terminal and after a second or two, I goes back to the login screen. 

How can I find out if it's FF causing this and report this as a bug?

mine used to do that, but it hasnt in a good while. i wasnt sure if this was due to firefox, flash, xserver, or my ati drivers
i dont have much to say that can help, but i can confirm the issue

---

### Post by coolen on 2008-04-12
I've experienced this, too, somewhat more frequently. It happened to my brother's computer as well.

Both using nVidia cards, he's on the old drivers (as in, for older cards), so I don't think it's a driver issue.

I'm using non-free flash, with PulseAudio (requires a slightly experimental library to work with PulseAudio), but my brother doesn't use PA. We're both running 2.0.0.13, although I do have beta 4 installed, but he does not.

We're both using Compiz, with AWN and Screenlets. I've disabled AWN for now, and see if the problem pops up again.

---

### Post by markekeller on 2008-05-03
I've got the same problem; only I'm using Firefox 2 and Gutsy (Linux Mint edition).  I also use Compiz, perhaps that could be what's causing the problem?  It's awfully annoying, whatever it is.

---

### Post by tnmarktx on 2008-05-03
> **bardic said:**
> I'm not sure if this is exactly what is happening but I think so. Sometimes when I minimize Firefox (3 beta 5) it seems X is crashing. It goes to terminal and after a second or two, I goes back to the login screen. 

How can I find out if it's FF causing this and report this as a bug?


Not having the same exact problem, but this version of FF seems to be very buggy.  Hopefully they will have an update soon.  I have an inspiron 1525n with intel integrated graphics and have no x server crashes in ubuntu 8.04.  But, I do have problems with the sound.  If I am listening to some music in rythmbox and pause it to watch some streaming video in FF, I get no sound till I close rythmbox and restart FF.  Go figure.

---

### Post by coolen on 2008-05-04
Your problems with sound are likely related to Flash. The nonfree Flash in Hardy (like previous versions) does not use PA. If you start using Flash, it'll hog the sound card, and Rhythmbox seems to freeze upon this.

---

### Post by coolen on 2008-05-04
I'm pretty sure it is an issue with Compiz. I've been on Hardy for over two weeks now, and I haven't seen it. Whichever was causing the crash (Compiz or Firefox), it seems to have been fixed in Hardy (remember that Hardy uses beta 5 Firefox).

---

### Post by bvanaerde on 2008-05-07
X crashes when I visit [http://ubuntuguide.org](http://ubuntuguide.org)

I'm on Hardy, using Firefox 3 beta 5
It also happens when I disable compiz...

---

### Post by coolen on 2008-05-08
Works fine for me, same software.

What graphics card do you have? Drivers? I'm assuming you're using the Ubuntu derivative, correct me if I'm wrong.

Not that I have a clue why this is happening, but narrowing it down helps with the Google search.

---

### Post by bvanaerde on 2008-05-08
I'm using the restricted nVidia drivers, those were proposed by my Ubuntu installation (so no manual install).

These drivers seem to be the problem though.
More info can be found on [launchpad]("https://bugs.launchpad.net/ubuntu/+bug/219866").

---

### Post by coolen on 2008-05-08
Well, I'm using the nvidia drivers included with Ubuntu (which defiitely seem to be the source of the problem), and I'm not having this problem.

Seems strange that the Envy installed version produces this behaviour, yet the drivers installed directly from Nvidia do not.

Still, it seems that upgrading your drivers, or using theirs, will likely solve the issue for you.

---

### Post by jimmy the saint on 2008-05-09
ubuntuguide.org crashes mine too.  I saw another thread about an anime wallpaper site crashing ff and gnome the same way.

---

### Post by loserboy on 2008-05-09
[http://ubuntuforums.org/showthread.php?t=785560&highlight=FF+issues+firefox+crashes](http://ubuntuforums.org/showthread.php?t=785560&highlight=FF+issues+firefox+crashes)


maybe helpful?

---

### Post by coolen on 2008-05-10
libflashsupport was only included in the beta releases of Hardy, I believe. It was never necessary in earlier versions, and was removed from the final release due to stability issues (which are made obvious in that thread).

That fix for libflashsupport at the end looks intriguing, though. The PA issues with flash have been bugging me ever since the upgrade. It'd be great if they could fix it for 8.04.1

---

### Post by jimmy the saint on 2008-05-16
I did a little research at launchpad and there is a fix available in the Hardy-proposed section.  It seems it is due to some error in the packaging process for the Video drivers and only affects 8*** series nvidia cards running the Nvidia drivers.  I will attempt the fix and post later this evening or tomorrow and fixit guide for people like me who have difficulty with the developers explanations!

---


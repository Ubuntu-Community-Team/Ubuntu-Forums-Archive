---
title: "Media Player Buttons"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by original_jamingrit on 2007-05-23
Hi,
On the side of my laptop keyboard, I have some extra buttons, normally intended for music and video players.  I don't want a full explanation, I just wanted to know how to get started, and make sure I can detect these buttons, and if anyone's seen a tutorial on this sort of thing a link would be appreciated as well.  Also, if I mapped them to a script or macro or something, would I have to do that once for each button, or would I have to do it for each player and each media player(Amarok, Totem) I use as well?

Thanks

---

### Post by Iokua on 2007-05-23
> **original_jamingrit said:**
> Hi,
On the side of my laptop keyboard, I have some extra buttons, normally intended for music and video players.  I don't want a full explanation, I just wanted to know how to get started, and make sure I can detect these buttons, and if anyone's seen a tutorial on this sort of thing a link would be appreciated as well.  Also, if I mapped them to a script or macro or something, would I have to do that once for each button, or would I have to do it for each player and each media player(Amarok, Totem) I use as well?

Thanks

Do you have Ubuntu installed? If not, I suggest booting into a LiveCD and going to Settings -> Preferences -> Keyboard shortcuts. Then try pressing a few of those keys to see if Ubuntu recognizes them as keyboard keys. If so, you shouldn't have any problem mapping them to whatever you want.

---

### Post by drowner on 2007-05-23
I have a USB keyboard with these buttons.... they work perfectly with rhythmbox (which i am starting to become really fond of).

There is a keyboard shortcuts app in the menu which you could program them to do what you want.

---

### Post by original_jamingrit on 2007-05-25
Yes, I already have Ubuntu Feisty installed and running properly.  I looked through the Keyboard shortcuts window and it was unable to detect any key presses when I hit the media buttons, and they don't show up as anything in the terminal either.

Also, I looked through the Keyboard Settings, and couldn't find anything else helpful.  I'm using a Toshiba Satellite M40, and my keyboard layout was set to Generic 105-Key Intel, and the only Toshiba layout was something like S3000, but I found no improvements when I chose that (I simply switched back after trying that).

Even when I was running this machine with windows xp, I had difficulty configuring these little buttons to do what I wanted.  The user's manual hasn't given me any special insight.  I do suspect that the buttons are not directly connected to the keyboard and may be considered some sort of alternative input.

I'm not sure how to proceed, is there any terminal commands I could use to search for these buttons, or to wake them up some how?

---

### Post by rax_m on 2007-05-25
I have a Toshiba P100-429 (UK spec) and these buttons work perfectly using Rythmbox :) 
BTW I'm using XFCE if that makes a difference..

---

### Post by ske1fr on 2007-05-25
Have a look at **[ the MultimediaKeys page.](https://help.ubuntu.com/community/MultimediaKeys)**

---

### Post by original_jamingrit on 2007-05-25
> **ske1fr said:**
> Have a look at **[ the MultimediaKeys page.](https://help.ubuntu.com/community/MultimediaKeys)**

That's exactly what I needed.  I may have to fiddle around with the touchkey editor program, but it can at least detect my multimedia button presses.  I should be good with it for now, and I'll post again if everything works out.  Thanks!

---

### Post by Dougle on 2007-05-25
Media keys work great using Prefs->Keyboard shortcuts but only if your using the default player, is there a way to direct the shortcuts (and essentially change the default player) to another player such as XMMS?

xbindkeys is coughing up errors like "cannot catch key presses, another process is listening"

Dan

---


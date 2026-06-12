---
title: "Preffered application multimedia"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Jim_in_Germany on 2008-04-13
Hi,

Does anyone know how to change the preferred application for multimedia. I want to play mp3s with the vlc player, not the standard Rhythmbox / Totem players.

I tried going to System -> Preferences -> Preferred Applications, but in the  dialogue box that then opens I can only choose between  Rhythmbox / Totem and "custom".

When I select custom, nothing happens.

Grateful for any help

---

### Post by mikeyphi on 2008-04-13
Having entered 'Custom' Have you then entered anything in the 'Command' box? - perhaps 'vic'

---

### Post by Jim_in_Germany on 2008-04-13
Yup, tried vlc & vlan. Couldn't think of anything else.
I think that this is along the right lines though

---

### Post by kwacka on 2008-04-13
2 possible solutions - I don't know which one works, I tried both at the same time.

Instead of 'vlc' in preferred applications try 'wxvlc'; and/or right-click on the file and select the 'open with' option, choose vlc.

---

### Post by Jim_in_Germany on 2008-04-14
Cheers for the replies.
Unfortunately adding "wxvlc" in the custom box didn't work.
I can always open the mp3 with a right click and the option "open with VLC media player" but it would be nice if I didn't always have to do that.

---

### Post by forrestcupp on 2008-04-14
Try right-clicking an mp3 and choose Properties, then click the Open With tab and see if vlc is in there.  If so, choose that and mp3's should open with vlc from then on.

It's strange that **wxvlc** didn't work though.  That command opens vlc from the terminal.  You didn't add the quotes did you?

---

### Post by Jim_in_Germany on 2008-04-14
Yay, it worked!
Thanks a lot.
I used the second solution mp3 -> properties -> open with -> vlc

I can run vlc from the terminal with the command wxvlc
I didn't use the quotes and entered this into the custom box under prefered applications -> multi media.
I tried this with and without the "run in terminal" box checked.

Bizarre, but never mind as the problem is solved.

Cheers

---


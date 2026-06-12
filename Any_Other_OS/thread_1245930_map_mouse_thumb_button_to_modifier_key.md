---
title: "map mouse thumb button to modifier key?"
date: 2009-08-21
forum: Any Other OS
---

### Post by bluerabbit4210 on 2009-08-21
Hi all, hopefully this is in the right forum.

Simply put:  Is there a way to map a mouse button to a modifier key?  I've got a thumb button (button 9) on my mousie and I've been trying to map it to Shift_L (or whatever) and am having no luck.  I've been able to find very little information on the subject.  
So far I've been hammering out different combinations of xbindkeys and xte to a limited effect.  xev reports that button 9 is sucessfully remapped as Shift_L (it can be used while typing, but thats not the goal) as long as I don't use any other mouse buttons while its down.  basically what im seeing in xev is this:

KeyPress Shift_L (as i press button 9)
...
ButtonPress button 4  (wheel up)
ButtonRelease button 4
...
ButtonRelease button 9 (as i release button 9)

Net result is i'm left with a pseudo-capslock until i send another KeyRelease Shift_L (either keyboard or mapped button 9).  again, as long as I avoid other mouse buttons while i'm holding button 9, releasing it sends a KeyRelease Shift_L.  I've tried catching release+b:9, shift+release+b:9 and all sorts of other stuff.  Is there something I'm not seeing with regards to how x handles simultaneous mouse input?  Something else entirely?  I'd really like to be able to Shift+MouseWheel without touching the keyboard.

Thanks in advance!

btw, i'm running Mint 5 (hardy)

---

### Post by insub2 on 2009-09-03
Try btnx.

Not that you'll need it but here is a step-by-step:
[LIST=1]
[*]Go to synaptic and install btnx (it will have a couple of dependencies).
[*]It should show up under System->Preferences (I'm on Xubuntu, so I may be wrong).  Or if you have GnomeDo, just Win+Space and start typing "btnx".
[*]Click "Detect mouse & buttons" then follow the instructions.
[*]Go to the button tab and set your thumb button to a shift key.
[*]Go back to the Configuration tab and click "Restart btnx".
[*]Enjoy.
[/LIST]

---

### Post by bluerabbit4210 on 2009-09-05
Thanks for the tip!

On first glance, it doesn't appear that btnx will allow me to map a button to *just* a modifier.  I also remember reading somewhere that the mouse handling in x simply does not allow for simultaneous mouse buttons, but i'm happy to be corrected on this one.

it seems like i'm gonna have to roll up my sleeves and patch evdev if i want this one to work!  (not that i have anywhere near that kind of ability...)

Thanks again!  I'll keep trying nonetheless!  :D

---

### Post by insub2 on 2009-09-05
> **bluerabbit4210 said:**
> Thanks for the tip!

On first glance, it doesn't appear that btnx will allow me to map a button to *just* a modifier.  I also remember reading somewhere that the mouse handling in x simply does not allow for simultaneous mouse buttons, but i'm happy to be corrected on this one.

it seems like i'm gonna have to roll up my sleeves and patch evdev if i want this one to work!  (not that i have anywhere near that kind of ability...)

Thanks again!  I'll keep trying nonetheless!  :D

umm...I'm using btnx to have my thumb button cycle workspaces.  But I went in a set it up just to be left shift.  Opened up Gimp and tried it out.  It worked fine.

---

### Post by bluerabbit4210 on 2009-09-05
Well hot damn!  I stand corrected!  Don't ask me what was different when I tried it this afternoon, but it works beautifully now.  Thanks for that follow up, it was just the push I needed to retrace my steps, eh?

Big ups!
-br

---

### Post by apasnuy on 2012-08-05
For Ubuntu 12.04 works flawlessly

[http://forum.pinguyos.com/Thread-HOWTO-Mouse-buttons-to-change-workspaces-in-gnome-shell]("http://forum.pinguyos.com/Thread-HOWTO-Mouse-buttons-to-change-workspaces-in-gnome-shell")

---

### Post by Perfect Storm on 2012-08-06
Very old thread.

Closed.

---


---
title: "Ubuntu Applications Menu"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by kelinu on 2008-02-25
Hi,

I'm still quite new to Ubuntu, so please bear with me.  On Ubuntu Gutsy Gibbon, there is the Applications menu at the top yes? Well, when I install new packages, in this case Avast 
Home Antivirus, it doesn't appear on the applications menu! (this happens with some other programs too)  Is this normal?  And is there a way to get a shortcut to Avast etc. on the Applictaions Menu?  This would be very convenient because I wouldn't have to stay looking through usr/... and finding where the program file is every time I want to launch it.

Thanks,
Mike:KS

---

### Post by neurostu on 2008-02-25
try typing ```
 $avastgui 
``` in a terminal that should bring it up.

Or you can right click on a panel, click add to this panel, click Custom Application launcer then name the app whatever and for command type avastgui

---

### Post by kelinu on 2008-02-25
OK thanks the terminal thing didn't work for me but I managed to do the shortcut on the panel :)

---

### Post by northern lights on 2008-02-25
Great you've got the shortcut/launcher working.

At the side, lemme ask a question though - why do you wanna run some antivirus app? Hope you're not planning on having it constantly in the background, all its gonna do is hog resources (even if it's not many - what's the point)?

---

### Post by Delkster on 2008-02-25
> **kelinu said:**
> OK thanks the terminal thing didn't work for me but I managed to do the shortcut on the panel :)

If you don't want to spend panel space on it and would like to have it in the Applications menu instead, you can right-click on the menu and select "Edit Menus". There you can move, hide, delete and add new items where you would like them on the menus.

Also -- and sorry if you already knew this -- in the terminal command the dollar sign ($) at the beginning usually isn't supposed to be typed. It's just often shown there in examples to denote the command prompt.

---

### Post by neurostu on 2008-02-25
> in the terminal command the dollar sign ($) 

thanks for posting that, sometimes I forget to add that note...

---

### Post by kelinu on 2008-02-25
Hi guys,
Thanks for all this...I'm installing antvirus so that I can download stuff on Linux that is for windows...then if it has a virus i delete it and if it doesnt i move it to windows...(sometimes  i use windows but now more ubuntu)

---

### Post by Syndacate on 2008-02-25
> **kelinu said:**
> Hi guys,
Thanks for all this...I'm installing antvirus so that I can download stuff on Linux that is for windows...then if it has a virus i delete it and if it doesnt i move it to windows...(sometimes  i use windows but now more ubuntu)

You use a UNIX based system now, man, viruses aren't really coded for them.  That's why macs and Linux have it so easy when it comes to virus protection.

It's not like Windows where you need to protect yourself 6 ways from Sunday with all the anti-virus and firewall crap you can get your hands on, you're pretty much set from the start.

---

### Post by kelinu on 2008-02-25
yeah i kno but some programs that i love dont work on linux, so i have windows installed too

---

### Post by northern lights on 2008-02-25
Other than Photoshop, which **is** more powerful than the GIMP (Hooray for Blending Options), what is it you can't find suitable equivalents for?

---

### Post by kelinu on 2008-02-25
Oh i can't mention them all here...I have dreamweaver, google desktop, a few games that i play, QBASIC, etc.

---

### Post by sayakb on 2008-02-25
> **kelinu said:**
> Oh i can't mention them all here...I have dreamweaver, google desktop, a few games that i play, QBASIC, etc.

You may have QBasic on DOS emulator... Also, why do you need google desktop for? Is it about the sidebar? I think you should try screenlets (a wise replacement to google desktop)

```
sudo apt-get install screenlets
```

---

### Post by kelinu on 2008-02-25
ok thx ill try this out...I'm still keeping windows on my pc tho for some games etc + my brother uses the same pc (we share it - i kno, it's stupid) and he wont even go near linux!:)

---

### Post by kelinu on 2008-02-25
oh by the way....do dos emulators even existfor LInux?

---

### Post by seventhc on 2008-02-25
> **kelinu said:**
> Oh i can't mention them all here...I have dreamweaver, google desktop, a few games that i play, QBASIC, etc.
google desktop works in linux
[http://desktop.google.com/linux/](http://desktop.google.com/linux/)

---

### Post by kelinu on 2008-02-25
yea i know but u cant add gadgets to it on linux

---

### Post by Delkster on 2008-02-28
> **kelinu said:**
> oh by the way....do dos emulators even existfor LInux?

Yes, for example Dosbox (which you can find for Ubuntu from Add/Remove Applications). It's a true emulator, though, emulating also pretty much all relevant hardware from the CPU to the graphics card, so it's quite slow. Should be okay, though, if you aren't going to run anything particularly demanding. QBasic etc. don't have almost any performance requirements and will probably be okay (never tried), and some old games also work pretty nicely. Running Dosbox on a modern machine should give approximately the speed of a 386 PC or so.

---


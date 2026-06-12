---
title: "missing buttons in the windows"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ken-kenshin on 2007-11-15
hi a lot of my windows buttons have diapered the minimize and maximize buttons are not on my windows to get out of them i am useing the 7.10 ubuntu desktop 
and my terminal is not working ether it just i a white box what can i do about this what will fix it 
i just install 7.10 and it was working before it started when I installed wine a few days ago

---

### Post by Qwerty_ on 2007-11-16
So you installed 7.10. Everything was working fine then it all starting messing up?

---

### Post by ken-kenshin on 2007-11-16
yas was bout a few day after i installed wine

---

### Post by unprinted on 2007-11-20
I have this too, following the /home partition being - according to 7.10 - 100% full. (If I booted into Windows and looked at it with ext2fs, it thought it had several gigabytes free, but that's another post!)

If I change the session to 'default GNOME' in the login screen, the buttons and window edges are as usual.

Back to the standard session, gone again.

Setting the theme to something definitely with buttons doesn't work.

---

### Post by Inxsible on 2007-11-20
> **ken-kenshin said:**
> hi a lot of my windows buttons have diapered the minimize and maximize buttons are not on my windows to get out of them i am useing the 7.10 ubuntu desktop 
and my terminal is not working ether it just i a white box what can i do about this what will fix it 
i just install 7.10 and it was working before it started when I installed wine a few days ago
in the terminal, type in```
metacity --replace
``` I know your terminal doesnt have borders, but you can type in it correct?

---

### Post by unprinted on 2007-11-20
> **Inxsible said:**
> I know your terminal doesnt have borders, but you can type in it correct?

Not here - it's literally just a white rectangle, no text visible, and typing things that should get a response (e.g. a gui program name + return) don't.

It should be possible to do this in another session, and if necessary set up a shortcut to run a shell script with it in the faulty default session though.

---

### Post by DutyDuty on 2007-11-20
Try ```
metacity --replace
``` in Alt+F2. Then you can run ```
emerald --replace
and 
compiz --replace &
```
to try and start compiz right.

---

### Post by unprinted on 2007-11-21
That works, thanks, but it's not 'permanent' - the buttons disappear if I log out and log back in again.

Where is the session info, including which window manager to use, stored?

---

### Post by unprinted on 2007-11-21
I've cheated(?) and reinstalled 7.10 from CD. It works now...

---

### Post by zignego on 2007-11-21
I had a similar problem. My windows always defaulted to the upper left corner when I opened them and I couldn't move them because the top bar was off the screen. CODE: metacity --replace worked:) Thanx

---

### Post by Drate on 2007-11-30
How do I make that permanent?  What file do i need to edit how to make that happen by default?!?!

---

### Post by Drate on 2007-12-02
For all those concerned, reinstalled metacity (rebooted to see if it fixed it), nope, ran "metacity --replace" (rebooted to see if it fixed it), yep. Maybe I didn't need the first reboot, but who cares? That process seems to have done the trick permanent.

---


---
title: "Weird error on install"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by viergeame on 2007-03-17
I'm trying to install ubuntu on my sister's computer, which probably wasn't a good idea to start with since I didn't install my own, a friend did it.  Anyway, I put in the live CD and I can get to the screen asking if I want to install or run, start ini safe graphics mode, etc.  When I select start or install the screen goes black and stays that way for about 5 minutes and then two error messages come up and it refuses to go any further.  

The messages are:
(numbers) Buffer I/O error on device hdc , logical block 192563
(numbers) hdc: drive is not ready for command

The numbers in ( ) are different every time.  I ran the disk check and it came out alright.  Also it is the same disk that was used to install mine and I have also used this disk as a live CD on another computer with no problems.

I don't know if this is necessary information, but here are the specs on her computer.
eMachine w1640
1600+ AMD Athlon XP
224mb DDR ram

---

### Post by Kobalt on 2007-03-17
When you boot the computer and arrive at the menu (install/start, etc.) : press F6 to access the boot options then add at the end of the line (with a space before, none after)
> noapic nolapic
Then press enter to boot.

I hope it helps.

---

### Post by viergeame on 2007-03-22
Now I got past that error.  Now it's doing something else.  I start the installer and it freezes as soon as I get to the time zone selection page.  Everything in the background works and when I mouse over the close/minimize/fullscreen buttons on the installer they darken just like they would in a normal active window.  However, when I click them they don't do anything.

<RESOLVED>

---


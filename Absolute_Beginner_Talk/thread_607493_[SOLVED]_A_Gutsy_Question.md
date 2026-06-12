---
title: "[SOLVED] A Gutsy Question"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by LizardKing73 on 2007-11-09
Hey all,

My first Ubuntu was Dapper Drake which I installed on my laptop. Recently I installed Gutsy Gibbon, I love the distro but I was wanting to know does anyone else experience a long lag time when Gutsy is booting up?
I get the GRUB message when I first turn on my box followed by the black screen saying "Starting up" but then my box sits with a black screen for what seems to be a couple of minutes (I havent actually timed it) before coming up with the log in screen.
I'm not calling this a problem because there doesnt seem to be anything wrong with the distro and when it gets booted up it runs like a dream it just wasnt something Dapper Drake did or maybe it was because Drake showed the boot text while Gutsy is just a blank screen that makes it seem like it takes longer.
Anyway I was just wanting to know if anyone else was having this?
Is there anyway to get Gutsy to show the boot text?

Thanks all

---

### Post by Nulifier on 2007-11-09
The problem lies somewhere with your graphics I had this same problem when I upgraded to Gutsy from the RC of Gutsy.

If you just want to see the text scrolling past (not as pretty but its not a blank screen) do this:

sudo gedit /boot/grub/menu.lst

then find the line with the current kernel you are running and remove the lines:
quiet splash

just those words and same the file

Then when you boot up next you will have a large screen of scrolling text

Its not the best but its better

---

### Post by LizardKing73 on 2007-11-12
Ahh, thats MUCH better but the removal of the "quiet splash" has actually improved the speed of Gutsy's boot up time, I actually timed it. 63 seconds with quiet splash in place...38 seconds with it removed.
Guess taking it out lets Ubuntu run the way its supposed to.
Thank u very much Nulifier.

---

### Post by slymi2005 on 2007-11-12
I'm on Xubuntu, what input would I use? Says 'gedit' not found.

---

### Post by FuturePilot on 2007-11-12
> **slymi2005 said:**
> I'm on Xubuntu, what input would I use? Says 'gedit' not found.

```
gksudo mousepad /boot/grub/menu.lst
```
;)

---


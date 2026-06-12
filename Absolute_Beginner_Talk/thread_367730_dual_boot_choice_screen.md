---
title: "dual boot choice screen"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by dylpicklesdad on 2007-02-22
hello everyone!
this may seem like a strange question but cnsider i am very new at this.
when you set up a dual boot has anyone come up with a gui that will display your
operating system logo's and click to choose instead of the text based selection?
thank you
dylpicklesdad

---

### Post by annda on 2007-02-22
grub (that's what is behind the menu you see at boot) can't do it. but you can look around for other bootloaders.

---

### Post by dylpicklesdad on 2007-02-22
thank you annda; i thought grub came with egy eft as the main boot control? if so how is it possible to run a different boot loader? i do not think i am capable of that kind of tweak!
but i will look into it regardless. once again thank you for the reply
dylpicklesdad

---

### Post by netkid91 on 2007-02-22
It will NEVER happen with BIOS-based PC's.  The issue is the bootloader can only be 512 BYTES long, which is not a lot of space.  Just basic mouse functionality would cause a bootloader to expand way past that, you'd probably need to have around 3-10 Kbytes of bootloader to enable such a thing.  Grub CAN load a background image off disk, but that's it.

---

### Post by Dirty Ole on 2007-02-22
> **dylpicklesdad said:**
> hello everyone!
this may seem like a strange question but cnsider i am very new at this.
when you set up a dual boot has anyone come up with a gui that will display your
operating system logo's and click to choose instead of the text based selection?
thank you
dylpicklesdad

You can't have such a fancy boot menu as far as I know but you can use [gfxboot]("http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot"). It works flawlessly with Dapper and edgy.

---

### Post by dylpicklesdad on 2007-02-22
thank you all; to netkid91 it is nice to see someone else from idaho in here! 
dirty ole, i think that may be a little out side my ability i'm barely comfortable with using
xp all the command line scares the dickens out of me. but i guess you have to learn sometime. thanks all!
dylpicklesdad

---

### Post by Tomosaur on 2007-02-22
Gag bootloader allows you to have nice little icons with your operating systems. It does not have mouse functionality though, and I don't think any bootloader does.

---

### Post by dylpicklesdad on 2007-02-22
to TOMOSAUR;
you hit the nail on the head this was pretty much what i was looking for. not quite the picture in my head but i do not think it is possible from the things i have heard here.
i was thinking a simple black screen with the ubuntu and xp logo's as a display with a point and click function. but gag may be just fine!
thanks all

---


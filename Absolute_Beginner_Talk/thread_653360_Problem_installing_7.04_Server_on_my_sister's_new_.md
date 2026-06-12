---
title: "Problem installing 7.04 Server on my sister's new laptop"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-12-29
trying to install the desktop gui over it. It apt-get updates fine but gets stuck when I apt-get install unbuntu-desktop. It says it can't find the package. How do I fix this?

---

### Post by clayt0njknight on 2007-12-29
are you going to run the notebook as a server?  if you've got the bandwidth to do it, i'd just go download the newest Gutsy ISO (32-bit of course) and burn it. What kind of error are you getting?

---

### Post by Kedster on 2007-12-29
thin it would be easeir unless  have lots of stuff just to do a reinstal 
(keep personal stuff in seperate partion after that) then its easy to reinstall

---

### Post by woodsonoversoul on 2007-12-29
Alright, I downloaded 7.10, burnt it, now when I boot off the cd, I begin to boot then the screen fades to a pixelated white. What does that indicate?

---

### Post by clayt0njknight on 2007-12-29
boot safe mode or try changing the resolution before boot?


what kind of notebook is this?

---

### Post by woodsonoversoul on 2007-12-29
When I boot in safe mode it does the same thing, fades to a white screen when it attempts to load gnome. I don't know how to change the resolution before boot

---

### Post by clayt0njknight on 2007-12-29
one of the 'F' keys...  i think it's F4?  when you press it it gives you a long list of resolutions and color depths (1024x768x32 for example is 1024x768 at a 32-bit color depth).  i'd try just setting it down to 800x600x16 and see what you come up with... although it doesn't make a whole lot of sense that during boot this is happening...  at what point during the LiveCD boot is this happening?  Before Desktop?  After Desktop?

---

### Post by woodsonoversoul on 2007-12-29
I changed the resolution and I'm having the same problem. This is happening before desktop

---

### Post by Sef on 2007-12-29
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Checks if the download is good.)

2) Did you burn at 4x or less? (Faster can corrupt the download.)

3) Did you check the disk for errors? (Go down the initial menu towards the bottom.)

---

### Post by clayt0njknight on 2007-12-29
didn't even think about the possibility of a bad burn!  Sef you are an effing genius dude.  I ran into a problem with LinuxMint 3.1 Celena.  I suspected a bad burn, slowed it down to 8x and it ran all nice and purdy...


Good call on that one, and the md5sum as well!


-Clay

---

### Post by Sef on 2007-12-29
Thank you.  This community is all about sharing and that's why I like it.

---


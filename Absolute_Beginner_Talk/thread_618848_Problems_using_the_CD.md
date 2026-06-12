---
title: "Problems using the CD"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by magroski on 2007-11-20
I put the Ubuntu 7.10 CD in the drive, restarted the computer and selected the option "Start With Ubuntu" in the menu.
All the tests have been marked with an [ok] in the end of the line, but when the tests ended, the notebook screen turned into black, the ubuntu loading cursor (the round one) appeared on the screen for a few seconds, so the screen returned to the "console" where i can see the last test message:
Running local boot scripts (/etc/..... ) [OK]    (Something like this)
So the screen turned into black AGAIN, i saw the loading cursor, the screen turned into console (the same message was still there), then turned into black again, and looped until i turned the pc off.

So i thought the problem was the CD, i done the CD test and success.
I used the cd in my desktopm, every test were ok, BUT, when the screen turned into black, the loading cursor appeared, and a few seconds later the Gnome Desktop.

So, the question is: Can someone explain why the Ubuntu doesn´t run in my notebook???


Sorry for my horrible english ;P

---

### Post by Paul820 on 2007-11-20
Have you tried the alternate CD? [http://releases.ubuntu.com/7.10/]("http://releases.ubuntu.com/7.10/")

---

### Post by PurposeOfReason on 2007-11-20
Are they both the same architecture? As in, is one 64 bit or not? Always try the alternate install disk.

---

### Post by deadgobby on 2007-11-20
It may be a silly question. Can you post your system specs. Like what make, model, and ect...
Thanks 
Gobby

---

### Post by gn2 on 2007-11-20
When you get the Ubuntu splash screen, there are options to choose at the bottom of the screen,  F6 is for additional boot parameters.
There are quite a few to try. 
One that sometimes helps with laptops is acpi=off

---

### Post by magroski on 2007-11-21
@gn2
 I tried the acpi=off in the command line, but when i pressed "enter" the pc shut down

@deadgobby
Intel Celeron M430, 1,7ghz
512 ram DDR2
HD 60gb
On-Board video 64mb
14,1" widescreen LCD

---

### Post by atlfalcons866 on 2007-11-21
whats the onboard video card?

---

### Post by magroski on 2007-11-21
VIA Chrome 9 HC IGP

---

### Post by gn2 on 2007-11-21
I've heard of people having difficulty with that graphics adapter before.

At the F6 try typing: "force vesa" or "xdriver=vesa" or "VGA=771" (without the quotes)

If that works then after you've got it installed, this may help get a better driver installed: [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164)

---

### Post by magroski on 2007-11-22
i will try...
tonight i post the results

---

### Post by magroski on 2007-11-23
No way, no Ubuntu 7.10 to me

---


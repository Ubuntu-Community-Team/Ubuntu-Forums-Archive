---
title: "Failed to start the X server"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mowcius on 2007-04-05
Hi,
This is my first post so I hope you can understand it!

I have a computer with a pentium II processor, 192MB of ram, a 20GB hard drive and a reasonable sound card and graphics card.

I got it all for free but was told it all works.
It han Win 95 and i wiped the whole lot.
I've been trying to boot it up with Edgy but it is not working.
It gets to the graphical menu where I set up my screen res and keypad layout and then clicked 'start or install ubuntu. It then does all of the loading bar but stops after that and comes up (after about 10 seconds) with a box saying: Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the problem.
       <Yes>        <No>

I then pressed yes and had a look but it made no sense to me. I clicked ok and it said that the X server was disabled and to start it again when it was set up correctly. I don't know what to do!      Can you help me?

Many thanks if you can......

Mowcius

---

### Post by Iceni on 2007-04-05
Why not try the alternative install cd? It's easy and you don't have to start the graphical interface.

---

### Post by Mowcius on 2007-04-05
How do you get the alternative install cd?

I don't have Broadband and it was a friend who gave me the other CD. 

Is there any way i can get it through the post?

Thanks

---

### Post by STREETURCHINE on 2007-04-05
try

           > sudo dpkg-reconfigure xserver-xorg

answer all the questions if not sure use the default selections ,

restartx

---

### Post by Mowcius on 2007-04-05
Where do you type in:
sudo dpkg-reconfigure xserver-xorg ? 

That may seem like a stupid question!

---

### Post by STREETURCHINE on 2007-04-05
open terminal //..   application >accesories >terminal

---

### Post by Mowcius on 2007-04-05
When i've got to the graphical menue which says
[CENTER]UBUNTU

[SIZE="2"]Start or install ubuntu[/SIZE]
[SIZE="2"]Start ubuntu in safe graphics mode[/SIZE]
[SIZE="2"]check CD for defects[/SIZE][/CENTER]

etc

What do i type in where?

---

### Post by Jussi01 on 2007-04-05
after you get the xserver error does it take you to a command line? that is where you would type the command if it does. Also have you tried starting it in safe graphics mode?

---

### Post by Mowcius on 2007-04-05
I've tried it in safe graphics mode
it didn't work!

i'm just about to try that!

thanks

---

### Post by STREETURCHINE on 2007-04-05
have you got a live disk in.?

---

### Post by Mowcius on 2007-04-05
My computer hasasked me to pick a chipset manufacturer and mine is second hand so i have no idea what it is

i've had a look but i can't see what make it is

what can i do?

---

### Post by Gina on 2007-04-05
I had problems at that stage with Edgy (6.10) so tried Dapper (6.06) that gave no problem.

---

### Post by STREETURCHINE on 2007-04-05
just use the defaults,

if you read and follow the instructions it is pretty self explanatory.

---

### Post by Mowcius on 2007-04-05
there is no default unless you mean the first one on the list

---

### Post by STREETURCHINE on 2007-04-05
i think it is vesa

---

### Post by Mowcius on 2007-04-05
ok thanks

---

### Post by Gina on 2007-04-05
I got my first live CD on a magazine and have had others too.  I'm afraid you'll have lots of waiting about downloading updates on dial-up though - hope you have plenty of patience :lol:

---


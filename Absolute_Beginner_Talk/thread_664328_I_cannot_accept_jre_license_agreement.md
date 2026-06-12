---
title: "I cannot accept jre license agreement"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by ravi.786 on 2008-01-11
Hi all,
I'm a bit new at this, but I was trying to get my video and audio working online, and I found and used these codes:

sudo apt-get install aptitude
sudo aptitude install ubuntu-restricted-extras

the first one went through its business ok, but the second one goes as far as the Sun Java license agreement screen which pops up over the terminal screen, I would like to know how to accept or deny this license agreement. If I press "enter" nothing happens, and if I press escape it shows the terminal screen for about half a second and then goes back to the blue license screen. The only other normal buttons that do anything are Pgup and Pgdn. If I exit the terminal by clicking on the x at the top right hand corner, then I have to re- build dpkg by running:
sudo dpkg --configure -a

Then I ran some code which I can't see now, it's trapped behind the blue license agreement screen, but I think they were the following:

sudo apt-get update
sudo apt-get upgrade

and the second bit, sudo apt-get upgrade, brings me full circle back to the locked license agreement screen.

Does anyone know what I'm doing wrong?
any assistance at all will be great.
Thanks for taking the time to read all this,
Ravi...Please i am too tired and i need it Asap..

---

### Post by jrusso2 on 2008-01-11
Try tab then enter  Make sure the window has focus

---

### Post by matchstich on 2008-01-11
just went to package manager and installed java6 jre and the plug in.

it worked for me.  the agreement was a box to check.

thanks

---

### Post by capink on 2008-01-11
I once had this problem. The solution for me was to press F12.

---

### Post by ravi.786 on 2008-01-11
Thanks a lot, Its working Fine for me ......Really Appreciated..

---


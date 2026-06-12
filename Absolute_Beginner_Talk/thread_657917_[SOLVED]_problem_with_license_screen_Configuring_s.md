---
title: "[SOLVED] problem with license screen Configuring sun-java6-jre"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by andyclaxn on 2008-01-04
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
Andy

---

### Post by OldGrey on 2008-01-04
Its a while since I did this, but is there a accept box to tick? or accept button to click? or sometimes you have to scroll to the bottom of the ULA before the accept button is activated.

---

### Post by RSLxH on 2008-01-04
You just scroll down or maximize the console window to see the complete licence agreement, and use the TAB button to select accept or decline and then press enter.

---

### Post by andyclaxn on 2008-01-04
Hey,
 thanks a million, I'm well sorted, thank you both, it was the tab key thing i didn't know.
Thanks again
Andy

---

### Post by rdias23 on 2008-05-20
Thanks from me too.  Stupid Tab key...

---


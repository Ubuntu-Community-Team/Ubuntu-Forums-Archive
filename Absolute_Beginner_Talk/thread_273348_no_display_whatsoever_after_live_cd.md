---
title: "no display whatsoever after live cd"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Lithp on 2006-10-07
Dual AMD 4200 chips
1 gig ram
Hanns-g monitor
latest ubuntu distro i386

Hi, 
Great forum. This is my first post. Be gentle :)

I tried to install from the live cd and get a scrolling list of information. when i reach the Gnome graphical interface part (according to what is scrolling past) my monitor stops working and goes into standby mode.There is no display what soever!
i went to a site which trys to address this issue ( [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) ) i am still unsuccessful.

I have to ctrl/alt/f4 to get to command prompt.

When i try ctrl/alt/f7 nothing happens.

sudo /etc/init.d/gdm start results in a red "Fail" to be displayed on the screen.

it would appear that i do not have the Gnome desktop at all or it cannot be displayed. I have tried an update using " sudo aptitude update" and "sudo aptitude install ubuntu-desktop" 

Any ideas?

---

### Post by Lithp on 2006-10-08
can no one help?

---

### Post by wabbit-angelz on 2006-10-08
Sorry, I can't help, but I'm here to say that I have the same problem. Unfortunatley. Only diffrence is that my screen shows up not as blank but as green strips. Nothing I have tried so far works either, given that I'm totally new to Linux/Ubuntu in general.

I have a second system that doesnt have a case, which is what Im using right now, installed with Ubuntu+FVWM Crystal and It works smoothly. Ive been trying to install Ubuntu on my main desktop, and the problems I encounter are described above.

So.. help would be appreciated =\

---

### Post by mongooseman1128 on 2006-10-08
I'm not sure how much help I'll be but it seems like something you may want to try is popping in the live CD and run the disc checker to make sure it's not messed up or anything.

---

### Post by wabbit-angelz on 2006-10-08
Ive ran the check, and the only thing that is mismatched is the first file that has relation to GAIM near the end of the list. Everything else is a-okay.

---

### Post by Hranj on 2006-10-08
ive had the same problem before on my old computer. i tried using about 5 or   6 different cds with it and multiple distibutions on linux none of them worked. idk what it could possibly be.

---

### Post by mongooseman1128 on 2006-10-08
I think you want to make sure your hardware is all okay, different people have different programs they use, but Hitachi's DFT works great for your HDD as well as windows memory test (for RAM). Eurosoft makes a good MOBO and processor test and those are pretty much the important tests, other than giving you the names though I can't remember how to get the programs

---

### Post by wabbit-angelz on 2006-10-08
If this helps at all, I have two seperate HDs, a 60GB and a 80GB. Im running everything off of the 60, as my 80 is just a storage box. Ive installed Windows 2k SP2 on the 60, but partitioned only 16 gigs for it. The rest was planned to be left for Ubuntu. I dont know if they cause interference or something, and obviously, I have no clue. I have a Nvidia GeForce 6600, just as a side note.

---

### Post by mongooseman1128 on 2006-10-08
nah the two shouldn't interfere at all because of the seperate partition. the video card shouldn't be a problem, there are always default drivers that give the system a low level of functionality for the card until you get the right ones. I'm sorry, but my knowledge of this problem is pretty much spent as of now. I'll ask my networking teacher (she's been a long time linux user, but her distro is suse) though about it.

---

### Post by wabbit-angelz on 2006-10-08
Okay, Ive ran the sudo aptitude update and sudo aptitude ubuntu-desktop thing. Turns out kubuntu works and ubuntu doesnt. Whats the diffrence between kubuntu and ubuntu?

Edit: Thanks for the effort Mongoose =]

---

### Post by mongooseman1128 on 2006-10-09
as far as I know they run off the same kernel but the main difference is that kubuntu uses the KDE dekstop by default and Ubuntu uses Gnome. Also, kubuntu comes with different preinstalled apps I believe.

---


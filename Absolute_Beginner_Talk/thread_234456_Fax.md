---
title: "Fax"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by indie56 on 2006-08-11
Hi
I am brand new to Ubuntu (6.06). I want to fax directly from my computer. Efax is installed. 
When I drop the file into Efax, I get a message that the format is not supported. A post Script type is required. There is a thread on this but it was of no help. Pl give detailed instructionas as I am a novice at computers.
Indie56

---

### Post by GuitarHero on 2006-08-11
What type of file are you dropping into it?

---

### Post by indie56 on 2006-08-11
Open Office files.

---

### Post by indie56 on 2006-08-11
Hello
Can anybody pl help with fax. I want to fax from OO.
indie56

---

### Post by indie56 on 2006-08-11
Can anybody pl help with fax. I want to fax from OO.
indie56

---

### Post by frrobert on 2006-08-21
First,  install efax gtk from the Synaptic Paxkage manager if you haven't already.

Next go to Administration printing

Double click on new printer
Select Network Printer  HP JetDirect

Host   is localhost
Port is    9900

Hit Forward
Printer manufacter should be raw
click on queue and click forward

Replace the name queue with something like fax  then click on apply.

Now start Efax-gtk under Office  make sure the fax entry method is socket

Now if you print a document in openoffice using the fax driver a dialog box  from efax should open and just enter the telephone number

Hope this helps

---

### Post by nichos on 2007-11-06
Genious, after a few tries I made it work, BUT... I got many errors, red& black, the last was the one below.

Now, my modem is not recognized by Linux, so this must be why. BUT....how about the AOL B.Band I am on, & isn't it an "eFAX" after all?, or B,Band doesn't count?
tahnx      nick

efax-0.9a: 14:18:35 failed page /home/x/efax-gtk-server/efax-gtk-server-aefPE3.001
efax-0.9a: 14:18:35 Error: fax device w

---

### Post by rev0lv3r on 2008-05-29
> **nichos said:**
> Genious, after a few tries I made it work, BUT... I got many errors, red& black, the last was the one below.

Now, my modem is not recognized by Linux, so this must be why. BUT....how about the AOL B.Band I am on, & isn't it an "eFAX" after all?, or B,Band doesn't count?
tahnx      nick

efax-0.9a: 14:18:35 failed page /home/x/efax-gtk-server/efax-gtk-server-aefPE3.001
efax-0.9a: 14:18:35 Error: fax device w

Well that's what fax is, it's over phone line

I think the point of the e as in electronic in eFax was that you could use your computer as a fa machine a la WinFAX.

---


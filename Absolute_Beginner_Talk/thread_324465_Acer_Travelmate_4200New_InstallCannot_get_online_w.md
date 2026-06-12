---
title: "Acer Travelmate 4200/New Install/Cannot get online with wireless or cable/please help"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Knigel on 2006-12-23
I've installed Ubuntu a few weeks ago and have been trying to get online.  I have a Acer Travelmate 4200 and have tried various things, but without being able to use the internet from Ubuntu, I have trouble doing anything without jumping back and forth between Windows XP boot and Ubuntu.  Many things I did, didn't give me errors, I just cannot get online.  In the network tools, my local area connection is checked and looked like it would work, but once I plugged it in, I still could not get online.  The wireless checkbox is unchecked.  I have the Acer driver CDs, and have tried to install them, nothing worked yet.  I like to figure things out, but right now I'm stumped.  Thanks in advance, please feel free to ask me questions.

---

### Post by Bachstelze on 2006-12-23
It would help if we knew what NICs you have. Please paste the output of *lspci*.

---

### Post by Knigel on 2006-12-23
Do you know how I can get that information?  I'm on windows XP.

---

### Post by Bachstelze on 2006-12-23
You can't ;) Boot your Ubuntu, open up a [terminal](http://psychocats.net/ubuntu/terminal), type *lspci* and paste us what you get.

Windows will most likely give you the info in the Device Manager too, all we need is the model of the NICs.

---

### Post by Knigel on 2006-12-23
Is there anyway I can get the info from Windows?  I cannot get online so have no way of copy and pasting, unless I write it all out.

---

### Post by Knigel on 2006-12-23
If it helps any I get this in Device Manager:

Network adapters:
Broadcom 440x 10/100 Integrated Controller
Intel(R) PRO/Wireless 3945ABG Network connection

P.S.
I also cannot see my other drives from my Ubuntu partition so cannot transfer files

---

### Post by Bachstelze on 2006-12-23
As for your wireless card, I have the same on my Asus and I remember it worked just out of the box in Ubuntu so I guess all you have to do is to configure it and you should be up and running. However, I can't tell you how to do it in GNOME as I never use it.

---


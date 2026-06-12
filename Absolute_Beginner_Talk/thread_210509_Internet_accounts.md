---
title: "Internet accounts"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Numbat on 2006-07-07
Not new to computing but I am a complete newby with Ubuntu. What is the equivalent to setting up an internet account in Ubuntu? There doesn't seem to be any similarity with the language used or the processes. I wouldnt mind betting that a person completely new to computing would have an easier time than I am having. Maybe I should go look for a 9 year old?

---

### Post by dmizer on 2006-07-07
not sure what you mean by "setting up an internet account" for one.

what kind of internet service do you have? dial up, dsl, cable, pppoe ...

---

### Post by Apple 101 on 2006-07-07
In Windows, you can setup a dial-up account, VPN or other service provider, say PPPoA/E.  I think Numbat means setting up an account like those I have said.

---

### Post by 3rdalbum on 2006-07-07
System > Administration > Networking for all your Internet account needs. Don't feel bad that you couldn't work out which control panel let you set it up - it took me over half an hour to figure out which one to use in Windows!

---

### Post by Numbat on 2006-07-07
OK. I meant dailup internet accounts. I have however found some Help informatio (Google is my friend) on Ubuntu pages and may be able to work things out from there. If not, you may see me back again. Thanks.

---

### Post by Numbat on 2006-07-07
I take what I said in my last post back. Read the help and lost again. In Hardware Modems Help, it says (using the graphical i/f) System=>Aministration=>Networking, kppp, gnome-ppp. What does this mean? The bit on the end, the rest is OK.
Also, it gives what appears to be a command line.
"$ sudo adduser USERNAME dip" and
"$ sudo adduser USERNAME dialout". 
Where do you enter this?

---

### Post by Silver Streak on 2006-07-07
> **Numbat said:**
> I take what I said in my last post back. Read the help and lost again. In Hardware Modems Help, it says (using the graphical i/f) System=>Aministration=>Networking, kppp, gnome-ppp. What does this mean? The bit on the end, the rest is OK.
Also, it gives what appears to be a command line.
"$ sudo adduser USERNAME dip" and
"$ sudo adduser USERNAME dialout". 
Where do you enter this?

Not sure about the first one (I get cable internet), but to get to a terminal, go to Applications >> Accessories >> Terminal

SS

---

### Post by Apple 101 on 2006-07-08
> **Numbat said:**
> In Hardware Modems Help, it says (using the graphical i/f) System=>Aministration=>Networking, kppp, gnome-ppp.*kppp* is for KDE and *gnome-ppp* is for Gnome.  Can you see either one of those utilities.  If not, open Synaptic and search for *gnome-ppp* (or *kppp* if you are using KDE).  Then you can configure your modem.
> **Numbat said:**
> Also, it gives what appears to be a command line.
"$ sudo adduser USERNAME dip" and
"$ sudo adduser USERNAME dialout". 
Where do you enter this?
Those commands represent the bash terminal shell.  Do not input the $ dollar sign to the terminal, as your command will not be recognised.  Open a Terminal as said by Silver Streak.

---

### Post by catlett on 2006-07-08
The terminal is ubuntu's command prompt. The ~$ is like seeing C:\ before a command . You open a terminal by going to the top panel and selecting Applications then a menu drops down and you select Accessories and fibnally select Terminal.
Next is to enter those lines 1 at a time. Enter a lins of text and pres enter. If it asks you for a pasword, enter the pasword you login with. The screen will not acknowledge the letters but they are being entered. Just press the keys and hit enter.
Alot of times when instructions say USERNAME they mean for you to put your username there. Sometimes USERNAME is part of the command but usually the directions will clarify. So assuming USERNAME means your name, open a terminal and enter ```
sudo adduser Numbat dip
```
Press enter. Enter your password. Press enter. Then enter this
```
sudo adduser Numbat dialout
``` Press enter.

---

### Post by Numbat on 2006-07-08
Do I need to learn Unix in order to use Linux at the basic level?

---

### Post by Iowan on 2006-07-08
The blunt answer would be **yes**.  However, depending on how far you intend to go, most of the advice you get from the forum will (should) give you the command syntax you'll need - sometimes in cut/paste format. So, you can probably "learn as you go".

---


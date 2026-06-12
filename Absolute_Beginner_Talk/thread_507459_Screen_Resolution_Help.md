---
title: "Screen Resolution Help"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by BETOCORELLA on 2007-07-23
OK I JUST INSTALLED UBUNTU INTO MY LAPTOP. FREED IT YAW. ANYWAYS WHEN I START MY LAPTOP IT GOES INTO A BLACK SCREEN. HOW DO I CHANGE THAT? I HAD THE SAME PROBLEM WITH THE CD UNTIL I SWITCHED THE VGA TO 1024x768x16 THEN IT WORKED FINE. HOW CAN I CHANGE THIS ON MY LAPTOP?

---

### Post by pyros on 2007-07-23
> **BETOCORELLA said:**
> OK I JUST INSTALLED UBUNTU INTO MY LAPTOP. FREED IT YAW. ANYWAYS WHEN I START MY LAPTOP IT GOES INTO A BLACK SCREEN. HOW DO I CHANGE THAT? I HAD THE SAME PROBLEM WITH THE CD UNTIL I SWITCHED THE VGA TO 1024x768x16 THEN IT WORKED FINE. HOW CAN I CHANGE THIS ON MY LAPTOP?

First, find out what resolutions and bit depths your lcd will support. The manufacturer of your laptop should be of some help on this. then open a terminal and type:
"sudo dpkg-reconfigure -phigh xserver-xorg"
it will ask you what type of video chipset you have, and then what resolutions to use.

---

### Post by BETOCORELLA on 2007-07-23
I Figured It Out. Lol By Any Chance Do U Know How I Can Enable The Desktop Effects?

---

### Post by cawill on 2007-07-23
To get desktop effects go to System->Preference. Click on Desktop Effects and Select Enable Desktop Effect, Click OK.

But whether this works depends on your graphics card and the driver for it.

---

### Post by BETOCORELLA on 2007-07-23
Ok Thanx

---

### Post by pyros on 2007-07-23
> **cawill said:**
> To get desktop effects go to System->Preference. Click on Desktop Effects and Select Enable Desktop Effect, Click OK.

But whether this works depends on your graphics card and the driver for it.

As far as I can tell, this method only works for nvidia cards.

---

### Post by BETOCORELLA on 2007-07-23
Dats What I Have A Nvidia Card

---

### Post by pyros on 2007-07-23
worh a shot then. it should give you the desktops-on-a-cube, wobbly windows, menus, etc and the transparent window borders.

---

### Post by BETOCORELLA on 2007-07-23
Nothin...i Keep Clickin On Enable Desktop Effects An All Get Is A Whte Screen

---

### Post by pyros on 2007-07-23
> **BETOCORELLA said:**
> Nothin...i Keep Clickin On Enable Desktop Effects An All Get Is A Whte Screen

welp.. still beta-quality stuff, so it's not working for everyone.

---

### Post by cawill on 2007-07-23
> **pyros said:**
> As far as I can tell, this method only works for nvidia cards.

No it works with open source ati drivers (as I can do it) and intel drivers I think.

---

### Post by pyros on 2007-07-24
> **cawill said:**
> No it works with open source ati drivers (as I can do it) and intel drivers I think.

Ah, I've tried it with the proprietary ati drivers and saw "nvidia card not found" or similar messg and assumed too much. Good to know.

---


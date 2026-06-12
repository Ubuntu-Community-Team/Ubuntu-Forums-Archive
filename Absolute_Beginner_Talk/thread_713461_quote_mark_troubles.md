---
title: "quote mark troubles"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by rotata on 2008-03-02
I bought an eeePC with xubuntu installed. Due to some ownership issues, I re-installed xubuntu. I added some useful-looking utilities and visual accessibility support with synaptic and a couple of programs with the add utility. Now, I can not insert a single quote or double quote without hitting space afterwards. I have messed with fonts and language and keyboard until I developed a headache. 

How to fix this problem? 

TIA!

---

### Post by prshah on 2008-03-05
Hi 

I have an Acer TravelMate with an English+Arabic keyboard that shows these same symtoms. If I didnt press space, and instead typed in a vowel, it would display with accents/umlauts. Also, pressing the double/single quote key twice in a row produces two double/single quotes.

Using "sudo dpkg-reconfigure xserver.xorg" and setting the keyboard to "us" cleared it for me.

If your keyboard has characters in other langages, maybe this will clear your problem.

Cheers,
PRShah

---


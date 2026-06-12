---
title: "Ubuntu Boot Problems"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by umattu on 2006-05-17
Hi all,

I have recently made a switch from FC5 (which i was a noob with also) due to its shortcomings with my laptop hardware. Ubuntu on the other hand is humming along like a dream.

I want to have ubuntu on my main box as well. I have run many dual boot setups so I am familiar with how to do it, now this same prob plagued me on my box with FC5. 

The ubuntu install went beutifully, grub works great, but when i get to ubuntu's login screen, I enter my username and password, as soon as I hit enter the screen distorts and my rig just stops in its tracks. I beleive it to be the same NVIDIA probs I had with FC5. I have a BFG 7800gtoc PCIX 16x, atleast with fc5 I could get into runlevel 3 and fool around, but with ubuntu I cannot, I searched around and found peeps changing files to get ubuntu to boot to a terminal. I cannot get at the files in noway, even when i select "failsafe terminal" from the login session window, it messes up just like if I was booting into gnome. 

I have fallin in love with ubuntu the last couple weeks and I really want to get it up and running on my main PC. I did find the installing NVIDIA drivers in the FAQ but I can't run the commands without a terminal.

Please Help!!!
someone..

umattu

---

### Post by zhoux on 2006-05-17
[QUOTE=umattu]Hi all,

I have recently made a switch from FC5 (which i was a noob with also) due to its shortcomings with my laptop hardware. Ubuntu on the other hand is humming along like a dream.

I want to have ubuntu on my main box as well. I have run many dual boot setups so I am familiar with how to do it, now this same prob plagued me on my box with FC5. 

The ubuntu install went beutifully, grub works great, but when i get to ubuntu's login screen, I enter my username and password, as soon as I hit enter the screen distorts and my rig just stops in its tracks. I beleive it to be the same NVIDIA probs I had with FC5. I have a BFG 7800gtoc PCIX 16x, atleast with fc5 I could get into runlevel 3 and fool around, but with ubuntu I cannot, I searched around and found peeps changing files to get ubuntu to boot to a terminal. I cannot get at the files in noway, even when i select "failsafe terminal" from the login session window, it messes up just like if I was booting into gnome. 

I have fallin in love with ubuntu the last couple weeks and I really want to get it up and running on my main PC. I did find the installing NVIDIA drivers in the FAQ but I can't run the commands without a terminal.

Please Help!!!
someone..

umattu[/QUOTE]

i don't know if i understand you problem completely (i'm a noob), but you can hit ctrl+alt+F1 to F6. They don't involve any gdm/kdm. then you can use somthing like "sudo nano ......" to edit the file.

Hopefully that helps

---

### Post by umattu on 2006-05-17
I can't get to a command line.

If I could get to a command line I could install the NVIDIA drivers, instead of fixing up a file to boot to the terminal.

---

### Post by zhoux on 2006-05-17
[QUOTE=umattu]I can't get to a command line.

If I could get to a command line I could install the NVIDIA drivers, instead of fixing up a file to boot to the terminal.[/QUOTE]

So you can't access the other consoles at all? For example :

Ctrl+Alt+F1

---


---
title: "Where do the downloads go?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by SamTheShaman on 2006-03-25
After my unsucessfull attempt at Breezy badger. With no luck. The old CD mount problem. I was hoping to use breezy because it had automatix.
Anyway that didn't work So I tried Dapper. My first linux and Dapper seems to work. But I cannot get the DVD to work. I tried all kinds of things after reading all day on the forum. As a last resort I am trying different installations. Realplayer etc... Everytime I do a download to the desktop. I cannot find the download. Firefox is set to put it on the desktop, under tools, preferences.
I tried all kinds of downloads but cannot find one. Where do the downloads go?
I'm sold on dapper, if I can get the DVD to work.
So far so good though. A bit of a learning curve But not too bad.
](*,)

---

### Post by KansasJoe on 2006-03-25
usually they go to /usr/bin but if you want to check where the executable is type which programname...e.g. say you're looking for firefox...then in terminal type

which firefox

note: many of programs should go to apps menu

---

### Post by OBnascar on 2006-03-25
[QUOTE=SamTheShaman]Where do the downloads go?[/QUOTE]

In a terminal, try this command:
'sudo whereis name_of_program'

See what that command shows you......Welcome to the forums SamTheShaman !

---

### Post by SamTheShaman on 2006-03-25
I cannot find anything downloaded.
I go to [www.real.com](www.real.com)
I download. realplayer10gold.bin
Who knows where it is on my hard drive. It ain't in my /user/bin.
I have Firefox/1.5.0.1
from Dapper.
I tried the which command nothing.
I looked in applications add/remove, not there.

---

### Post by SamTheShaman on 2006-03-25
I tried sudo

Here what i got
ubuntu@ubuntu:~$ sudo where is realplayer10gold.bin
sudo: where: command not found
ubuntu@ubuntu:~$

---

### Post by Chyper on 2006-03-25
firefox probably sent it to your temp folder

filesystem/tmp

you can tell firefox where you want the download to go
i usually send it to the desktop

edit>preferences>downloads>save all files to this folder

---

### Post by OBnascar on 2006-03-25
[QUOTE=SamTheShaman]I tried sudo

Here what i got
ubuntu@ubuntu:~$ sudo where is realplayer10gold.bin
sudo: where: command not found
ubuntu@ubuntu:~$[/QUOTE]

I don't have RealPlayer installed but I would guess your name is to long, try just entering: "Realplayer" or "realplayer gold"

or try playing around with different combinations.
That command does work real well, I am just not to sure what one would have to enter for RealPlayer. Maybe someone will come along what to enter exactly for it.

---

### Post by big joe on 2006-03-25
[QUOTE=SamTheShaman]I tried sudo

Here what i got
ubuntu@ubuntu:~$ sudo where is realplayer10gold.bin
sudo: where: command not found
ubuntu@ubuntu:~$[/QUOTE]

Try "whereis" instead of "where is" (no gap)

---

### Post by OBnascar on 2006-03-25
[QUOTE=big joe]Try "whereis" instead of "where is" (no gap)[/QUOTE]

I did not notice he was using two words !

---

### Post by SamTheShaman on 2006-03-25
This is what I got 
ubuntu@ubuntu:~$ sudo whereis RealPlayer10GOLD.bin
RealPlayer10GOLD:
ubuntu@ubuntu:~$

What does sudo mean anyway?

---

### Post by Chyper on 2006-03-25
if you go to edit>preferences>downloads

where is firefox set to save your downloads?

---

### Post by OBnascar on 2006-03-25
[QUOTE=SamTheShaman]
What does sudo mean anyway?[/QUOTE]


[**[COLOR="DarkOrange"]HERE [/COLOR]**]("https://wiki.ubuntu.com/RootSudo")is good documentation on using sudo

---


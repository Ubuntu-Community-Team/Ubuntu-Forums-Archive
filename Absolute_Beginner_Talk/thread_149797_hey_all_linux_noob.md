---
title: "hey all linux noob"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by LORD_PoLvO on 2006-03-24
hey all ive been a windows suer for the past (god knows how manny years lol) and im really frustrated with wiundows on a whole when my friend finally reffered me to linux i so dar have a duel boot system (ubuntu and home) and i need help getting a lot of things going lol sorry to annoy u but i really want to get ubuntu to work for me are there any good drivers for my NVIDIA gforce 4 mx440 becasue it works but its incredibly slow trying o do anything in 3d (all i have is 3d screensavers atm lol) also i am on a network and the modem is conected to another compter and the hub and i need a program called bigpond broad band cable whic logs u into it and it windows only....... also i have a copy of a program called cedega in a rpm file but every time i try to open it it says it cant read the archive type? any help on any 3 of these issues would be gr8 thnx btw im running ubuntu 5.10 32bit on my AMD athlon xp 2600+ 40 gig hdd is there a way i can get it to detect my network/modem so i no longer have to log onto windows so i can ask questions etc lol ty for any help u can give me at all

---

### Post by Zeroangel on 2006-03-24
For the Nvidia drivers, take a look at [This thread]("http://www.ubuntuforums.org/showthread.php?t=75074").

Ubuntu uses Debian (.deb) packages instead of RPMs, but you might be able to convert cedega to a debian package using alien, though it will fail most of the time. Do a search on the repos for alien. Additionally you can do a search on the forums for 'RPM Cedega Alien' to find threads about this that have already been covered.

---

### Post by LORD_PoLvO on 2006-03-24
thnx for link to the drivers ill take a look at that now also what do u mean by search on repos? sorry i dont no what that means im totally new to linux lol

---

### Post by Zeroangel on 2006-03-24
[COLOR=DarkGreen][COLOR=black]Alien is a command line tool, which means you have to open up a 'terminal' (screen that you use to run text commands) and type in a command in order to use it. Usually, only an intermediate user will want to use this terminal to run commands like this. Linux newbies might be better off just looking for another solution (not to scare you, the terminal is *great* to learn, but you do have to invest some time).[/COLOR][/COLOR]

Repos = Repositories = Places where software is stored online. If you go to **[COLOR=DarkGreen]&#65378; System > Administration > Synaptic Package Manager &#65379; [/COLOR]**[COLOR=black]then you will be able to install packages (linux addons, and programs) right from there. To enable the universe and multiverse repositories, use the menu bar in Synaptic to select  [/COLOR]**[COLOR=DarkGreen]&#65378; Settings > Repositories &#65379; [/COLOR]**[COLOR=DarkGreen][COLOR=black]make sure all of the checkboxes are checked (you only have to do this once throughout the life time of your ubuntu install), and then click OK and do a search for 'alien'.

EDIT: Just found this post:
[quote="Artificial Intelligence"][/COLOR][/COLOR]It's not advisble to use alien to make .deb out .rpm it could mess up something or not working at all. Better to use a .deb package or compile your own.[/quote]
[COLOR=DarkGreen][COLOR=black] 

[/COLOR][/COLOR]

---

### Post by LORD_PoLvO on 2006-03-24
ok kool i need to use method 2 for the dirvers i downloaded to .run file and i am logging of windows now so i can go and try it on my ubuntu boot ty for ur help i will post back if it works or not

---

### Post by LORD_PoLvO on 2006-03-24
ok kool i have the net working in ubuntu somehow i just loged in and it was working so i dont have to keep logging ino windows now lol umm i have some problms i managed to get alien installed but i dont know where it is located also i recived and error trying top do the drivers thing i will post a pic here now
[IMG]http://i18.photobucket.com/albums/b135/lord_polvo/Screenshot-2.png[/IMG]

ne help

---

### Post by Zeroangel on 2006-03-24
That's odd. It *should* be in the repos. Run the command ```
sudo apt-get update
```To refresh the list of programs and then run the apt-get install command again. If that doesn't work try opening synaptic and doing a search for 'gcc', install the most advanced version they have (3.3, 4.0, what have you).

I suggest that you use method 1 instead of method 2, however. I also have a GF4MX and Method 1 has worked flawlessly for my card all of the times I have installed it.

---

### Post by LORD_PoLvO on 2006-03-24
ok i managed to get the file to read i placed it on the desktop i ran it and them ran it thro terminal right i copied and pasted the codes it read fine then it said it had to download mor files i allowed it but by this time i was not getting a conection to the internet anymore it stayed conected for like 30 mins then droped out i dont even no why it was working i will tell u how my net wokrs iits broadband and we have 2 sepperate username which u ned to use the program bigpond bradband cable login to acces ur username so i dont even know how i managed to get a conection in the first place does method 1 need a conection to the net coz i cant get conected on ubuntu the modem is conectecd to the network hub

---


---
title: "internet connection doesnt work"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kingfoot on 2007-02-11
Hey, so heres how it goes. I repartitioned me 2nd hard drive, i have my first hard drive for storage in windows. the second is split up liek this; 1st partition is 30gb for windows XP, 2nd partition is 60gb for installing programs and things for windows XP, and the 3rd partition is 10gb for ubuntu linux (6.10). the 4th is the linux swap partition.

so everythign installed fine and i can boot into it no problem. I boot into it (it also lets me choose to boot my old windows XP yay!!) and i start changing preferences and making it my own. i realise i need the correct drivers for my hardwarre. so i go into firefox to search how to get the right drivers. but it wont connect. now, i have a dsl box, and its physically connected to my computer, and in the network settings, i enabled it. but there is a username and password for it. i cant find where to input that so it will allow it to connect.

also, when i choose to boot into my windows XP install, it goes to blank screen, and then i hit a button it restarts, otherwise it jsut sits there. so I have to boot into my backup install of windows Xp (SUUUUUUPER SLOW) on my backup hard drive. thats how im typign this now.

any help please? im completely new to linux and have no clue what im doing, except for what ive read about it for isntalling it, but i would say im an intermediate-advanced windows xp user.

---

### Post by shareMenaPeace on 2007-02-11
For a cable modem try 
```
pppoeconf
```
than start the connection with 

```
pon dsl-provider
```

---

### Post by kingfoot on 2007-02-11
where do I put that into?

---

### Post by shareMenaPeace on 2007-02-11
Into the terminal - from top panel see
```

Applications -> Asseccoires -> Terminal
```

This is often handy, rightclick temrinal in the drop down menu and choose add to panel to have betetr access to this application.

---

### Post by Ptero-4 on 2007-02-11
kingfoot. Go to Aplications > Accesories > Terminal. In the command prompt window type the provided commands.

---

### Post by kingfoot on 2007-02-11
I input "pppoeconf" and was told to go to root before entering "pppoeconf" and i dont know how to go to root...

---

### Post by shareMenaPeace on 2007-02-11
type

```
sudo ppoeconf
```

to access with admin privileges

---

### Post by kingfoot on 2007-06-13
hey. so it took me a long time but ive got my computer mostly situated how i would please. first, my main os is windows vista (getting rid of soon though, its not worth it!!!) and xp will be in soon, but right now i have ubuntu 7 installed perfectly awesome with its own 65gb of space. the problem is, it still wont go online. I hooked up my dsl box to it, and ran the pppoeconf command (with sudo :P) and i input my info, it said it connected. so i tried firefox, no luck. i tried to run an update on linux, it failed. whats wrong now? it says all is fine, it just wont go online.

---


---
title: "Windows flashback"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-01
I installed the xmoto game from synaptic. It was slowing down so I messed with some of the graphics settings hoping I could solve this. When I restarted the program the screen for the game was black on black and I couldn't see any of the menus so I couldn't put it back the way it was. I thought no problem."I will just go back to synaptic, select the completely remove program option, reinstall it, and all the default settings would be restored", and that would have worked fine except for one huge problem. Even though I selected the option to completely remove the program, It still held on to all the scores, profiles, and yes even the black screen of death that I had created. I can get around in the menu to an extent (It's like a blind man trying to navigate through a room he had only been in a few times) but theres no way I'm going to be able to find the check boxes that I had to click to create the situation in the first place, but I'm not worried about that. There's a hundred games to try out, and I'm not one to play a whole lot of games anyways. Whats bothering me is the fact that even after I got rid of this program it still held onto it's configuration file. Where would the file be? Is there a way I can keep this from happening again? Did I do something wrong, or is it just the way things are?

---

### Post by Raineer on 2007-07-01
Eh, well the command line version would be:
```
sudo apt-get remove xmoto --purge
```
But I have a feeling synaptic has done that, I'm sure it's made a hidden directory in your home folder you should look for. It likely has the display settings that are messing you up

---


---
title: "no off button gutsy"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Roofie on 2007-10-15
i installed the newest ubuntu yeasterday gutsy.
Today i noticed i have no off button.
I myself can use the terminall to shut down the system but really would like to get the button back.
Can anyone give me some idea of what i can do 
Thanx

---

### Post by Daveth on 2007-10-15
well, if it is anything like feisty, right click the panel at the top (nr the clock), "add to panel", and the "Quit" button should be in the options listed. Just click on it to put it back.

---

### Post by Roofie on 2007-10-15
Ok my bad i should of explained a little better ...sorry
The quit button is there when i click it opens there is hibrinate,logout,lock screen,suspend,switch user.
There is no turn off ?
I just installed yeasterday i thought there was a button there that said turn off

---

### Post by Daveth on 2007-10-15
you have an advantage over me in that i have not yet seen Gutsy, but if like feisty then there is a "shut down" button over the "cancel" option.....

---

### Post by wormser on 2007-10-15
> **Roofie said:**
> Ok my bad i should of explained a little better ...sorry
The quit button is there when i click it opens there is hibrinate,logout,lock screen,suspend,switch user.
There is no turn off ?
I just installed yeasterday i thought there was a button there that said turn off

It sounds like a bug or some config file is messed up.  I do not have the answer but you can shutdown and reboot by the command line for now until it is resolved.

```
sudo halt
sudo reboot
sudo shutdown -h now
sudo shutdown -r now
```

Gusty is still beta and it might get resolved with the official release.  Maybe somebody else knows how to fix it now.

---

### Post by Officer Dibble on 2007-10-15
C'mon guys stop messing around now... give him his button back... who's got his button... c'mon, own up.... :D

---

### Post by Roofie on 2007-10-15
Ok i used sudo halt earlier so i geuss i will wait for a couple days to see what happens.
I did notice the release date,but didnt clue in that this version was beta.
Well i have to say gutsy is sure a sweet system and cant wait for the new release.
I just use linux, im no master by far.
Thanx for reply

---

### Post by vincentvee on 2007-11-11
dude
have had the same problem before, there was a config file that could be edited, but i forget where......also, just downgraded from gutsy cause it gives me problems) and i have this same problem again in feisty, no shutdown or reboot button, no problems to get it to shutdown but i would really like my button back too......
let me know if you find a solution

> **Roofie said:**
> i installed the newest ubuntu yeasterday gutsy.
Today i noticed i have no off button.
I myself can use the terminall to shut down the system but really would like to get the button back.
Can anyone give me some idea of what i can do 
Thanx

---


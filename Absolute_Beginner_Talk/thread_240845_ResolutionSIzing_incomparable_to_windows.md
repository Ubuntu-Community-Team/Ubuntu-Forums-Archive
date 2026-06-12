---
title: "Resolution/SIzing incomparable to windows?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Matt827 on 2006-08-21
Okay, this is my first hour on using this new OS. Used windows for a very long time. I have my Video Card drivers installed, restarted and everything is working as intended. 

Everything seems huge in comparison to windows however. my max resolution i can get off of this is 1024X764 on windows with the same card i get 1280X1024. Perhaps i'm using an outdated driver? or is my ATI Radeon X800 XT no good to run a ubuntu OS correctly?

How would i find out? haha, i'm very new to this so i apologize for my lack of knowledge!

I feel like im running my windows system through foreign dos prompts!

---

### Post by Ziox on 2006-08-21
> **Matt827 said:**
> Okay, this is my first hour on using this new OS. Used windows for a very long time. I have my Video Card drivers installed, restarted and everything is working as intended. 

Everything seems huge in comparison to windows however. my max resolution i can get off of this is 1024X764 on windows with the same card i get 1280X1024. Perhaps i'm using an outdated driver? or is my ATI Radeon X800 XT no good to run a ubuntu OS correctly?

How would i find out? haha, i'm very new to this so i apologize for my lack of knowledge!

I feel like im running my windows system through foreign dos prompts!

try this command, and pay special attention to the part where you can choose your resolution:

sudo dpkg-reconfigure xserver-xorg

after that command, kill X by hitting ctrl+alt+backspace

---

### Post by Matt827 on 2006-08-21
i take it you mean for me to kill the command after i go through all the menu items and all that stuff it brings up?

It brought me to the config and all that and is asking me to autodetect my video card and stuff like that. So does this mean my driver's are not installed correctly if it has to detect it? Or is this the normal procedure which i have to go all the way through to get to the resolution thing?](*,)

---

### Post by Ziox on 2006-08-21
> **Matt827 said:**
> i take it you mean for me to kill the command after i go through all the menu items and all that stuff it brings up?

It brought me to the config and all that and is asking me to autodetect my video card and stuff like that. So does this mean my driver's are not installed correctly if it has to detect it? Or is this the normal procedure which i have to go all the way through to get to the resolution thing?](*,)

yes, kill after the sudo dpkg-configure xserver-xorg command is done, and this procedure is not "normal", but it is the easiest way to change resolutions and stuff...the "normal" should be out-of-the-box, perfect resolution...we're not there yet, but we are getting close ;)

---

### Post by Matt827 on 2006-08-21
alright, Went through the entire thing. Selected 1280X1024 as the best video settings, but the resolution (as stated by the Resolution section in System->preferences->resolution) is still on 1024X764

Should it have forced it into a different video mode?

---

### Post by Matt827 on 2006-08-21
im going through it again.

last time i made it to the screen stating for me to select and add all of the Resolutions i wanted. I arrowed down to 1280X1024 and hit enter... I dont think that's what i wanted haha. How would I add multiple resolutions to that list? (annoted by the '*" between the brackets.) If you hit enter it takes you to the next screen. I want to see the * in the brackets before i continue to make sure it realizes i want to use that setting. but i dont know what to press! lol@my lack of knowledge on this

---

### Post by avtolle on 2006-08-21
I believe you select with the spacebar; try it and see what happens.

---

### Post by Matt827 on 2006-08-21
yepp that worked Thanks!

---


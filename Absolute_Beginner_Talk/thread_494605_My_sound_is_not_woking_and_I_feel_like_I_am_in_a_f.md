---
title: "My sound is not woking and I feel like I am in a foreign land"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by wilste on 2007-07-07
Hi... I am a complete newbie and am not that good with computers in general - but I have miraculously managed to install Linux and get it to start working (which for me is quite impressive)...But I am having a problem with the sound. i have tried looking at the site and it all looks like a complete different language for me.. Is there anyone who us able to give me step by step instructions as if they were talking to a two year old as i am reallly drying to get this to finally start working. 

My laptop is a Toshiba satellite a200-1ag and I my soundcard is intel...

Cheers (Thanks alot!!)

---

### Post by robertc36 on 2007-07-07
Double click volume icon-check switches tab and make sure that it is set to analogue (worked for me).
To test sound go to system/preferences/sound

---

### Post by wilste on 2007-07-07
Thanks for the reply - O.k just tried that but ir does not give me the option of analogue sound only:

Headphone
Caller ID and
off hook

:(--

---

### Post by robertc36 on 2007-07-07
Just uncheck if there is an option for digital/analogue and then test

---

### Post by wilste on 2007-07-07
ok .. It does not have that option so there isn´t a box for me to uncheck... I just tested sound and it is still not working

---

### Post by robertc36 on 2007-07-07
Have a look at this post seems to be a fix for intel [http://mepislovers.org/forums/archive/index.php/t-4721.html](http://mepislovers.org/forums/archive/index.php/t-4721.html)

---

### Post by nitro_n2o on 2007-07-07
open a terminal (the black little window) and type this ```
speaker-test
``` if you can't hear anything types this ```
alsamixer
``` it should tell you the name of the sound card and give the option of changing something... If you can't find the sound card name that's another problem

The analogue option should be in the file menu

---

### Post by wilste on 2007-07-07
Hi nitro - ok i tried speaker test and no sound played .. but I types in alsamixer and now have a menu.. What can I do from here? Thanks for the help

---

### Post by robertc36 on 2007-07-07
What is the name of your card?

---

### Post by wilste on 2007-07-07
Robert - it is a &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC861-VD                                                      &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Off-hook [Off]

---

### Post by robertc36 on 2007-07-07
[http://ubuntuforums.org/showthread.php?t=440251&highlight=Realtek+ALC861-VD](http://ubuntuforums.org/showthread.php?t=440251&highlight=Realtek+ALC861-VD) there is asolution here for your chipset
also some pointers here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).
I know this can be frustrating at first but having problems to solve and work out will get you used to OS quicker.

---

### Post by wilste on 2007-07-07
The only problem - is that I have no idea how to understand basic instruction such as:
[B]
  [I][I]  *[

      install the required tools

sudo apt-get install build-essential ncurses-dev gettext[/B]

I have no idea what that means!!
Thanks for all your help so far!

---

### Post by Swab on 2007-07-07
Enter that command in a terminal (application > accessories > terminal)

Then type:
sudo apt-get install build-essential ncurses-dev gettext

It will ask for your password, so type that and press enter.

---


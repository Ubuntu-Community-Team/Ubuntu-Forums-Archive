---
title: "Intel Setup"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Armaniboy on 2007-08-06
There is a link I'm using to get my intel sound card working. It's:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

However after you download the 3 files. You have to configure the directories. Now...I originally downloaded them and put them in a seperate folder. It looked like **home/vaughn/downloads** and then in there are the 3 files.

I don't know what command to type in the terminal to setup the directories. This step has me really baffled:

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
**[SIZE="5"]sudo cp ~/downloads/alsa* .[/SIZE]** (No idea what to type here)
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14a.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2

I know this is just a really easy fix for someone to tell me. Thanks.

-Armaniboy-:KS

---

### Post by nichipet on 2007-08-06
> **Armaniboy said:**
> **[SIZE="5"]sudo cp ~/downloads/alsa* .[/SIZE]** (No idea what to type here)

Is this the line that has you confused, and is it the only part causing confusion?

If so, it looks correct. The line is saying as the superuser copy everything in /home/myusername/downloads/ that starts with alsa to the current location. The . just means use where you are as the destination.

---

### Post by wolfen69 on 2007-08-06
this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards) has worked for me.

---

### Post by Armaniboy on 2007-08-06
When it says replace with your flavor...does that mean the model number?

-Armaniboy-

---

### Post by nichipet on 2007-08-06
From [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) :

cat /proc/asound/card0/codec\#*

---

### Post by Armaniboy on 2007-08-06
Thats the code I put in at the end of the list....

---

### Post by Armaniboy on 2007-08-06
I have no idea what that code is for or where I place it.

---

### Post by nichipet on 2007-08-06
The line starting with cat? From the terminal.

In Terminal, you'll see some writing ending with $ or $: (I'm not in Ubuntu, otherwise I would quote it from mine).

It may be something like myusername@mylocalhostname$: then on that line, paste the above line that starts with cat and post the output here.

---

### Post by Armaniboy on 2007-08-06
It says no such directory :(

---

### Post by Armaniboy on 2007-08-07
The sound on my computer is just really really soft. I used the alsamixer command and that didnt' work. Everything is also set to a high volume as well. I only get sound when my speakers are on a the highest turn...

---


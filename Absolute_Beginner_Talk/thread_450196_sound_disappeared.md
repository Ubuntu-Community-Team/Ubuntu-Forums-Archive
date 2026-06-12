---
title: "sound disappeared"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ymasarwar on 2007-05-21
i am using ubuntu 7.04,

yesterday i was doing some customization from ubuntu guide, and for some reason now i lost sound :(

can anyone help me out on this.

thanx

---

### Post by Lucifiel on 2007-05-21
Oh, first, could you tell us what sound card you have?

---

### Post by ymasarwar on 2007-05-21
it is a standard sound card in my Gateway Laptop.

---

### Post by Lucifiel on 2007-05-21
> **ymasarwar said:**
> it is a standard sound card in my Gateway Laptop.

Without knowing the sound card model, we can't help you. There's Sound blaster live, AC97 and a lot of different sound cards out there. 

Try seeing if there's a sticker on your laptop and see if the sticker tells you what sound card you have.

---

### Post by ymasarwar on 2007-05-21
well there is no sticker,and i think there is a command from where we can find out the hardware list, i dont know that command, can anyone tell me that so i can post my sound driver here.

anyways, when i try to run a movie player, this is what i am getting

*The requested audio output was not found. Please select another audio output in the Multimedia Systems Selector.*

---

### Post by Lucifiel on 2007-05-21
A solution to try:

Check the volume control panel and see if PCM is muted. 

If you can't find PCM, go to Edit----> Preferences in your Volume Control Panel. Scroll until you see "3d control-switch". "PCM" should be directly below that option. Select "PCM" and "Close" "Volume control preferences".

---

### Post by Lucifiel on 2007-05-21
> **ymasarwar said:**
> well there is no sticker,and i think there is a command from where we can find out the hardware list, i dont know that command, can anyone tell me that so i can post my sound driver here.

anyways, when i try to run a movie player, this is what i am getting

*The requested audio output was not found. Please select another audio output in the Multimedia Systems Selector.*

Try "lshw". Hmmm... about the movie player thingy, I'm stumped. Can't help you on that, sorry.

---

### Post by Lucifiel on 2007-05-21
Also, check to see if your Volume Control Panel has selected the correct device. Go to File---> Change Device and see if your sound card is listed there.

---

### Post by ymasarwar on 2007-05-21
what is a Ishw :o

---

### Post by ymasarwar on 2007-05-21
i trued to setup this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA)

i think this might be the problem, do u know how to roll back this,

and i checked all of those things u said, all of them are allright

---

### Post by Lucifiel on 2007-05-21
> **ymasarwar said:**
> what is a Ishw :o

Sorry, my bad. :p 

Try pasting the command "lshw" into Terminal.

To bring up Terminal, go to Applications ======> Accessories ======> Terminal .

---

### Post by ymasarwar on 2007-05-21
thanks guys, i figured out, i had to roll back the mistake i did .:D

---

### Post by Lucifiel on 2007-05-21
> **ymasarwar said:**
> i trued to setup this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA)

i think this might be the problem, do u know how to roll back this,

and i checked all of those things u said, all of them are allright

Right, then just do "gedit ~/.asoundrc" in Terminal and remove those lines you added.

---


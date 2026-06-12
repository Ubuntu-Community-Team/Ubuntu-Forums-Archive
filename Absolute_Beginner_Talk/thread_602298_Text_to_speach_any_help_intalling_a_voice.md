---
title: "Text to speach any help intalling a voice ?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-11-04
cant see any voices ?????  when i go voices add - select festival - it flashes some message up quickly the thats it ... what do i do ???

---

### Post by Soarer on 2007-11-04
Voices for Festival are in the repositories. Search for 'festvox' in Synaptic - make sure you have the 'Universe' repo enabled. 

I've never used it but I imagine once they are installed you will be able to select them.

---

### Post by tbskinn on 2008-01-25
I am having the same problem with Festival there seems to be no voices installed. I am not sure how to install them either i think it has something to do with festvox but i don't know how to install that after i download it. As you probably cam see I am new to Ubuntu any help in the right direction would be great.

---

### Post by dherath10 on 2008-02-28
root@Daminda:/home/toor# festival

WARNING
No default voice found in ("/usr/share/festival/voices/")
either no voices unpacked or voice-path is wrong
Scheme interpreter will work, but there is no voice to speak with.
WARNING

Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival>

How do I install voices??????

---

### Post by Soarer on 2008-02-28
You can install voices from Synaptic Package Manager.

They all start with 'festvox' - you can search for that & install the one(s) you want.

---

### Post by dherath10 on 2008-02-28
festival> (SayText "type the text you want to hear over here")
Warning: format is changed to S16_BE
#<Utterance 0xb70ebc28>

These is a problem.

---

### Post by mikeym on 2008-03-14
I know this is a bit late but I had to set mine up for using ALSA sound from the following guide [https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)

I then added a command for my window manager to read the selected text with

```
echo "(SayText \"`xsel -o`\")" | festival
```

you can also select a voice of your choosing first with a command more like:

```
echo "(voice_my_voice) (SayText \"`xsel -o`\")" | festival
```

---

### Post by cwmoser on 2008-03-14
I installed a couple of the American voices in the repositories.

What are the names of these voices?  Is there a command to list the voices currently loaded?

From the help command, I note that I can do the default voice....

festival> (voice_ked_diphone)  

... but what do I use for the voices I installed?

Thanks

Carl

---


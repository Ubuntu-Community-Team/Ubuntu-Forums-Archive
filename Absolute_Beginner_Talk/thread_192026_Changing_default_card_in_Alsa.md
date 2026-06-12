---
title: "Changing default card in Alsa"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by vicrp on 2006-06-08
I have two sound cards in my machine.  I, somehow, changed the Alsa Mixer settings to use my Sound Blaster card instead of the onboard Intel card. 

I do not understand how to access the options in Alsa.  All I want to do is set the sound card back to default, "0".

Thanks in advance...

---

### Post by Sutekh on 2006-06-09
The best way would to be to create an ~/.asoundrc file.  Double check that the card you want to use is card 0, using this command from the Terminal (Applications -> Accessories menu)
```
cat /proc/asound/cards
``` 
Then use this command  to create the .asoundrc file
```
gedit ~/.asoundrc
``` Then paste in these lines
```

pcm.!default {
    type hw
    **card 0**
}
ctl.!default {
    type hw           
    **card 0**
}
```
This should set you up.

---

### Post by steve.horsley on 2006-06-09
System->Preferences->Sound

The default card selection is at the bottom

---

### Post by hachaboob on 2006-06-09
A panel applet would be much appreciated :)

---


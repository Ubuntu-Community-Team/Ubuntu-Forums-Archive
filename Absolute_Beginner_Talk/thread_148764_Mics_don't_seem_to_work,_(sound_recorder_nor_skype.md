---
title: "Mics don't seem to work, (sound recorder nor skype work)"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-22
I can't seem to get my microphones to work with the sound recorder nor skype.  I have 2 mics, and neither works.  They work fine with XP.  I have tried audacity with my mics, still the answer is no.  Running out of ideas, please help:confused: 
Maybe there's some setting in volume control that I don't understand or something?

---

### Post by Princey on 2006-03-22
What type of soundcard do you have? We can't help if you don't know the make or model of the soundcard

---

### Post by user1397 on 2006-03-22
It is a VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller
Thanks for the reply.

---

### Post by KansasJoe on 2006-03-22
first thing first make sure your mic is unmuted because by default it will be....next, type in alsamixer in terminal and you may need to turn on your mic boost (this is what i had to do) use arrow keys to scroll until you see mic boost and when you're on it hit m

---

### Post by user1397 on 2006-03-22
[QUOTE=KansasJoe]first thing first make sure your mic is unmuted because by default it will be....next, type in alsamixer in terminal and you may need to turn on your mic boost (this is what i had to do) use arrow keys to scroll until you see mic boost and when you're on it hit m[/QUOTE]
This seemed to turn on the mic sotospeak, but i still can't input... ](*,)

---

### Post by Princey on 2006-03-22
I'm not too familiar with that chipset as I'm somewhat biased towards SoundBlaster sound cards. I make sure I chose that type when building or configuring my systems. However, on my last Audigy one, I had problems getting my mic to work. I could hear it if I just upped the volume but wasn't working in skype. I had to go to the sound control (I'm not sure right now which I used as I'm on the Windows box in my workshop) but I had to first turn on microphone boost and check on the recording end. There are two or three options which includes output, input. I think that's where the problem might be. Check on the input and make sure the mic is enabled, boost turned on and volume up. 

Btw, if you try just speaking in the mic with the volume up, can you hear anything?

---

### Post by user1397 on 2006-03-22
Yes if I turn on my speaker and speak into my mic, sound does come out of my speaker.  I tried going into the volume control==>preferences and selected mic boost, and put it on mic1 (mic2 sounds all fuzzy)
Still, nothing happened.  I even went to Recording level monitor, which I guess is supposed to move if u say something on your mic, but when i do, nothing happens!
What else can I do?

---

### Post by user1397 on 2006-03-22
Maybe it would help if you could tell me your exact alsamixer settings?

---

### Post by Princey on 2006-03-22
[QUOTE=erik1397]Maybe it would help if you could tell me your exact alsamixer settings?[/QUOTE]

I can't say off the bat now as I'm downstairs in my workshop. When I get up I'll post it here. Try going to skype, options and sound devices. See if your sound card is selected or is there another option. That's what got mine working chosing the other option that was available.

---


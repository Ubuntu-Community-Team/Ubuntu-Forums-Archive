---
title: "Ubuntu atudio, Ardour and jakc, what do I do"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-06-23
So heres the deal, I'm trying to get ardour to load when all of the sudden it says it needs to connect to the Jack interface, whats the deal, do I need an internet connection, how do the Jack programs even work, now I'm lost.


Great release though. 

:popcorn:

---

### Post by WinterWeaver on 2007-06-23
I would also like to know ^_^ ... I was just fooling around with it, testing various programs... but cant test ardour.

---

### Post by LostArt on 2007-06-24
Bump,ooooh I just got chills

---

### Post by bazzer on 2007-06-25
Jack is the audio server that most programs communicate in ubuntu. You'll need to have it running before ardour will work.

But configuring it is a WHOLE other subject ;)

---

### Post by paulg on 2007-06-25
Some general information to get you started re: JACK since it sounds like you are unfamiliar with it.

You will see JACK (JACK Audio Connection Kit) referred to as a 'transport'. It's an audio server that makes it possible to 'patch', not unlike using physical patch chords, between programs and the ALSA driver (PCM I/O). I recommend you use qjackctl to start and stop jackd (the JACK daemon). Remember to press the 'play' triangle on the left to start the JACK server. You will probably need to do some messing around with the settings. Make sure you select the appropriate interface if you have more than one soundcard. You may want to find a howto or manual to learn it's basic functions or find someone using the same card who can help you with your configuration (try searching the forums, there is lots on the topic). Basically, if you see a lot of 'xruns' in the message log you probably need to increase the latency. 

Ardour is a really amazing, really powerful and probably a really complex program to wrap your head around if you try to use it without any prior knowledge. It may help if you have experience with other programs like Audacity, but Ardour, in my experience at least, has been a completely different beast. I highly recommend the manual which does an excellent job of outlining the basics and the only reason I have had any success running the program.

[http://ardour.org/files/manual/index.html](http://ardour.org/files/manual/index.html)

---

### Post by bazzer on 2007-06-26
Yeah that's a great link paul, thanks very much.

I've got issues atm with jack not outputting anything through the 'capture' connection. And I can't find any guide for Jack that allows me to diagnose the problem. Any ideas on a useful JACK tutorial?

---

### Post by paulg on 2007-06-27
Sorry, I don't have a link to a Jack tutorial/manual. I kind of futzed around with it using what little information I could garner from the forums until it worked for me(?). I still have some random xruns but that appears to the price of a USB interface

Have you looked at your connections to see if your PCM capture is being sent to an output? 
Is 'duplex' enabled in the settings? 

I am away from my computer now but that's off the top of my head. Also, to manage your connections in Jack have a look at the program called patchage. It does the same thing as the 'connect' tab in qjackctl but is a little easier to use and prettier.

---

### Post by bazzer on 2007-06-28
Ah, I worked it out yesterday - I stumbled across this: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/")
And I managed to futz about until I heard the monitored sound change from the line in jack I was hooked up to... Success!!

But now I realise that my latency issues mean I must purchase a better sound card. I'm thinking of something with a 5 1/4 panel, like an Audigy 2 or 4 perhaps? I'll have a look and maybe post a new thread about this if I can't find any proper info.

---

### Post by LostArt on 2007-06-30
Wow, sorry I have been really busy and couldn't get onto the forums, so just to make sure, all I have to do to get Ardour working is configure Jack on my computer, and I DO NOT need an internet connection

---

### Post by bazzer on 2007-07-02
> **LostArt said:**
> Wow, sorry I have been really busy and couldn't get onto the forums, so just to make sure, all I have to do to get Ardour working is configure Jack on my computer, and I DO NOT need an internet connection
Correct.;)

---


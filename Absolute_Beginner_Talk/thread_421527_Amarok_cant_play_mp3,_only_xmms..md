---
title: "Amarok cant play mp3, only xmms."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-04-24
Hi

The musicplayer xmms and vlc can play mp3 files, but not the player called amarok. What can I do? 


Thanks

_sAm_

---

### Post by crav on 2007-04-24
I just had to do this yesterday, here's the method that worked for me.

Navigate your way over to /usr/lib/amarok
Run "Install mp3"

That's it! I'm listening to mp3s right now.

---

### Post by _sAm_ on 2007-04-24
There is a document there called "install-mp3", and I cant "run" it? Could you tell me me what you did?

---

### Post by n3tfury on 2007-04-24
maybe he means navigating via the terminal and using that command there?  dunno since i don't use amarok, but sounds like it's what he meant.

---

### Post by crav on 2007-04-24
If you click it, you should get this message (see attachment)
click "Run"

That's what I did.

Alternatively, you should be able to do this:
(this is not the way i did it, so I cannot confirm)

```
 /usr/lib/amarok/install-mp3 
```

again, I can't confirm this will work.

---

### Post by _sAm_ on 2007-04-24
Thank you both for your answer:-)

I didnt get the message that you are posting(but I am running Kubuntu if that are different here), but I tried the command you wrote in a terminal and now it works like a dream:) 

So nice :guitar:

---

### Post by crav on 2007-04-24
I'm glad I could help. I try to avoid the terminal if I can, so I feel awesome knowing I made a terminal command work.

amaROK ON
:guitar:

---

### Post by amaroKer on 2007-05-01
Worked for my buddy too...

Is there a way to make this fix widely known?

---

### Post by cqnunez on 2007-05-18
A friend of mine just had the same problem. We tried using command and it didn't seem to work. But we were able to "run" the file and it finally worked... This support forum is really GREAT!!! Thanks! :KS

---

### Post by FreewheelinFrank on 2007-09-20
I've just had a similar problem.

Clicking on a certain album in the Amarok collection  jammed up Amarok, sometimes with a message about MP3 support.

I tried to run the script but got an error message.

Read though the script and found it just installs this library:

libxine1-ffmpeg

Installed the library through Adept and Bingo!

---

### Post by maryjanua on 2007-09-20
how interesting and helpful these forums are thanks very much guys i was wondering how to play mp3s in amarok=D>=D>:KS

---

### Post by khalid1100 on 2007-10-13
Guys I love this forum. Hands up for linux

---

### Post by cory_k on 2008-01-09
Hi, just wanted to say I was having the same troubles with mp3 support in amarok, but after doing

sudo apt-get install libxine1-ffmpeg

it works like a charm!  Thx for all the help!

---

### Post by Paqman on 2008-01-09
> **amaroKer said:**
> 
Is there a way to make this fix widely known?

Amarok *should* run the mp3 script automatically the first time you try and play an mp3. You only need to do this manually if that didn't happen for some reason.

---


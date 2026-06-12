---
title: "how do i make my mic work ?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-21
hello guys, 

my headphone wasnt working couple of days back but i made it work with the help of ubuntu community .. one thing that wasnt fixed was my mic.. now i went to alsa mixer and checked off the mic box.. it still doesnt work.. is there any alternative.. if so, what is it ? help is always appreciated.. thanks !

---

### Post by cowlip on 2007-03-21
Have you tried checking anything else?  Like Line In, Line, etc?  And also ensuring the input's volume is not set to mute or too low to hear.

If it stil doesn't work, what's your soundcard called?

---

### Post by HunkieChan on 2007-03-21
> **cowlip said:**
> Have you tried checking anything else?  Like Line In, Line, etc?  And also ensuring the input's volume is not set to mute or too low to hear.

If it stil doesn't work, what's your soundcard called?

i dont have line .. i have linein though.. yes they are checked and the are all high

---

### Post by HunkieChan on 2007-03-21
ok i just realized something.. i guess "Capture" is the mic.. so i unmuted it and closed the window but when i reopen the window "Capture" is mute somehow.. whats the problem ?

---

### Post by HunkieChan on 2007-03-21
okay i found another thing.. i opened sound recorder and i had the "capture" window side by side.. this is where it gets creepy.. whenever i press the record button.. "capture " gets mute.. . iis there a solution ?

---

### Post by cowlip on 2007-03-21
That's happened to me before, I just can't remember the solution but I can use my mic.  So be hopeful, I'm sure someone will help.  Does installing the sound capturer program Audacity help at all?  It has its own volume control IIRC, so you could choose "capture" and see what happens right away.  Just install it from Add/Remove programs.

Do you know if changing to OSS/ALSA/ESD under System->Preferences->Sound help at all?

(I have a Soundblaster Live card)

---

### Post by HunkieChan on 2007-03-21
> **cowlip said:**
> That's happened to me before, I just can't remember the solution but I can use my mic.  So be hopeful, I'm sure someone will help.  Does installing the sound capturer program Audacity help at all?  It has its own volume control IIRC, so you could choose "capture" and see what happens right away.

Do you know if changing to OSS/ALSA/ESD under System->Preferences->Sound help at all?

(I have a Soundblaster Live card)

i dont have audacity.. will that help ?

---

### Post by chaplanger on 2007-03-21
> **HunkieChan said:**
> i dont have audacity.. will that help ?

Audacity might be a solution for you.  In my case I could never get the "Sound Recorder" to work properly (it has always recorded at hyper speed -- like listening to the "chipmunks" of old).  Audacity though works just fine. 

 One caveat I found . . . when recording turn down your speaker sound to avoid feedback.  When listening to play back from your recording, mute the mic.

---

### Post by HunkieChan on 2007-03-21
> **chaplanger said:**
> Audacity might be a solution for you.  In my case I could never get the "Sound Recorder" to work properly (it has always recorded at hyper speed -- like listening to the "chipmunks" of old).  Audacity though works just fine. 

 One caveat I found . . . when recording turn down your speaker sound to avoid feedback.  When listening to play back from your recording, mute the mic.

i just wana use it for skype.. do you think it might help ?

---

### Post by HunkieChan on 2007-03-21
okay there is a problem.. i got audacity but. it game me error when i  FIRST started it.. something like not supoorted with audo i/o . not sure what it was.. but i closed it and restarted it.. i didnt get the error. but the problem is when i press record.. after few seconds.. audacity closes automatically.. only when i press record though. can anyone help ?

---

### Post by cowlip on 2007-03-21
I don't think mine has ever crashed on record, but I have gotten that error message before and still ended up getting it to work at some point.  Did you also try to switch OSS/ALSA/ESD under System->Preferences->Sound at all?  Sometimes one works better than the other. 

Try this in a terminal and reply back with the output:
lsmod | grep snd

---


---
title: "why i cant make conference call (skype)"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-26
my sound work properly i dont have problem with my sound card. thats the only problem .
*im using ubuntu 6.06

---

### Post by AtrejuT on 2007-03-26
as far as I know this is not supported by skype on linux - I might be wrong though...
can you make regular calls?

---

### Post by fanny on 2007-03-26
yes of course . i am making reguler calls.

---

### Post by AtrejuT on 2007-03-26
well I was wrong skype _does_ seem to support conference calls on linux.
What exactly does not work if you try making a conference call?

---

### Post by fanny on 2007-03-26
actually now nothing works, i cant make conversation at all. cause i tried to change some setting . i followed this instruction  [http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_i](http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_i).
but any way before this , if i try to add a person to the conversation i need to suspend one, and move to another.

---

### Post by AtrejuT on 2007-03-26
For the sound the first thing to do would be running 
```

alsamixer

```
and checking if master and pcm are unmuted and at a reasonable level.
For me to make conference calls I can right click on a person in my address book (while already making a call) and selecting 'invite to conference call' or so.
What is your version of skype? (Mine is 1.3.0.53)

---

### Post by fanny on 2007-03-26
see this print screen i dont understand allot.
my skype version is 1.3.0.53

---

### Post by eljalill on 2007-03-26
You can also check the volumes through double clicking on the speaker icon in the gnome panel... I personally like that better than alsamixer.

---

### Post by AtrejuT on 2007-03-26
you could turn up pcm more (left arrow to go there, up arrow to change) but it should be ok.
You don't get any kind of sound I assume? like play back audio files or so?

---

### Post by fanny on 2007-03-26
i can listen to music and do anything with sound. just cant make conference all ,and and now after i changed the settings icant make calls at all.

---

### Post by AtrejuT on 2007-03-26
ok, so what do you try to do to make phone calls, and at what point exactly do you run into problems? I'll need a slightly more detailed description here...

---

### Post by fanny on 2007-03-26
i pick a person . call him and after onr ring i have a message  say: problem with the sound device.

---

### Post by AtrejuT on 2007-03-26
Mhm, I have to admit I've never seen *that* before.
Can you start skype from a terminal, try calling someone and see if it gives any more details on the console?

---


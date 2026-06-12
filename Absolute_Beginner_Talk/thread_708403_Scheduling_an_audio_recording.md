---
title: "Scheduling an audio recording"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Cullen on 2008-02-26
I am trying to set my computer to begin a recording at a specified time each morning.  I have no idea where to begin.  Anyone have any thoughts?

---

### Post by herbster on 2008-02-26
What are you trying to record exactly? Are you using your microphone to record audio or trying to capture a stream of some kind?

---

### Post by Oldsoldier2003 on 2008-02-26
> **Cullen said:**
> I am trying to set my computer to begin a recording at a specified time each morning.  I have no idea where to begin.  Anyone have any thoughts?



create a file for your cron job. name it whatever you like. save it in your home dir for convenience in editing and reloading it.

in the crontab file

30 3 * * *      /full path to whatever-command- you- need- to- run


would run the command you specified at 330 am every morning.

man cron goes into more detail  and there are many tutorials on the web, Google crontab for a selection 

Then:

crontab -u <your username> <your cronfile>
crontab -l to make sure it was loaded.

all done. (assuming you did not disable the cron service on your machine)

---

### Post by Cullen on 2008-02-26
Essentially I am trying to record from the microphone.  Long story short I am recording a radio show, using an actual radio with a cord from the radio headphone to the computer line in.

---

### Post by Oldsoldier2003 on 2008-02-26
> **Cullen said:**
> Essentially I am trying to record from the microphone.  Long story short I am recording a radio show, using an actual radio with a cord from the radio headphone to the computer line in.
substitute the time you need and the commandline to launch your recording app in the crontab and you're golden. you'll have to walk back and turn it off though...

---

### Post by herbster on 2008-02-27
You can try this:

```
arecord -d 10 -f cd -t wav -D copy radio.wav
```

Now, where it says "-d 10," the 10 is the length in seconds you want to record. Let's say you have an hour long radio show, you'd simply make that figure 3600. The "-D copy" is the PCM device you're using to record with. I'm guessing for you it's /dev/dsp1, so try to replace "copy" with "/dev/dsp1". This may take some tinkering, but it's a matter of running the command and trying to record a sound like your voice or something just to test which device it is.

The easiest way is probably to do "sudo apt-get install audacity" and then run audacity, hit the record button, talk and play it back. Do you hear your voice? Then go to Edit > Preferences > Recording device and see which one is selected.

Then we can add the command to a cronjob.

---


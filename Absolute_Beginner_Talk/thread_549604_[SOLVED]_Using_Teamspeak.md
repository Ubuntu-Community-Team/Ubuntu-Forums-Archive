---
title: "[SOLVED] Using Teamspeak"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by RedGreen on 2007-09-12
I have been able to install TeamSpeak but when I connect to a server I notice that my mic and headphones are muted and I am unable to unmute them. Any ideas?

---

### Post by Maestro23 on 2007-09-12
> **RedGreen said:**
> I have been able to install TeamSpeak but when I connect to a server I notice that my mic and headphones are muted and I am unable to unmute them. Any ideas?

Open a terminal:

> alsamixer

See if anything is muted.

---

### Post by BLTicklemonster on 2007-09-12
Sound in Ubuntu is a major complication. I had to go forever trying to figure out how to get my settings in alsa just right to have my headset work. 

Good luck!

---

### Post by RedGreen on 2007-09-12
> **Maestro23 said:**
> Open a terminal:



See if anything is muted.

I wasnt really sure what I was looking at but the vars LFE and Line were black so I raised the volume there. After starting TS my mic and headphones are still muted.

---

### Post by Maestro23 on 2007-09-12
> **RedGreen said:**
> I wasnt really sure what I was looking at but the vars LFE and Line were black so I raised the volume there. After starting TS my mic and headphones are still muted.

The "M" key toggles the Muting under each bar. Did you try that?

---

### Post by RedGreen on 2007-09-12
> **Maestro23 said:**
> The "M" key toggles the Muting under each bar. Did you try that?

Okay I tried to unmute anything that looked remotely correct but I am still unable to unmute myself in TS.

Is there somewhere where I can find a description of what each of those bars corresponds to?

---

### Post by Maestro23 on 2007-09-12
> **RedGreen said:**
> Okay I tried to unmute anything that looked remotely correct but I am still unable to unmute myself in TS.

Is there somewhere where I can find a description of what each of those bars corresponds to?

Go with what BLTickle posted.

---

### Post by BLTicklemonster on 2007-09-12
Double click on the speaker on your panel.

Look to see that Microphone is listed, and doesn't have a red x over the icon at the bottom of it, and make sure the slider is over half way up.

Look to see that Master volume is up, also.

(you are sure you have the headset plugged in correctly, no?)

Now go to edit, and click preferences.

If you didn't see microphone in the first step, enable it here. Also mic boost isnt' a bad idea. You can activate it from the original panel by clicking on "switches".

Don't have ac97 turned on. That messed me up something fierce one time.

---

### Post by RedGreen on 2007-09-12
I made sure everything was set up as you suggested all the bars are high enough that it should work fine but my mic still refuses to function.

---

### Post by splintercellguy on 2007-09-12
The solution: alsa-oss

sudo apt-get install alsa-oss

Then run TeamSpeak with the aoss wrapper:

aoss "/path/to/TeamSpeak/binary"

---

### Post by RedGreen on 2007-09-12
> **splintercellguy said:**
> The solution: alsa-oss

sudo apt-get install alsa-oss

Then run TeamSpeak with the aoss wrapper:

aoss "/path/to/TeamSpeak/binary"

sorry im still figuring all this out. In order to get it to run in the aoss wrapper what exactly do I type.

Is it:

 > aoss /home/user/TeamSpeak2RC2

I dont see a binary in that file. Could you dumb down the instructions a little bit?

---

### Post by splintercellguy on 2007-09-13
aoss ~/TeamSpeak2RC2/TeamSpeak

TeamSpeak2RC2 is a directory containing the desired binaries.

---

### Post by RedGreen on 2007-09-13
> **splintercellguy said:**
> aoss ~/TeamSpeak2RC2/TeamSpeak

TeamSpeak2RC2 is a directory containing the desired binaries.

That got TS working...sort of. I am not having a lot of issues getting my headset to work correctly. I can change settings and get it working (although the output is never adequately loud for anyone trying to hear me) but from one minute to the next things will change and my mic will stop working.

I have also noticed when I go into alsamixer the volume bars seem to like changing themselves.

---


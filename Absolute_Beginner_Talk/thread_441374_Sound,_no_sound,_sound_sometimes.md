---
title: "Sound, no sound, sound sometimes"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-12
I've run the procedures in the Comprehensive Sound Solutions thread almost hourly.  If I'm working on some other config that requires a boot, sound is lost.  I run the sound procedures.  Amorok blows up and no sound.  Run the procedure again.  Sound in some modules.  No sound on DVD using xine.  Rythm Player works, VCL works, xine doesn't, Amorak doesn't.

Then all the sound is lost so I redo the procedure.  If I reboot, I may hear the login sounds.  That usually means everything may work.  If not I run the procedure again and reboot.  No sound.

This process repeats over and over.  I've had to give it up for a while so I can get to other things.

In all cases, my card is recognized as well as the drivers.  What works mostly, sort of is only running

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

Sometimes I don't have to reboot, sometimes I have to.

I've yet to get all modules with sound to play.

My card is a Creative Labs Audigy LS with driver ca0106. It's never given me a problem before.  As I add more software, such as Lightning and Contacts_Side bar to TB2 I find more things begin to run poorly.

Very frustrating.
bobland

---

### Post by DerArzt on 2007-05-12
does your computer also have an integrated sound card, and if so is it disabled in bios? ive often had problems with my sound card because the integrated one would confilct.

---

### Post by BobLand on 2007-05-12
I'm not aware.  It's an old card and one that was pushed out by Creative that offered decent gaming, 3D and that sort of thing.  It was probably around $50.  I bought it because it was cheap.  No docs, no support pages.

I don't think it's the card, more like some driver not turned on or off.

---

### Post by dbott67 on 2007-05-12
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 7 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

So, try creating a new user account and logging in.  If your sound troubles disappear, then it's likely the .asoundrc file.

-Dave

---

### Post by BobLand on 2007-05-12
I don't have a .asoundrc file anywhere on my system.  I tried some of the tips at the end of the Comprehensive... but they didn't work either.

The test tones show my drivers are "not connected."

Guess this will be a summer long project.

---

### Post by dbott67 on 2007-05-12
Can you post the output of:
```
dbott@feisty:~$ [COLOR=Red]**sudo lshw -C multimedia**[/COLOR]
  *-multimedia            
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: a
       bus info: pci@02:0a.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
       resources: ioport:b800-b81f irq:22
```

Did you also try creating a different user account and logging in?

-Dave

---

### Post by BobLand on 2007-05-13
Dave,
I tried a number of things last night but finally gave up and went to bed.  When I got up this morning I realized that I could hear the test tones and output from Rhtthmbox but not the xine player or Amarok.  Since Amarok uses the xine engine I first tried updating xine related from Synaptic.  That didn't do anything different.

I did add a user with root rights, checked the various files to see if the card and driver were detected.  All were correct.  Ran Amarok.  Got the infamous "No Demux Plugin" error.  Searched for that string and found the answer: no extra codecs so I ran:

sudo apt-get install libxine-extracodecs  - important! REBOOT

Restarted Amarok and Walla: sound!  Tried playing a CD with xine:  Sound!

BTW, no .asoundrc was found in my directory or the added user's directory.
Hope this helps someone else.

Added/Edited:  I stil get the occasional "No Suitable Demux..." message so I will continue to keep a lookout for more codecs.

Thanks,
bobland

---


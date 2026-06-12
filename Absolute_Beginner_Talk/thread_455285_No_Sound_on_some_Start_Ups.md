---
title: "No Sound on some Start Ups"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by azoutback on 2007-05-26
Sometimes when I start Ubuntu I seem to have no sound.  Volume is on and to the max.  Other times I startup I have sound.  Using a SoundBlaster PCI512.  I also have (but I think it is disabled, onboard sound card via the motherboard).

Here is my Sound Preferences screen:
[http://i104.photobucket.com/albums/m195/ffextensionguru/Screenshot-SoundPreferences.png](http://i104.photobucket.com/albums/m195/ffextensionguru/Screenshot-SoundPreferences.png)

---

### Post by dbott67 on 2007-05-26
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by azoutback on 2007-05-26
Cool I will that a shot later this evening and see what happens.  Thanks

---

### Post by azoutback on 2007-05-27
Now this morning I booted up fine with sound,:o

---

### Post by azoutback on 2007-05-27
Had problems when I came back from WinXP.  Did not have the .asoundrc file mentioned.  Did follow some steps in the Comprehensive Guide and it appears to be working (for now).

---


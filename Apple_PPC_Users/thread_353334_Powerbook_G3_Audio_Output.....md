---
title: "Powerbook G3 Audio Output...."
date: 2007-02-04
forum: Apple PPC Users
---

### Post by mdknaebel on 2007-02-04
Hi,

I have a PowerBook G3 Wallstreet edition running Ubuntu 5.10 and OS 9.

After getting Ubuntu 5.10 installed, I put some music onto the PowerBook.  However, in Ubuntu, sound plays only through the built-in speakers, regardless of whether or not headphones or speakers are plugged in to the audio output.  In OS 9, sound WILL play through the audio output when headphones are plugged in.  

Is there anything that can be done to fix this?

Thanks
(I don't know much about Linux...)

---

### Post by casfindad on 2007-03-28
Here's a couple suggestions:

1. Open Volume Control. (Right-click on the volume (speaker) icon in the top menu bar or select Applications>Sound & Video>Sound Recorder, then File>Open Volume Control.)

2. Under File>Change Device, make sure the correct sound device is selected. (I use ALSA on my Powerbook G4.)

3. Under Edit>Preferences, select Master, Headphone, Headphone Detection, PCM, PC speaker and any other tracks you want to be visible.

4. Close the Preferences window and select the Switches tab.

5. Make sure the Headphone and Headphone Detection boxes are checked.

6. On the Playback tab, make sure the Master and PCM volumes are set fairly high (ca. 80%).

Close Volume Control, and hopefully the headphone detection will work. If not, try a restart, then test again.

If this doesn't work, you can try messing around with more sound settings by running alsamixer in the terminal. (Search the forums for direction on this.)

Good luck!

---


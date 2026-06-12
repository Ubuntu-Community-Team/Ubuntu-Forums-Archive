---
title: "messed up decoders"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Cha1n5aW on 2008-02-18
I just got my java and frostwire runnin, downloaded an mp3, then when I double-clicked it in nautilus to play it, the "Movie Player" program opened, then it downloaded some GStreamer stuff, then gave me the following error...
```
"An error occured"
"The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed."
```
So, I decided to try it in Rhythmbox, which should be the default mp3 player program (not sure why movie player opened mp3 in first place).  When I try to import my ~/Music folder, I get the following error...
```
"The GStreamer plugins to decode "Unknown" files cannot be found"
```
and the only file in the ~/Music folder is the .mp3 file I downloaded.  Just to be sure it wasn't that particular file causing issues, I copied some known good mp3 files from other computers on my network to the folder, deleted the downloaded file and I still get the same error.
I'm sure I screwed something up because I played mp3 files perfectly fine from my mp3 player in rhythmbox a couple days ago.  I'm just not sure what exactly I screwed up.

Thanks for any help

- Shawn

---

### Post by randy78 on 2008-02-18
> **Cha1n5aW said:**
> I just got my java and frostwire runnin, downloaded an mp3, then when I double-clicked it in nautilus to play it, the "Movie Player" program opened, then it downloaded some GStreamer stuff, then gave me the following error...
```
"An error occured"
"The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed."
```
So, I decided to try it in Rhythmbox, which should be the default mp3 player program (not sure why movie player opened mp3 in first place).  When I try to import my ~/Music folder, I get the following error...
```
"The GStreamer plugins to decode "Unknown" files cannot be found"
```
and the only file in the ~/Music folder is the .mp3 file I downloaded.  Just to be sure it wasn't that particular file causing issues, I copied some known good mp3 files from other computers on my network to the folder, deleted the downloaded file and I still get the same error.
I'm sure I screwed something up because I played mp3 files perfectly fine from my mp3 player in rhythmbox a couple days ago.  I'm just not sure what exactly I screwed up.

Thanks for any help

- Shawn

You can check that the Restricted repository is enabled in Synaptic

---

### Post by Cha1n5aW on 2008-02-18
Thanks for the reply.  I seached synaptics for everything installed with "codec" in the name or description, marked it for reinstallation, now everything works fine.

- Shawn

---

### Post by jan quark on 2008-02-18
pleases mark solved threads as solved see signature thank you

---

### Post by randy78 on 2008-02-18
Cool
Glad everything is working for you ;)

---


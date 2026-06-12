---
title: "How to play a DVD"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by taco_truck on 2008-03-23
Can someone please tell me the easiest way to play a dang DVD in Ubuntu?

---

### Post by herbster on 2008-03-23
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I'd highly recommend VLC player:

```
sudo apt-get install vlc
```

---

### Post by marpstar on 2008-03-23
Easiest way for me to get started with DVD playback would be to open the DVD in Movie Player and it should prompt you to install restricted codecs.  Install the codecs and your DVD playback should be enabled.

---

### Post by taco_truck on 2008-03-23
VLC is installed...how do I play it now?

---

### Post by Ub1476 on 2008-03-23
Follow the instructions from the link herbster posted.

---

### Post by keratos on 2008-03-23
herbster has already told you.

open thy ears and follow the link

---

### Post by taco_truck on 2008-03-23
Those instructions did not help.

---

### Post by herbster on 2008-03-23
What doesn't help is not clearly and concisely telling us what did not help. What exact commands from the link I posted did you run and what was the output? Please paste what the terminal output was using [code] tags.

---

### Post by taco_truck on 2008-03-23
Ok got it, thanks for the help.

---

### Post by eragon100 on 2008-03-23
Get automatix via google. install the win32 dvd codecs from there. Open vlc and go to file -> disc.
A menu appears. If your dvd is already in the drive, simply select dvd, if that iption sn't already selected, and click open (or something like that) in the lower right corner of the vlc screen. The dvd menu appears.

---

### Post by herbster on 2008-03-23
Glad it worked taco_truck!

And do not get Automatix.

---

### Post by keratos on 2008-03-23
> **eragon100 said:**
> Get automatix via google. install the win32 dvd codecs from there. Open vlc and go to file -> disc.
A menu appears. If your dvd is already in the drive, simply select dvd, if that iption sn't already selected, and click open (or something like that) in the lower right corner of the vlc screen. The dvd menu appears.

BAD advice.

---

### Post by keratos on 2008-03-23
> **herbster said:**
> Glad it worked taco_truck!

And do not get Automatix.

Ditto that one.

Use synaptic and all codecs should be available however some are not installed by default due to "legal reasons"

Make sure the lines with "multiverse" in /etc/apt/sources.list are UNCOMMENTED.

Disregard the suggestion to install automatix because automatix should be used in extreme cases where specialised components are required that do not exist in the ubuntu repositories. Automatix is know to break ubuntu installs by rendering the package management system unstable.

Dont take my word, google it !! but DO NOT install and use it ..... as per herbster's advice.

---


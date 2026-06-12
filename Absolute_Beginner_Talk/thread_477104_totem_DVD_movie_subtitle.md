---
title: "totem DVD movie subtitle"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-18
when i play DVD movie using TOTEM it wont show me SUBTITLE, what plugin do i need ?????

---

### Post by ferronica on 2007-06-18
It plays DVDs automatically, but only plays them from the beginning to the end. No title screen, no menu, no chapters, no settings, no skipping around -- just straight play.  :( :(

---

### Post by onero on 2007-06-18
I haven't tried with actual DVDs, but when I play a video file with subtitles I just go to View > Subtitles > [subtitle name]. Sometimes it's listed as Unknown. Doesn't anything appear in this menu when you play the DVD?

---

### Post by RomeReactor on 2007-06-18
Hi. That's a problem when using totem-gstreamer (no menus and can't select subtitles); I recommend you install totem-xine. Look for it in Synaptic, or from the terminal (Applications-->Accessories-->Terminal) if you're using Feisty:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by ferronica on 2007-06-18
totem-gstreamer and totem-xine are different things or same i found TOTEM-XINE under add/remove

---

### Post by onero on 2007-06-18
> **ferronica said:**
> totem-gstreamer and totem-xine are different things or same i found TOTEM-XINE under add/remove

Same program but different engines. You should install totem-xine, it'll also remove totem-gstreamer. It's better if you just use the command that RomeReactor gave, because that would also install the codecs you need :)

[I keep forgetting that I changed to totem-xine, should have mentioned it from the get-go :p]

---

### Post by ferronica on 2007-06-18
many thanx RomeReactor and onero TOTEM-XINE worked great for DVD :) :)

---


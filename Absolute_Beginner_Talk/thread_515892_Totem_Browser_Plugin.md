---
title: "Totem Browser Plugin"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-08-02
I am having some trouble playing video files in firefox. I recently had to do a fresh install of Ubuntu and when I tried to get back all the programs... I think I may have forgotten something. I am attempting to play .mov trailers from the apple website in firefox. I had them going before, so I know its possible. I can download them and play them in totem or vlc fine, but I can't seem to get them to stream in the page. I get the play icon, ticker, etc. but all I get is a black screen. Any ideas. I also know that the browser has Totem Browser Plugin 2.18.1 installed. Any suggestions?

---

### Post by atomkarinca on 2007-08-02
have you tried mozplugger?

[http://mozplugger.mozdev.org/](http://mozplugger.mozdev.org/)

---

### Post by aysiu on 2007-08-02
The Totem plugin stinks. 

**Step 1**:
Remove it by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove totem-mozilla
```

**Step 2**:
[Make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources)

**Step 3**:
Install the MPlayer plugin instead: ```
sudo apt-get update
sudo apt-get install mozilla-mplayer mplayer-fonts
```

**Step 4**:
Close Firefox. Then launch Firefox again.

---

### Post by univremonster on 2007-08-02
This is something I have also wondered about from time to time; I had the Totem plugin as it comes when you do a fresh install of Ubuntu and it always said something about missing codecs, but I never put the time and effort into this problem since I don't do much that involves embedded movies.  I took your advice, ayisu, but it's still not playing movies in Firefox, although I can download them and play them using MPlayer.

---

### Post by aysiu on 2007-08-02
Can you close Firefox, install the *ubuntu-restricted-extras* package, restart Firefox, and see if that fixes the problem?

---

### Post by univremonster on 2007-08-02
> **aysiu said:**
> Can you close Firefox, install the *ubuntu-restricted-extras* package, restart Firefox, and see if that fixes the problem?

Ayisu,

I think it may be a problem of settings... I'm not sure which ones to change.  I did as you suggested and installed the ubuntu-restricted-extras followed by a restart, but when I click a video I still get an option either to download or browse for a program to open with

---

### Post by univremonster on 2007-08-02
PS - shouldn't the restricted media add-on allow me to view things like on [this page]("http://www.vdat.com/techsupport/PRNwindowstest.asp")?

---

### Post by univremonster on 2007-08-02
this [add-on]("https://addons.mozilla.org/en-US/firefox/addon/446") to Firefox has been able to play every video I've thrown at it (although it gives me an error message each time), but it's still not internal... am I just grousing at this point?

---

### Post by univremonster on 2007-08-03
*bump*... still unable to get videos to play within Firefox

---

### Post by univremonster on 2007-08-06
bump

---

### Post by univremonster on 2007-08-14
*crickets chirp*

---

### Post by wcbardwell on 2007-08-15
I Got things running. I removed totem plugin and even totem. I tried different plugins, but I just liked totem better. I reinstalled totem (gstreamer), totem plugin, the gstreamer extra plugins (good, bad, ugly), and I was off and running. Thanks for the help everyone.

---


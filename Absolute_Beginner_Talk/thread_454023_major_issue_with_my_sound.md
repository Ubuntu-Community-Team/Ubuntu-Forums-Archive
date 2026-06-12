---
title: "major issue with my sound"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-25
ok.. i have this external volume controller.. its touch sensative.. it has mute button... so what happened is that i muted my volume couple of minutes and when i tried to press it again to get back my sound.. it didnt work then i check my volume controller but it doesnt go in.. it says.. no gstremer of sound card.. no i was playing song all day long.. i know i have a sound card.. i check synaptic and gstreamer is installed.. no sure which one but there were many.. so what can be the problem ? thanks

---

### Post by HunkieChan on 2007-05-25
anyone please ?

---

### Post by HunkieChan on 2007-05-25
ok please i really need help guys.. my sound is working

---

### Post by HunkieChan on 2007-05-25
okay, why isnt anyone helping me ? i really need my sound.. can anyone help ?

---

### Post by justifier on 2007-05-25
try checking if its muted in ubuntu in Gmix. (its in the menu)
unmute everything and see if that solves the issue

---

### Post by HunkieChan on 2007-05-25
> No volume control GStreamer plugins and/or devices found.

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

it says the same thing ^.. what should id ?

---

### Post by aeiah on 2007-05-25
does a reboot solve it? what soundcard is it? (not that this should matter to be honest)

---

### Post by HunkieChan on 2007-05-25
reboot doesnt solve it.. sound card is intel hda..

---

### Post by hanzomon4 on 2007-05-25
Open up the mixer by double clicking the speaker Icon, check to make sure all of the channels are unmuted

---

### Post by aeiah on 2007-05-25
go in a terminal and type
```
asoundconf list
```

this should list your soundcard. what may have happened is that your mute button sent a signal to unload your soundcard modules. does 'asoundconf list' list your soundcard(s)?

there's a way to set it by default and load it up using asoundconf but im at work on a windows box so i cant go and check right now. if you just type
```
asoundconf
``` in the terminal it'll give you the command to use though. if it doesnt list it with 'asoundconf list' then it's a deeper issue perhaps

---


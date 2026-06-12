---
title: "question: music"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by davaca on 2006-06-20
When I insert a cd , rhythmbox says: "could not establish connection to sound server". How do I get ubuntu to play a cd, or music in general?

Something related: mp3's can't be played normally, right? What do I have to do to make them work (after the sound is fixed:p )?

---

### Post by FredB on 2006-06-20
Install gstreamer plugins with Add/Remove in Applications Menu.

Click "Show unsupported applications" and "Show proprietary applications" boxes.

And just search for gstreamer. Install them and MP3s will be played.

Hope it helps !

---

### Post by givré on 2006-06-20
did you read that [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ;)

---

### Post by FredB on 2006-06-20
Why do I forget to ask this wiki page in my answer ?

Why ???????????????

---

### Post by davaca on 2006-06-20
wel, thank you, but my problem isn't solved... I t's not just mp3, but all sound, so it's a sound card problem...
looking in the wiki, I found you had to run 'alsamixer' in the terminal, which led to this:
alsamixer: function snd_ctl_open failed for default: No such device
aplay -l gave me :
"aplay: device_list:200: no soundcards found..."
but when i did 
$ lspci -v 
it nowhere showed Multimedia audio controller, which it was supposed to do

---

### Post by givré on 2006-06-20
What is your soundcard ?
If you have two sound card, try to disable one via the bios, it is source of confict

---

### Post by davaca on 2006-06-20
I only have one sound card, but I don't know exactly what kind.

---


---
title: "How to record Firefox midi"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by paker on 2007-03-05
I got mozplugin installed and midi is playing fine now in Firefox. Is there a way to record this? Thanks.
By the way, I tried Sound Recorder. It appeared to be recording, but I don't hear any sound when the file is played back.

---

### Post by zanglang on 2007-03-06
I think you can right-click on the page with playing midi, select View Page Info -> Media, and then find the .mid file from a list there. Give it a try. ;)

---

### Post by paker on 2007-03-07
Here is the page I am playing the midi file from. I recorded it Sound Recorder. If someone can please help, I will appreciate. 

[http://library.timelesstruths.org/music/Satisfied_with_Jesus/](http://library.timelesstruths.org/music/Satisfied_with_Jesus/)

midi play button is at about 7 o'clock direction.

---

### Post by paker on 2007-03-07
By the way, I tried this:

System>Preferences>Sound>Sound Capture. ALSA was the default setting. When I clicked on TEST, it didn't make any beep. Something's not working right here?

---

### Post by zanglang on 2007-03-08
Again, have you tried using View Page Info to save the midi file?

Following your link, my Firefox goes to the page:
[http://library.timelesstruths.org/music/Satisfied_with_Jesus/midi/](http://library.timelesstruths.org/music/Satisfied_with_Jesus/midi/)
at which point if I click 'View Page Info' -> Select 'Media' -> Scroll the list down to the bottom I see the item '../../../library/music/S/Satisfied_with_Jesus/Satisfied_with_Jesus.mid' with the type 'Embed'. Click on the 'Save As' button and you'll be able to save the midi file to your computer. This works with any other types of media embeddable on web pages.

For Sound Capture to work you need something feeding audio into your computer Line-In, or have your capture source changed to the playback device (can't give steps because I'm not on my Feisty laptop at the moment, but I will if you're still interested)

---


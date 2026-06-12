---
title: "Soundconverter not converting tracks properly"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Charco on 2007-02-22
I was trying to convert mp3's to mp3's at lower bitrates, but when i convert them, their song lengths get messed up. For instance, I convert a song that is 2:51 long, it will display that it is 9:58 long. The song ends at the proper time, but the tracking is messed up. If i drag the tracking to 7:00 for instance, the song will just end. Why?! Any help much appreciated!

---

### Post by jethro10 on 2007-02-23
> **Charco said:**
> I was trying to convert mp3's to mp3's at lower bitrates, but when i convert them, their song lengths get messed up. For instance, I convert a song that is 2:51 long, it will display that it is 9:58 long. The song ends at the proper time, but the tracking is messed up. If i drag the tracking to 7:00 for instance, the song will just end. Why?! Any help much appreciated!

Well we need to know which converter program you use. I use Gnormalize and its fine.

Sounds like you have created VBR files, or Variable Bit Rate. Normally you have a fixed amount of data per second but with VBR it varies on the complexity of the given section of music. This means a length cannot be guessed correctly. It then often screws up.

J

---

### Post by Charco on 2007-02-25
Thanks so much! gnormalize converts way better than soundconverter! Problem solved!

---

### Post by diafygi on 2007-07-29
> **Charco said:**
> I was trying to convert mp3's to mp3's at lower bitrates, but when i convert them, their song lengths get messed up.
This is a registered bug for soundconverter at [http://developer.berlios.de/bugs/?func=detailbug&bug_id=8117&group_id=3213](http://developer.berlios.de/bugs/?func=detailbug&bug_id=8117&group_id=3213)
Might it have something to do with the gstreamer plugins 0.10?

I have been looking for gnormalize and can't seem to find a deb package. Can anyone post a link?

If you use the "nautilus-script-manager" and "nautilus-script-audio-convert" packages, you can convert the files in nautilus. Just go to the terminal and type "nautilus-script-manager enable ConvertAudioFile" to enable the right-click option. Make sure you have lame installed, too.

---


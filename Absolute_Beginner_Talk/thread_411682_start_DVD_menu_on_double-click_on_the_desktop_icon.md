---
title: "start DVD menu on double-click on the desktop icon"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2007-04-17
I'd like to start video DVDs with double click on the desktop icon. I have Feisty and it now the double click only opens the file manager window. I want it to open the DVD menu just like when inserting the DVD. Is that possible?

---

### Post by crispy_420 on 2007-04-17
I'm sure you can make a custom script to do the job. I can't help you there. My guess  would be to make it would be:

point script toward drive
tell your player of choice to open it (I like VLC)

Just as a test I created a desktop launcher. Simple and crude but it worked for.

Using gnome right? Right click desktop and "create launcher..."

Name your file, I called it "Play DVD". Give a description, just name it whatever works for you.

I use vlc to play DVDs so in command I put: vlc /media/dvdrecorder.

And it worked!

---

### Post by 1002285 on 2007-04-18
> **crispy_420 said:**
> I'm sure you can make a custom script to do the job. I can't help you there. My guess  would be to make it would be:

point script toward drive
tell your player of choice to open it (I like VLC)

Just as a test I created a desktop launcher. Simple and crude but it worked for.

Using gnome right? Right click desktop and "create launcher..."

Name your file, I called it "Play DVD". Give a description, just name it whatever works for you.

I use vlc to play DVDs so in command I put: vlc /media/dvdrecorder.

And it worked!

Thank you, this seems to work for me, too, except that I had to replace dvdrecorder with cdrom0 (and vlc with totem).
I

---

### Post by crispy_420 on 2007-04-18
I guess what ever player works for you and a location of you choice. Should work with DVDs ripped to hard drive as well.

---

### Post by phenest on 2007-05-02
Is there another way to do this without creating a launcher?

---

### Post by phenest on 2007-05-09
I have also had problems with audio CD's. Double clicking the icon gives an error about the path being invalid. I have just completed a fresh install of Feisty and now I can double click the audio CD icon to open Sound Juicer, like it did before it went wrong (no idea why). So there must be a way to change the default action when a device icon is double clicked.

---

### Post by phenest on 2007-08-18
I have noticed a difference between audio CDs and DVDs. CDs are not mounted whereas DVDs are. Would that make a difference? If so, how do I fix it?

---


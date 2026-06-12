---
title: "Pioneer Inno"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-05-09
Looks like Inno sotware only works with windoze. Has anyone tried downloading from Linux to the Inno?

---

### Post by intel on 2007-05-10
Pioneer Innovest ?

if you can provide the download link, or upload the s/w in question somewhere,
then, perhaps can someone take a look

---

### Post by chazmo on 2007-08-05
The Inno uses the napster software to transfer music to and from the inno. When I connect the inno to my computer (using Ubuntu 7.04) it shows up as a usb drive which I can then drag-and-drop music to.

One thing to be careful with is to make sure that you unmount the inno before disconnecting it from your computer otherwise some of your music will become corrupt. Ubuntu will tell you the the device has been unmounted but the display on the inno will tell you not to disconnect. I have ignored the message on the inno and have not encountered any problems,

You won't be able to create playlists through Ubuntu but you can use the Inno to create playlists once you have your music transfered. Make sure your mp3 tags are correct so you can search your playlists by any category. I use easytag to edit my tags and that works great.

I'm hoping that Rhythmbox will add support for these types of devices.

---

### Post by trash.eighty on 2007-08-21
> **chazmo said:**
> The Inno uses the napster software to transfer music to and from the inno. When I connect the inno to my computer (using Ubuntu 7.04) it shows up as a usb drive which I can then drag-and-drop music to.

One thing to be careful with is to make sure that you unmount the inno before disconnecting it from your computer otherwise some of your music will become corrupt. Ubuntu will tell you the the device has been unmounted but the display on the inno will tell you not to disconnect. I have ignored the message on the inno and have not encountered any problems,

You won't be able to create playlists through Ubuntu but you can use the Inno to create playlists once you have your music transfered. Make sure your mp3 tags are correct so you can search your playlists by any category. I use easytag to edit my tags and that works great.

I'm hoping that Rhythmbox will add support for these types of devices.
Rythymbox does support them.  You need to drop a text file called .is_audio_player in the root of your player telling it where to put the music.  Here's a guide on how to do it (the guide is from Banshee, but will work for Rythymbox as well, since they follow the same standard)
[http://banshee-project.org/Guide/DAPs/MassStorageDevices]("http://banshee-project.org/Guide/DAPs/MassStorageDevices")

---


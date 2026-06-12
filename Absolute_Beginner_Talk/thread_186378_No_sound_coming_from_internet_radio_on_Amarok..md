---
title: "No sound coming from internet radio on Amarok."
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Virtuous on 2006-06-01
I am having a problem with the sound on Amarok. WHen I want to listen to the radio on it. It would start the radio but nothing would be playing. Whats strange is that When I start up Kubuntu it would play the welcome tone and all its other system tones just fine. But when it comes to music it seems to not work at all. Is there a way where I could fix this? Thanks!

---

### Post by LAurel on 2006-06-02
The radio station you are trying to listen to is probably streaming music in the .mp3 format. Since this is not an open-source format, Ubuntu doesn't include the codec for it on the installation CD, because of licensing issues.

First, you should read [this wiki page](https://wiki.ubuntu.com/AddingRepositoriesHowto) on how to add extra respositories. You'll want to add the universe and multiverse repositories.

Then, read [this wiki page](https://wiki.ubuntu.com/RestrictedFormats) on how to install any non-free codecs.

---

### Post by N8K99 on 2006-07-02
I have the codecs installed that allow me to play mp3s and m4as and ogg and all of that stuff, however I am still getting an error message when ever I try to listen internet radio streams and podcasts, like the UbuntuOS podcast. However, I can listen to the last.fm radio groups, so all is not lost!

I would like to be able to use amarok to listen to radio streams. I'd also like it if my amarok even pretended to look for the wikipedia artist pages. Other than these minor little luxury issues, I love this music player.

---

### Post by Jimmeh on 2006-09-30
hello

Grab a package called libxine-extracodecs from [http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)
That enables MP3 support in Amarok.

Cheers!

---


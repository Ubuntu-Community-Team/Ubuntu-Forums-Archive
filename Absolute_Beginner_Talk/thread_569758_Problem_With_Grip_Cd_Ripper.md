---
title: "Problem With Grip Cd Ripper"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by nickmayfield on 2007-10-07
hello everyone. for some reason grip thinks there is no cd in my drive. i tried both of my drives and it says the same thing. i used the sound juicer and that worked fine but i don't want ogg files, i need mp3 for my car. how do i get it to see the cd. i'm new to the linux world
nick

---

### Post by julian67 on 2007-10-07
You can set up sound juicer to encode to mp3, there are some threads on it but briefly you need to install gstreamer plug ins and maybe liblame and lame. I had it working fine but it's a while since I used it so can't offer precise details. You can also configure grip to see whichever drive you're using but it doesn't have the friendliest interface. You just need to find the drive config and point it to the right place.

There are extremely good alternatives such as [Asunder](http://littlesvr.ca/asunder/)

> "Asunder is a graphical Audio CD ripper and encoder for Linux. You can use it to save tracks from an Audio CD as WAV, MP3, OGG, and/or FLAC." 

Its interface is a lot like soundjuicer, it starts up quicker and there's a deb available. When you install it it will add anything you need for mp3 support automatically. 

If you want an easy gui interface and and good rips Asunder is excellent.

---


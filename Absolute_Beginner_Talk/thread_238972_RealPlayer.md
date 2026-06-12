---
title: "RealPlayer"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by alainsamoun on 2006-08-18
I downloaded RealPlayer and installed it in the computer.
Now, how do you embed the player in FF so it can open the audio/video files automatically?

---

### Post by Perfect Storm on 2006-08-18
You might want to use mplayer for that. Much better.
If you havn't set up your sourcelist, you can do it here: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

When sample your sourcelist change it with your previous one:
```
sudo nano /etc/apt/sources.list
```

save and exit.
```
sudo apt-get update
sudo apt-get install w32codecs mplayer-386 mozilla-mplayer
```

When done open FF and type in the browserbox **about : plugins** (without spaces in between) to check if it's installed correctly.

---

### Post by geokok1981 on 2006-08-18
Maybe u can find help here:
[http://www.ubuntuforums.org/showthread.php?t=235552]("http://www.ubuntuforums.org/showthread.php?t=235552")

---

### Post by true_friend on 2006-08-18
Artificial Intelligence: ur desktop is great. can u tell what theme u are using???
fine 3d look and my favourite light colour bombastic. so i m in love with this theme. plz tell me its name or source.
Regards
True_Friend

---

### Post by Perfect Storm on 2006-08-18
Which one? in my sig?
Try read some of the comments there's made on some of them, this isn't the right place to discuss themes ;)
[http://ubuntuforums.org/gallery/showgallery.php?cat=500&ppuser=19](http://ubuntuforums.org/gallery/showgallery.php?cat=500&ppuser=19)

---

